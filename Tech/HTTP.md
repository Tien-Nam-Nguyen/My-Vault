---
type:
  - Tech
tags:
  - http
  - network
  - api
published: true
created: 2023-11-01 11:17
modified: 2023-11-01T16:30:00
folder: Tech
---
# What is HTTP?

- Stand for **H**yper **T**ext **T**ransfer **P**rotocol 
- Communication between web servers & clients
- HTTP is a layer 7 (application) protocol in OSI model
- Every request is completely independent

# What is HTTPS?

- Stand for **H**yper **T**ext **T**ransfer **P**rotocol **S**ecure
- Data sent is encrypted by SSL or TLS
- Install certificate on web host.

# HTTP methods

|  Method |                                                   Purpose                                                  |
|:-------:|:----------------------------------------------------------------------------------------------------------:|
| GET     | Get one or many data record from server                                                                    |
| POST    | Send request to create new record on server                                                                |
| PUT     | Update a entire record or create one if not exists                                                         |
| PATCH   | Update a field of a record                                                                                 |
| DELETE  | Delete a record                                                                                            |
| HEAD    | Like GET request but doesn't have response body                                                            |
| OPTIONS | Get information about allowed methods in this URL                                                          |
| CONNECT | Create a two way connection between client and server                                                      |
| TRACE   | Debug web server connections by returning the full HTTP request to the client for proxy-debugging purposes |

# HTTP status codes

**1xx: Informational**
Request received / processing

**2xx: Success**
Successfully received, understood and accepted

**3xx: Redirect**
Further action must be taken / redirect

**4xx: Client error**
Request does not have what it needs

**5xx: Server error**
Server failed to fulfil an apparent valid request.


|            Code            |                                     Purpose                                    |
|:--------------------------:|:------------------------------------------------------------------------------:|
|           200 OK           | GET, PUT, PATCH, DELETE successfully                                           |
|         201 Created        | Create record successfully                                                     |
|       204 No Content       | Request successfully but there's no content in payload                         |
| 301 Moved Permanently      | Requested resource has been permanently moved to a new URL                     |
|      304 Not Modified      | The requested resource has not been modified since the last time it was loaded |
|       400 Bad Request      | Bad request                                                                    |
|      401 Unauthorized      | Missing authorization information                                              |
|        403 Forbidden       | Do not have right to access resources                                          |
|        404 Not Found       | The requested resources are not found                                          |
|   405 Method Not Allowed   | Method is rejected by server because it is not allowed                         |
|          410 Gone          | Requested is not available at requested address                                |
| 415 Unsupported Media Type | Media type is not supported by server                                          |
|  422 Unprocessable Entity  | Actions are not taken because false data                                       |
|    429 Too Many Requests   | Clietns send too many requests to server in a short time                       |
|  500 Internal Server Error | Server cannot fulfil request                                                   |
|     501 Not Implemented    | Server don't support actions to fulfil request                                 |
|   503 Service Unavailable  | Service is unavailable                                                         |

