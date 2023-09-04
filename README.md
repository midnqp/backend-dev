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

On the other hand, projects such as WebRTC are not a standalone protocol, rather a set of technologies and standards to enable real-time communication (usually voice and video) between clients.

Various architectural styles are maintained to communicate in a structured approach such as REST, SOAP, gRPC, and GraphQL.

### REST API Design
REST or Representational State Transfer is a standard in API design. 

#### Guiding principles
It stands on 6 guiding principles, important among them are:
- Client-server: separate backend and frontend.
- Stateless: each http request contains enough data (e.g. auth, session, user data) to be understood without knowing what the previous request was.
- Cacheable
	- GET: always
	- POST: using http headers expire, cache-control, etag, last-modified
	- PUT, DELETE: never

#### Hierarchy
REST APIs are modeled as a resource hierarchy. The primary data representation is called a "resource".
- `users` is a **collection** (collection resouce, plural naming).
	- Such as `/users`
- `user` is a **document** (singleton resource, singular naming)
	- Such as `/users/:userId`
- A **controller** (named as a verb) is an executable function, with parameters and return values
	- Such as `/users/:userId/cart/pay`
- **Sub-collection resources** are nested. 
	- For example, in `/users/:userId/projects`, "projects" is a sub-collection resource
	- Similarly, a singleton in that sub-collection will be `/users/:userId/projects/:projectId`


#### Design
Constraints in REST API naming ensures a design of scalable API endpoints:

- Use plural nouns, such as `users`, `orders`, `categories`.
- Use hyphen, not underscores. Use lowercase, never camel-case. Correct one is `GET /food-categories`, not `GET /foodCategories`.
- Never use CRUD function names, such as `GET /users/list` or `POST /users/create`.

Examples of commonly used APIs:
- `GET /users` to get a list of users.
- `GET /users/:id` to get a single user.
- `POST /users/:id` to create a single user.
- `PUT /users/:id` to update a single user.
- `DELETE /users/:id` to delete a single user.

For sub-resources:
- `GET /users/:id/projects` to get projects of given user
- `DELETE /users/:id/projects/:id` to remove a project of given user

Adding some features:
- `GET /users` `?country=arabia` `&status=verified` to search users by country and status
- `GET /users` `?_fields=name,country` to list users, but return only 2 data attributes: name and country
- `GET /users` `?_sort=name` `&_order=asc` to list users and sort by name in ascending order
- `GET /users` `?_page=1` `&_limit=10` to list users and paginate