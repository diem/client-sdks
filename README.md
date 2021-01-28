# Diem Client SDKs

Diem Client SDKs is a collection of libraries and tools for creating applications integrated with Diem Payment Network.

This codebase keeps track of [specifications](specs) and [status](status.md) for standard Diem Client SDK features.

Open sourced client SDKs: [Python][l1] [Java][l2] [Go-lang][l3]

| Module                             | [Python][l1]                                    | [Java][l2]      | [Go-lang][l3]   | Rust                  | TypeScript      | C#          | C++                                 |
|------------------------------------|-------------------------------------------------|-----------------|-----------------|-----------------------|-----------------|-------------|-------------------------------------|
| [BCS Runtime][1]                   | :sunny:                                         | :sunny:         | :sunny:         | :sunny:               | :partly\_sunny: | :sunny:     | :sunny:                             |
| [Transaction Builder Generator][2] | :sunny:                                         | :sunny:         | :sunny:         | :sunny:               | :snowflake:     | :snowflake: | :partly\_sunny:                     |
| [JSON-RPC Client][3]               | :partly\_sunny:                                 | :partly\_sunny: | :partly\_sunny: | :partly\_sunny:       | :partly\_sunny: | :snowflake: | :cloud\_with\_lightning\_and\_rain: |
| [Off-chain][4]                     | :partly\_sunny: ![xli] ![yanivmo] ![martonmaya] | [:snowflake: 71][j71]     | :snowflake:     | :snowflake:           | :snowflake:     | :snowflake: | :snowflake:                         |
| [Faucet Client][5]                 | :sunny:                                         | :partly\_sunny: | :partly\_sunny: | :snowflake:           | :partly\_sunny: | :snowflake: | :snowflake:                         |
| [Packaging][6]                     | :sunny:                                         | :sunny:         | :sunny:         | :cloud: ![bmwill]     | :snowflake:     | :snowflake: | :snowflake:                         |
| [Verifying Client][7]              | [:snowflake: 201][p201]                         | [:snowflake: 68][j68]     | :snowflake:     | :cloud: ![anomalroil] | :snowflake:     | :snowflake: | :snowflake:                         |
| [Multisignature][8]                | [:snowflake: 202][p202]      | [:snowflake: 69][j69]     | :sunny:         | :sunny:               | :snowflake:     | :snowflake: | :snowflake:                         |
| [Mini Wallet][9]                   | :cloud: ![xli]                                  | [:snowflake: 70][j70]     | :snowflake:     | :snowflake:           | :snowflake:     | :snowflake: | :snowflake:                         |


