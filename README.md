# Introduction to Web Protocols (HTTP and HTTPS)

## Learning goals

- Understand what protocols are and their importance
- Identify the most commonly used protocols in the web
- Learn what an HTTP request is and how it is composed
- Become acquainted with TCP and UDP

## Introduction

As we briefly touched upon in the previous chapter, the internet is essentially a collection of computers that interact with each other. We last looked over some of the ways computers identify one another-- but what about once they resolve their destination, how do they *actually* interact? In this lesson, we will be looking at some of the most common ways users as well as other devices and software interact with the web and how these methods really work under the hood.

## Protocols

At the heart of the internet (and by extension, the web), are *protocols*. A **protocol** is simply a standardized way of communication that ensures both the device on the receiving end and the device on the sending end are on the same page. Without protocols, devices would be unable to communicate with each other, and the exchange of information would be chaotic, to say the least.

Given the many different types of information and data that want to be exchanged, it makes sense that different protocols would emerge for their own purposes. For example, if you want to transfer a file, that will most likely be using a different protocol than if you wanted to retrieve text from a website.

Let's take a look at some of the most commonly used protocols on the web!

## HTTP and HTTPs

*HTTP* (HyperText Transfer Protocol) and *HTTPS* (HyperText Transfer Protocol Secure) are both protocols you most likely use multiple times on a daily basis. Both of these protocols are used for exchanging data over the internet.

*HTTP* is the standard protocol used for transmitting data between a web server and a client (e.g. web browser). *HTTPS* is mostly the same thing, with an added layer of encryption to prevent it from being tampered with or intercepted by others on the same network. You can view which protocol you're using every time you go to a website simply by looking at the address bar at the top:

![Browser address bar](https://curriculum-content.s3.amazonaws.com/6685/devops-m1-web-networking-protocols/browser.jpg)

Under the hood, when you try accessing a website like `google.com`, it actually builds a request and sends it to the server IP address the DNS resolves to. 

An HTTP request consists of several parts:

- **Method:** Specifies the type of action that the request wants to perform. The most common methods (which we will take an in-depth look eventually) are: `GET` (used for retrieving data), `POST` and `PUT` (used for submitting data) and `DELETE` (used for deleting data).
- **URL (Universal Record Locator):** Specifies the location that is to be accessed. It also includes the protocol, for example: `https://google.com`.
- **Headers:** These contain additional information about the request, like the type of web browser being used and custom information.
- **Body:** The meat of the request; contains any data that needs to be sent with the request, for example the website content.

When the server receives the request, it replies with a response message, including most of the same components as the request itself, with the addition of a status code. A status code simply indicates whether the request was successful or not. Some common status codes include `404 (Not Found)`, `200 (OK)`, and `500 (Internal Server Error)`.

Here's an example of what an HTTP request would look like:

```bash
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:87.0) Gecko/20100101 Firefox/87.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Upgrade-Insecure-Requests: 1
```

Most of these are headers and provide additional information, like what type of format the browser prefers. Don't worry about not understanding what most of these mean, the main idea right now is to begin *recognizing* how these requests appear.

Here's an example of what an HTTP request's *response* would look like:

```bash
HTTP/1.1 200 OK
Date: Thu, 10 Mar 2023 15:00:00 GMT
Server: Apache/2.4.51 (Unix)
Last-Modified: Tue, 08 Mar 2023 12:00:00 GMT
ETag: "123456789abcdef"
Content-Length: 512
Content-Type: text/html

<!DOCTYPE html>
<html>
<head>
    <title>Welcome to Example.com</title>
</head>
<body>
    <h1>Welcome to Example.com!</h1>
    <p>This is the home page of our website.</p>
</body>
</html>
```

At the top you can see the status code `200`, meaning it succeeded. The `body` is that entire chunk in the bottom half, which includes the *HTML* source code for the website. Your browser would then parse that HTML code and render it into an actual site that you can interact with!

## TCP and UDP

Besides HTTP, the two most important communication protocols are *TCP (Transmission Control Protocol)* and *UDP (User Datagram Protocol)*. Both of these protocols are used to transfer data between two connections, with some important differences between them.
The *main* difference between TCP and UDP is that TCP is *reliable* and *ordered*, whereas UDP is *unreliable* and doesn't care about the order in which data was sent. As a result, what ends up happening is TCP is slower, so UDP gets used for the sorts of data that are sent continuously where only the latest state matters, such as video streaming and online games. TCP is typically used for more sensitive data like web browsing, emails, file transfers, etc.  

![TCP vs UDP](https://curriculum-content.s3.amazonaws.com/6685/devops-m1-web-networking-protocols/udp-and-tcp-comparison.jpg)

## Conclusion

This lesson is meant to start getting you used to the terminology and reasoning behind a lot of the underlying web protocols. In the upcoming lessons and labs we will begin actually interacting with these, but for now don't worry too much if it hasn't clicked yet!