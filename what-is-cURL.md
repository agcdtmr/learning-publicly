# What is cURL?

Client URL Request Library is a command-line tool and a software library for transferring data using various network protocols.

Primary use: Sending and receiving data over the internet. It is most commonly used to make requests to web servers or APIs (Application Programming Interfaces).

Protocol Support: Supports many protocols, including HTTP, HTTPS, FTP, SMTP, and more.

## Where the "Client" Comes From
In network computing, communication usually follows a client-server model:

Client: This is the program or device that requests a service or data. It initiates the communication. Examples include your web browser (Chrome, Firefox), a mobile app, or, in your case, the cURL command.

Server: This is the program or device that provides the service or data in response to the request. In AWS, the API Gateway endpoint is the server (or rather, the gateway to the server that processes the request).

## Why It's Called "Client"
cURL is called a "client" because when you execute the command, it immediately takes on the role of the requester:

Initiates Contact: When you type curl --location --request POST 'https://...', your local terminal (running the cURL program) initiates contact with the server.

Sends the Request: It explicitly tells the server what it wants to do. For example: a POST request with what data to use (--data-raw).

Receives the Response: It waits for the server to acknowledge the request and returns the result (a confirmation code or error message) to your terminal screen.

Since the program's entire purpose is to act as a tool that initiates and manages requests to URLs (servers), the name Client for URLs perfectly describes its function in the network model.


## But WHY IS IT CALLED CLIENT 
Think of two parties talking on the internet:

The Server: This is the machine waiting to serve or provide information (like the AWS API Gateway, which for example can serve to trigger the account creation lambda function).

The Client: This is the machine or program that asks for something or requests a service (like your laptop, or your web browser).

The cURL program is called the Client because it is the party that starts the conversation and requests the server to perform the action you want it to do.

It's the asker, not the giver. It acts on your behalf to be the "Client" making a "Request."


## Is the computer or server not smart enough to know that we are the "Client" making a "Request." without using curl?
The computer or server is smart enough to know that a "Client" is making a "Request." However, they need that request to arrive in a very specific, understandable, and standardized way.

Here is why you need a tool like cURL:

1. The Computer Needs a Messenger
Your operating system (Windows, macOS, Linux) is powerful, but it's not a ready-to-use messenger like cURL. It doesn't automatically know:

Which Protocol to Use: Should it use HTTP, FTP, or something else?

How to Format the Headers: Where do you put the X-API-Key?

How to Format the Body: How do you correctly package the Intake data as JSON?

cURL is the messenger program. It takes all your raw input (the URL, the headers, the data) and wraps it up into a perfectly formatted, standard, and complete network request that the server can instantly understand and process.

2. The Server Needs Standardization
For example, the AWS API Gateway isn't just looking for data; it's looking for a well-formed HTTP Request.

The cURL tool ensures:

It uses the correct POST method.

The required Content-Type: application/json header is present.

The essential authentication API-Key is correctly placed in a header.

If you tried to just paste your data into a text file and send it without cURL, the server wouldn't recognize it as a valid, trustworthy request and would simply reject it.

In summary: The server knows that a client is asking for something, but it needs a specialized program like cURL to correctly structure that question so it meets all the strict rules of the network protocol and the API design.


## Let's try it!

##### Simple Data Retrieval

The most common way to use cURL is for simple data retrieval. You only need the URL:

`curl http://wttr.in/amsterdam`

This command acts as a Client asking the wttr.in Server for the weather data for Amsterdam. The server responds directly in your terminal.


Let's try getting the public IP address of your machine.
`curl ifconfig.me`
