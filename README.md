Notes on Backend by *Muhammad Bin Zafar*

## Preface
In software engineering, backend refers to the **separation of concerns of the data access layer** from the presentation layer i.e. frontend that **allows a software to operate**.

A software backend is concerned with data storage and business domain code. This way the backend application can hide away proprietary business logic and be deployed with fixes and features indepedent of the frontend. This is essential.

With these two as foundation, a plethora of backend-specific concepts emerge.
- API
- Authorization and authentication
- Scalability and high availability
- Database concepts e.g. storage, design, migration, performance, security
- Backend architecture and frameworks

## API
An application programming interface or API is a way for two programs (in this case, frontend and backend) to communicate with each other.

APIs communicate across the web through protocols. 

### HTTP
Hypertext Transfer Protocol or HTTP is the de facto standard to communication over the web, especially between a frontend and backend. 

Other protocols exist to address specific needs, but are never seen between a frontend and backend. Such as:
- FTP or File Transfer Protocol to transfer files between servers and clients.
- WebDAV or Web Distributed Authoring and Versioning, an extension of HTTP, to collaboratively edit and manage files.
- WebSocket, an extension of HTTP, to enable full-duplex communication between a server and a client.