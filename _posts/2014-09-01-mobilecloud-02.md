---
layout: post
title: Programming Cloud Services for Android Handheld Systems Week 2
categories: [Tech, Learning]
tags: [Android]
---

1. Building Cloud Services on HTTP
 use http request(query parameter) to send command to 
	1. PUT - store new video
	2. GET - query/fetch video
	http response(response code - status, body - data(vido, just text), content type)
 put video(name, content type in header) in mutil-part body
 
2. Protocol Layering & HTTP Design Methodologies
  web services on top of http
  rest api 
  
3. REST
  get video/1/deration
 
4.  HTTP Polling
 start with client
  client decide 
  web socket
 
5. Push Messaging 
  GCM service
  
6. Java Servlet
	web.xml to routing request
	
7. HttpServlet

8. Request Routing and Web.xml

9. Video Servlet Walkthrough
	lots of Servlet
	doGet(){
		resp.setHeader();
		resp.setContextType("text/plain");
	}
	doPost(){
		//get values from the client
		String name = req.getParameter("name");
		//validate duration
		//set content type
		//validate parameters
		//tell client bad request
		//tell client successful processed
	}
	
	loop each video 
	video are stored in the java object
	anyone can pertend to be your client and send you data, you need to check the data
	
10. Securely Handling Client Data & Avoid Injectiong Attacks

	client send some data, because of that data can be a command, we execute that command.

	Don't trust client data.












 