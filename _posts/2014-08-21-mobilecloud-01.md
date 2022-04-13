---
layout: post
title: Notes For Mobile Cloud
categories: [Tech]
tags: Android
---
Week1
---
1. Introduction to the mobile cloud

2. What are communication Protocols
	how to commucate:
	syntax (format of messages)
	semantics (meaning of message)
	timing (how long wait/process next)
	
3. Intro to HTTP

4. Why HTTP

5. What is a Cloud Service

6. HTTP Request Methods

7. HTTP Request Anatomy

8. URLs & Query Parameters

URL format: http://host:por/pat&parameter1=2
URL Encoding: If you pass special charaters in the url, it will automaticlly encoding.
9. Mime Types & Content Type Headers

Both client and server can send Body
Images have different format, like jpg, png
pure text or html format
how to interpret these formats
MIME Types: (Describing the http body)
image/jpg
image/png
text/plain
text/html
either in a request or response, client and server will decide how to interpret these data
meta information
Content-type(header)
describe the mime type
10. Request Body Encoding

How to send data to server
mime type in body:
url encoded form data (simple key value)
multipart (uploading data)
applicaiton/json
11. HTTP Response Anatomy

Satus line
	1. response code (what happened on server)
	2. headers:
		content-type(MIME)
	3. body:
		actual data
		
12. HTTP Response Codes

	100-500
	1XX: info
	2XX: success
		200: OK
	3XX: redirection
	4XX: client error
		404: not found
	5XX: server error
		500: server error
		
13. Cookies
	logged in
	same client 
	small piece file server send to client to save 
	client add these to request header
	
