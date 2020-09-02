# [protobuffed](https://github.com/fenollp/protobuffed)

[Google's Protocal Buffers](https://developers.google.com/protocol-buffers/docs/proto3) all buffed-up.

* Protocol Buffers v3 compatible
* type aliases
* lockfile
* always formatted
* embeddable messages
* Mark fields as deprecated (not messages)
* Golang syntax

```go
package my_package






type SomeRequest struct {
	ANestedMessage

	count int32 `id:"4"`
	previously_modified_at int64 `"id:"5",deprecated:"true"`
}
```

```go
pkg my_package

svc MyService {
    rpc SomeCall(SomeRequest): (SomeResponse)
    rpc AnotherCall(SomeRequest): (stream SomeResponse)
}

msg SomeRequest {
    ANestedMessage

  4     int32           count
  5     int64           previously_modified_at (DEPRECATED)

    enum Ordering {
            indefinite
         1  by_publication_date
        // ...
        37  by_rank
        // ...
     31284  by_view_count
    }

 17     []Ordering      sort_by
 18     map[uint64]Item sort_by
}

msg ANestedMessage (ids:<4) {
 1      bool   only_recent
    // Comments can be
    // above field or message...
 2      string matching_curation // ...as well as inline with field or message
}

msg SomeResponse {
 1      string matching_curation
}
```
