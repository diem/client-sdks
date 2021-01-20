# Off-chain

[DIP-1] off-chain protocol is designed for 2 VASPs to update the payment object in sequence like playing ping-pong. It requires a two-phase commit process for making sure two VASPs command object data are synchronized when one VASP updates the command object.

SDK off-chain module provides building blocks for creating such a service in multiple areas.

## Offchain Client

SDK off-chain client should provide the following high level APIs for an application to communicate with counterparty off-chain API service:

* send command:
  * Construct `CommandRequestObject` with a given command.
  * Serialize the `CommandRequestObject` into a JWS message.
  * Look up counterparty onchain account resources.
  * Send the JWS message to the counterparty off-chain service API.
  * Verify the response JWS message and handle HTTP errors.
  * Return the deserialized `CommandResponseObject`, or raise error for the failure response.
* process inbound request:
  * Verify inbound data.
  * Look up counterparty onchain account resources.
  * Deserialize inbound request body into `CommandRequestObject`.
  * Validate data according to the data type specification, and raise / return `OffChainErrorObject` for errors.
  * Return `Command` object.


## JWS

[JWS](https://tools.ietf.org/html/rfc7515) is a low level protocol used on top of HTTPS. SDK off-chain module may create or import a JWS implementation for encoding and decoding off-chain API JWS messages.

Please refer to [DIP-1] for details.

## Data Deserialization

SDK off-chain module should provide native language data types for the types defined by [DIP-1] and it's extension DIPs. On top of native data types, we also need to provide a framework for serializing/deserializing the data type to/from JSON data.

JSON serialization and deserialization are widely supported in most languages. However, there is one problem needs special handling as no JSON deserialization is likely to support it without customization:
* `CommandRequestObject` field `command` is a dynamic data type.

Both `CommandRequestObject#command_type` and `CommandRequestObject#command#_ObjectType` can be used to indicate what is the type of the `CommandRequestObject#command` JSON object.

You can choose one of them for deserialization, and validate the other one is same value.


## Data Validations

SDK off-chain module should provide a data validation framework for validating the data types it defines.

We need the following validations for a field value:
1. is required.
2. can only be written once across the object lifecycle.
3. can only be written once at object creation time.
4. is an enum.
5. is a specific type.

For all validations, we need split them into 2 steps:
1. Validations w/o prior command object: can be performed after we deserialize the input request data into command object.
2. Validations w/ prior command object: can be provided as utility functions by the `Command` type for the user to call before saving the command object. See the following commands sections for more details.


## Command Interface

A `command` object should meet the following interface:

| name               | arguments       | return type          | description                                                              |
|--------------------|-----------------|----------------------|--------------------------------------------------------------------------|
| id                 | N/A             | string               | A unique command id, it is `cid` defined in [DIP-1].                     |
| is\_inbound        | N/A             | boolean              | Indicate the command is inbound or outbound                              |
| follow\_up\_action | N/A             | action enum          | Indicate what is action should be followed up for processing the command |
| reference\_id      | N/A             | string               | The reference id defined in [DIP-1], it is hex-encoded bytes value       |
| new\_command       | Changes[1]      | Command              | An utility function for creating updated command from existing command   |
| validate           | Command or None | (Raise/return) error | This function validates the object with a prior command object.          |

[1]: Depending on language, changes that can be applied to the command object data and create new command objects.

## Payment Command

A `Command` object implementation to wrap `PaymentCommand` utility functions and validation logic with a prior command.

:building\_construction:

## Fund Pull Pre-approval Command

A `Command` object implementation to wrap `FundPullPreApprovalCommand` utility functions and validation logic with a prior command.

:building\_construction:


[DIP-1]: https://dip.diem.com/dip-1
