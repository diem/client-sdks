# Faucet Client

Faucet Server API document: https://github.com/diem/diem/blob/master/client/faucet/README.md.

For making sure your code (since you're connecting to Testnet, it's probably testing code) can handle server side data eventual consistency, the Faucent client should not create its own [JSON-RPC Client](json_rpc_client.md).

## Mint Coins

You don't need make `return_txns` query param as an option, set it `true` for every request, then decode the respond transactions and wait for the transactions executed successfully. If any transaction execution failed, retry.

* Useful functions may consider to add on top of `mint` function:
  * `gen_account` with `is_designated_dealer`, `currency_code`, `base_url` options.
  * `gen_child_vasp` with a `parent_vasp` account info, `initial_balance` and `currency`.


## Create DD Account

By default, Faucet service creates a parent VASP account for you, make an option to pass in `is_designated_dealer` param for the request, so that caller can create designated dealer account. [Python SDK Example](https://diem.github.io/client-sdk-python/diem/testnet.html#diem.testnet.Faucet.mint).
