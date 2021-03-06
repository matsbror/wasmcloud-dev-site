---
title: "waPC FFI Functions"
date: 2018-12-29T11:02:05+06:00
weight: 6
draft: false
---
For the curious, here is the exact list of the waPC protocol’s functions. The guest always imports from a module called “wapc”, and all function names are preceded by two underscores to avoid accidental collisions with other exported functions.

| Function | Owner | Description |
| :-- | :--: | :-- |
| `__console_log` | Host | Guest calls host to log to host’s stdout (if permitted) |
| `__host_call` | Host | Guest calls to request the host perform an operation |
| `__host_response` | Host | Tells the host the pointer address at which to store its response |
| `__host_response_len` | Host | Returns the length of the host’s response |
| `__host_error` | Host | Tells the host the pointer address at which to store its error blob |
| `__host_error_len` | Host | Returns the length of the host error blob |
| `__guest_response` | Host | Called by the guest to set the pointer and length of the guest’s response blob |
| `__guest_error` | Host | Called by the guest to set the pointer and length of the guest’s error blob |
| `__guest_request` | Host | Called by the guest to tell the host the pointer addresses of where to store the request’s operation (string) and request payload (blob) values. |
| `__guest_call` | Guest | Invoked by the host to tell the guest to begin processing a function call. The guest will then retrieve the parameters and set response values via host calls. |

The waPC FFI functions are already taken care of for you in the existing guest and host libraries that you can find in the [waPC](https://github.com/wapc) organization. Built on top of those libraries, using waPC code generation from `widl` schemas, we have the wasmcloud [actor-interfaces](https://github.com/wasmcloud/actor-interfaces).

If you are interested in building your own language binding for waPC (and subsequently wasmcloud), check out the next section.
