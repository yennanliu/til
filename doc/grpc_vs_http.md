
# gRPC Request Types (gpt)

gRPC does not use the traditional HTTP methods like `GET`, `POST`, `PUT`, `DELETE`, etc., because it operates over HTTP/2 with its own mechanism for request/response handling. However, gRPC service methods can be conceptually compared to HTTP methods:

## Unary RPC (similar to HTTP POST)
- The client sends a single request to the server and receives a single response.
- Example:
  ```proto
  rpc RentCar (RentCarRequest) returns (RentCarResponse);
  ```

## Server Streaming RPC (similar to HTTP GET with streaming)
- The client sends a single request to the server and receives a stream of responses.
- Example:
  ```proto
  rpc ListAvailableCars (Empty) returns (stream Car);
  ```

## Client Streaming RPC (similar to HTTP POST with streaming)
- The client sends a stream of requests to the server and receives a single response.
- Example:
  ```proto
  rpc UploadRentalRecords (stream RentalRecord) returns (UploadStatus);
  ```

## Bidirectional Streaming RPC (similar to WebSocket communication)
- Both the client and server send a stream of messages to each other.
- Example:
  ```proto
  rpc Chat (stream ChatMessage) returns (stream ChatMessage);
  ```

## Mapping gRPC to HTTP Methods

- **Unary RPCs** can be compared to `POST` requests in HTTP, where a client sends a request and receives a response.
- **Server Streaming RPCs** can be compared to a `GET` request with a streaming response, though gRPC streaming can continuously push updates, which is not typically how REST `GET` requests work.
- **Client Streaming RPCs** might resemble a series of `POST` requests being sent to a server before getting a single response.
- **Bidirectional Streaming RPCs** are more like a continuous conversation (like a WebSocket), where both the client and server can send and receive messages at any time.

gRPC provides a more flexible communication pattern between clients and servers than traditional HTTP methods.
