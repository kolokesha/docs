# Handling errors

If an operation completes successfully, the server returns the OK status to the client. If an error occurs during the operation, the server returns a message with the error description.

Errors in APIs are described using the [google.rpc.Status](https://github.com/googleapis/googleapis/blob/master/google/rpc/status.proto) message. This error model is used in both gRPC and REST interfaces.

The [the table below](#error-list) lists the errors that are supported in the API.
The .proto specification is available in the [repository on GitHub](https://github.com/googleapis/googleapis/blob/master/google/rpc/code.proto).

## Error message format {#error-message-format}

The `Status` message contains three fields:

| Field | Description |
| ----------- | ----------- |
| `code` | <b>int32</b></br>gRPC error code. Possible error codes are defined in [google.rpc.Code](https://github.com/googleapis/googleapis/blob/master/google/rpc/code.proto). |
| `message` | <b>string</b></br>Error description. |
| `details` | <b>repeated google.protobuf.Any</b></br>Error details. This field contains detailed information about the error, such as which parameters were specified incorrectly.</br> </br>Message types used in this field are defined in [google.rpc.ErrorDetails](https://github.com/googleapis/googleapis/blob/master/google/rpc/error_details.proto). |

Below is a gRPC description of the `Status` message:

```protobuf
message Status {
  // gRPC error code. Possible values are defined
  // in [google.rpc.Code].
  int32 code = 1;

  // Error description.
  string message = 2;

  // Error details.
  repeated google.protobuf.Any details = 3;
}
```

## HTTP mapping {#http-mapping}

To see how gRPC statuses correspond to HTTP codes, see [google.rpc.Code](https://github.com/googleapis/googleapis/blob/master/google/rpc/code.proto).

The example below shows an error that can be returned by the server in response to a REST request:

```json
{
  "code": 16,
  "message": "Token is invalid or has expired.",
  "details": [
    {
      "@type": "type.googleapis.com/google.rpc.RequestInfo",
      "requestId": "e38e71c3-adc6-4584-98a4-b0f103d55f61"
    }
  ]
}
```

## List of possible errors {#error-list}

| gRPC code | gRPC status | HTTP code | Error description |
| ----- | ----- | ----- | ----- |
| 1 | CANCELLED | 499 | The operation was aborted on the client side. |
| 2 | UNKNOWN | 500 | Unknown error. |
| 3 | INVALID_ARGUMENT | 400 | Incorrect request parameters specified. Details are provided in the `details` field. |
| 4 | DEADLINE_EXCEEDED | 504 | Exceeded the server response timeout. |
| 5 | NOT_FOUND | 404 | The requested resource not found. |
| 6 | ALREADY_EXISTS | 409 | Attempt to create a resource that already exists. |
| 7 | PERMISSION_DENIED | 403 | The user has no permissions required to perform the operation. |
| 8 | RESOURCE_EXHAUSTED | 429 | The request limit exceeded. |
| 9 | FAILED_PRECONDITION | 400 | The operation was canceled because the conditions required for the operation were not met. Examples: attempting to delete a non-empty folder or calling the rmdir command for an object that is not a folder. |
| 10 | ABORTED | 409 | The operation failed due to a concurrent computing conflict, such as an invalid sequence of commands or an aborted transaction. |
| 11 | OUT_OF_RANGE | 400 | Out of range. For example, searching or reading outside of the file. |
| 12 | NOT_IMPLEMENTED | 501 | The operation is not supported by the service. |
| 13 | INTERNAL | 500 | Internal server error. This error means that the operation cannot be performed due to a server-side technical problem. For example, due to insufficient computing resources. |
| 14 | UNAVAILABLE | 503 | The service is currently unavailable. Try again in a few seconds. |
| 15 | DATA_LOSS | 500 | Permanent data loss or damage. |
| 16 | UNAUTHENTICATED | 401 | The operation requires authentication. |