> Rust SDK modules are developed in [Diem core codebase](https://github.com/diem/diem).


## JSON-RPC Client

| Feature                              | Python          | Java            | Go-lang         | Rust        | TypeScript  |
|--------------------------------------|-----------------|-----------------|-----------------|-------------|-------------|
| [JSON-RPC SPEC API][c1]              | :sunny:         | :sunny:         | :sunny:         | :sunny:     | :sunny:     |
| [Retry stale response error][c2]     | :partly\_sunny: | :partly\_sunny: | :partly\_sunny: | :sunny:     | :cloud:     |
| [Wait for transaction execution][c3] | :sunny:         | :sunny:         | :sunny:         | :sunny:     | :sunny:     |
| [Request strategy][c4]               | :sunny:         | :snowflake:     | :snowflake:     | :sunny:     | :snowflake: |
| [JSON-RPC Batch API][c5]             | :snowflake:     | :snowflake:     | :snowflake:     | :sunny:     | :snowflake: |
| [Off-chain resource query APIs][c6]  | :sunny:         | :snowflake:     | :snowflake:     | :snowflake: | :snowflake: |
| [Async IO API][c7]                   | :snowflake:     | :snowflake:     | :snowflake:     | :sunny:     | :snowflake: |
| [User-Agent HTTP Header][c8]         | :snowflake:     | :snowflake:     | :snowflake:     | :snowflake: | :snowflake: |


## Off-chain

| Feature                              | Python                           | Java        | Go-lang     | Rust        | TypeScript  |
|--------------------------------------|----------------------------------|-------------|-------------|-------------|-------------|
| [JWS][o1]                            | :sunny:                          | :snowflake: | :snowflake: | :snowflake: | :snowflake: |
| [Offchain Client][o2]                | :sunny:                          | :snowflake: | :snowflake: | :snowflake: | :snowflake: |
| [Data Deserialization][o3]           | :sunny:                          | :snowflake: | :snowflake: | :snowflake: | :snowflake: |
| [Data Validations][o4]               | :partly\_sunny: ![xli]           | :snowflake: | :snowflake: | :snowflake: | :snowflake: |
| [Payment Command][o5]                | :sunny:                          | :snowflake: | :snowflake: | :snowflake: | :snowflake: |
| [Fund Pull Pre-Approval Command][o6] | :cloud: ![yanivmo] ![martonmaya] | :snowflake: | :snowflake: | :snowflake: | :snowflake: |


## Status Emoji

:sunny: : complete; documentation and examples improvements are welcome.

:partly\_sunny: : feature works as MVP, but not fully match the specification, need improvement.

:cloud\_with\_lightning\_and\_rain: : broken or out of dated.

:cloud: : MVP in development, feature incomplete.

:snowflake: : frozen, feature development is not started, no one is planning or working on it.

## Contribute

You may send a PR for adding new feature specifications or update SDKs' development status.
For questions and discussions, please open an [issue](https://github.com/diem/client-sdks/issues).

See [CONTRIBUTING](CONTRIBUTING.md) for more details.


[1]: specs/bcs_runtime.md
[2]: specs/transaction_builder_generator.md
[3]: #user-content-json-rpc-client
[4]: #user-content-off-chain
[5]: specs/faucet_client.md
[6]: specs/packaging.md
[7]: specs/verifying_client.md
[8]: https://github.com/diem/diem/tree/master/specifications/crypto#multi-signatures
[9]: specs/mini_wallet.md

[c1]: specs/json_rpc_client.md#user-content-json-rpc-spec-api
[c2]: specs/json_rpc_client.md#user-content-retry-stale-response-error
[c3]: specs/json_rpc_client.md#user-content-wait-for-transactoin-execution
[c4]: specs/json_rpc_client.md#user-content-request-strategy
[c5]: specs/json_rpc_client.md#user-content-json-rpc-batch-requests
[c6]: specs/json_rpc_client.md#user-content-off-chain-resource-query-apis
[c7]: specs/json_rpc_client.md#user-content-async-io
[c8]: specs/json_rpc_client.md#user-content-user-agent-http-header

[f1]: specs/faucet_client.md#user-content-mint-coins
[f2]: specs/faucet_client.md#user-content-create-dd-account

[o1]: specs/off_chain.md#user-content-jws
[o2]: specs/off_chain.md#user-content-offchain-client
[o3]: specs/off_chain.md#user-content-data-deserialization
[o4]: specs/off_chain.md#user-content-data-validations
[o5]: specs/off_chain.md#user-content-payment-command
[o6]: specs/off_chain.md#user-content-fund-pull-pre-approval-command

[l1]: https://github.com/diem/client-sdk-python
[l2]: https://github.com/diem/client-sdk-java
[l3]: https://github.com/diem/client-sdk-go

[xli]: https://github.com/xli.png?size=20 "@xli"
[bmwill]: https://github.com/bmwill.png?size=20 "@bmwill"
[anomalroil]: https://github.com/anomalroil.png?size=20 "@anomalroil"
[yanivmo]: https://github.com/yanivmo.png?size=20 "@yanivmo"
[martonmaya]: https://github.com/martonmaya.png?size=20 "@martonmaya"


[p201]: https://github.com/diem/client-sdk-python/issues/201
[p202]: https://github.com/diem/client-sdk-python/issues/202

[j68]: https://github.com/diem/client-sdk-java/issues/68
[j69]: https://github.com/diem/client-sdk-java/issues/69
[j70]: https://github.com/diem/client-sdk-java/issues/70
[j71]: https://github.com/diem/client-sdk-java/issues/71
