---
layout: post
title: The Maven Issues I met in work
categories: Tech
tags: Maven
---
Today my work is to merge the unit tests and integration tests to a new component.

What should I do are:

1. Add maven dependencies and plugins to make them run.
    For UT, just add the testng dependency
    For IT, add plugin for additional integration source and resource

                   <!-- Adds IT source directory to our build -->
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>build-helper-maven-plugin</artifactId>
                        <version>1.9.1</version>
                        <executions>
                            <!-- Add a new source directory to our build -->
                            <execution>
                                <id>add-integration-test-sources</id>
                                <phase>process-resources</phase>
                                <goals>
                                    <goal>add-test-source</goal>
                                </goals>
                                <configuration>
                                    <!-- Configures the source directory of our integration tests -->
                                    <sources>
                                        <source>src/it/java</source>
                                        <!--<outputDirectory>${project.build.directory}/test-classes</outputDirectory>-->
                                    </sources>

                                </configuration>
                            </execution>
                            <execution>
                                <id>add-resource</id>
                                <phase>generate-resources</phase>
                                    <goals>
                                        <goal>add-resource</goal>
                                    </goals>
                                <configuration>
                                    <resources>
                                        <resource>
                                            <directory>src/it/resources</directory>
                                        </resource>
                                    </resources>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>

                     <!-- Runs unit tests -->
                     <plugin>
                         <groupId>org.apache.maven.plugins</groupId>
                         <artifactId>maven-surefire-plugin</artifactId>
                         <configuration>
                             <!-- Tests write logs and hence need these parameters -->
                             <excludes>
                                 <exclude>**/*ITCase.java</exclude>
                                 <exclude>**/IT*.java</exclude>
                             </excludes>
                         </configuration>
                     </plugin>

                     <!-- Runs integration tests -->
                     <plugin>
                         <groupId>org.apache.maven.plugins</groupId>
                         <artifactId>maven-failsafe-plugin</artifactId>

                         <executions>
                             <execution>
                                 <id>integration-tests</id>
                                 <goals>
                                     <goal>integration-test</goal>
                                     <goal>verify</goal>
                                 </goals>
                             </execution>
                         </executions>
                     </plugin>


There is one issue happend, after I added these plugins the integration test classes which under src/it/java
is not complied and I can not find out.

Finally I found the reason, which is so silly, it was because my plugin was added under the <pluginManager> tag,
instead of the <plugins> tag, so it is not executed.

The <pluginManager> tag was used to share the same plugin configuration across all your project modules,
it is not executed automatically.



