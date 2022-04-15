---
layout: post
title: RESTful Spring
categories: Tech
tags: [Spring, RESTful]
---

As you see in steps below, Spring uses the Jackson JSON library to automatically marshal instances of type Greeting into JSON.
 
When you're working with Spring, assume someone else has come up against the same issue. You can dump all the server-side JSON generation, because all you need to do is:

1. Include the Jackson JSON JARs in your app
2. Set the RequestMapping return type to @ResponseBody(yourObjectType)
Spring will auto-magically convert your object to JSON. Really. Works like magic.

Doc for [@ResponseBody](http://static.springsource.org/spring/docs/3.0.x/spring-framework-reference/html/mvc.html#mvc-ann-responsebody)

```
An HttpMessageConverter implementation that can read and write JSON using Jackson's ObjectMapper. JSON mapping can be customized as needed through the use of Jackson's provided annotations. When further control is needed, a custom ObjectMapper can be injected through the ObjectMapper property for cases where custom JSON serializers/deserializers need to be provided for specific types. By default this converter supports (application/json).
```

If you want to use xml as the respon body, you can use request mapping properties:

```
//start from 3.1.0
@RequestMapping(
    value = "/{id}.json",
    method = RequestMethod.GET,
    produces = "application/json")
@ResponseBody
public Person getDetailsAsJson(@PathVariable Long id) {
    return personRepo.findOne(id);
}

@RequestMapping(
    value = "/{id}.xml",
    method = RequestMethod.GET,
    produces = "application/xml")
@ResponseBody
public Person getDetailsAsXml(@PathVariable Long id) {
    return personRepo.findOne(id);
}
```

or java bean annotation

```
//@XmlRootElement(name = "user")
public class User {
	private long id;
	private String name;
	private Date registrationDate;
```
