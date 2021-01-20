# Verifying Client

These clients verify the cryptographic proofs accompanying responses from the server.
A verifying client is a client built on top of [JSON-RPC verifying API](https://github.com/diem/diem/blob/master/json-rpc/json-rpc-spec.md#experimental-apis), which is still in experimental.
The verifying client should provide similar or same API with non-verifying client, so that application can switch from non-verifying client to verifying client much easier.

Current plan is working out one verifying client in Rust language.
