# SAuth

SAuth(Service Authentication) is a protocol for B2B solution services to authenticate each client's end-user.

## 1. Introduction

There are many B2B services communicating directly to their customer's end users. In most cases, they need to authenticate and identify each end-users to ensure secure usage of service. However, there isn't a standard protocol to do so.

Most services found their own way to do so and fortunately, we found they're similar to one another.

This SAuth protocol is nothing but an organized set of them. With this, we hope all the terminologies and communication sequences can be clarified and standardized.

## 2. Roles

- Service Server : The server providing a B2B service(which needs an end-user authentication - e.g., chat or sticker API) to the Client Server and End User.
- Client Server : The server providing a B2C service to the End User. (The term "client" does not imply any particular implementation characteristics - e.g., whether the application executes on a server, a desktop, or other devices).
- End User : Users of the Client Server.

## 3. Verifying the Client Server to the Service Server

The Service Server needs to verify requests from Client Server. So the Client Server should send a requist to the Service Server with `Secret Token` every time, issued by the Service Server.

## 4. Authentication

    +--------+                +--------+                        +---------+
    |        |                |        |                        |         |
    |        |                |        |--(A)- Authentication ->|         |
    |        |                |        |           Grant        |         |
    |        |                | Client |                        |         |
    |        |                | Server |<-(B)-- Access Token ---|         |
    |  End   |<-(C)- Access --|        |                        | Service |
    |  User  |       Token    |        |                        | Server  |
    |        |                +--------+                        |         |
    |        |                                                  |         |
    |        |--(D)------- Request with Access Token ---------->|         |
    |        |                                                  |         |
    +--------+                                                  +---------+

### 4-A. Authentication Grant

First, the Client Server should request an access token to the Service Server.

### 4-B,C. Access Token(Service Server -> Client Server)

The Service Server will issue an access token. And the Client Server will give it to the user.

### 4-D. Request

Now, the end user got a token granted to himself. He/She can now access to the Service Server's resource with it.

## 5. Open Source

### 5-A. License

SAuth protocol is under the MIT License.

### 5-B. Community

If you have any problems or questions, please make an issue on Github.
