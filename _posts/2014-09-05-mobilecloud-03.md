---
layout: post
title: Programming Cloud Services for Android Handheld Systems Week 3
categories: [Tech]
tags: Android
---
1. Java Annotation
@indentifier
by compiler
2. HTTP to Object Marshalling

3. Intro to JSON

4. The Spring Dispatcher Servlet and Controller Abstraction 
using spring framework to dispatcher servlet: extract parameter from request, validation,construct object with params
5. Spring Controllers
tell the dispatcher servlet 
@Controller
 public class ContactsCtrl{
	@RequestMapping("/contacts")
	public Contacts getContacts(){
		//retrieve contacts
		
		return C;
	}
	@RequestMapping("/friends")
	public Contacts friends(){
	}
 } 
 
need to connect to the request
use @annotation 

6. Accepting Client Data with RequestParam Annotations
@Controller
public class ContactsCtrl{
	@RequestMapping("/path")
	public Contacts search(
	//http request paramters with key search
		@RequestParam("search") String searchString,
		//convert flag to int
		@RequestParam("flag") int searchFlag){
		
	}

}

7. Accepting ClientData with PathVarialbe Annotations
rest architecture
// /search/ab
//look into the path, things after the /search/ is a variable named string
@RequestMapping("/search/{string}")
public Contacts search(
	@PathVar("string") String searchStr,
	@RequestParam("flag") int flag){
	return;
}

8. Accepting Client Data with Request Body Annotaions & JSON

public class Search{
	private String first;
	private String last;
}
@RequestMapping("search")
public Contacts search(
	//take all the params to convert to a seach body, HTTP message convert
	@RequestBody Search s){

}

9. Handling Multipart Data
public Class VideoSvc{
	public boolean uploadVideo(
		@RequestParam("data") MultipartFile videoData){
		
		InputStream in = VideoData.getInputStream();
		//save to desk
		//save to database
		
	}
}
//add a new bean to accept multipart data
public Class Application{
	@Bean
	public MultipartConfigElement getMultipartConfig(){
		MultipartConfigFactory f = ...
		f.setMaxFileSize(2000);
		f.setMaxRequestSize();
		return f.createMultipartConfig();
	}
}

10. Generating Responses with the ResponseBody Annotation
//return the response body to json
public @ResponseBody contact search(){
	//find contact
	
	return contact;
	
}

11. Custom Marshlling with Jackson Annotations 

public Video createVideo(video){
	//from json 
	//Jackson ObjectMaper
	//to json
}
@JsonIgnore

12. Spring Boot & Application structure


13. Spring Controller Code Walkthrough
