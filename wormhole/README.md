

Wormhole architecture:
https://book.wormhole.com/wormhole/2_architectureOverview.html 

Wormhole contract addresses: 
https://book.wormhole.com/reference/contracts.html


# Based on Binance Chain code

For an app to request a function call on a remote chain, call Implementation.publishMessage.

An app contract can verify a message by calling Messages.parseAndVerifyVM. Note that:

* Replay protection is the responsibility of the app contract.
* Pauing is the responsibility of the app contract.

Admin functions (submitContractUpgrade, submitSetMessageFee, submitNewGuardianSet,  submitTransferFees) are public and permissionless (that is, no msg.sender == ). They are expected to be called by an EOA relayer, though could be called by another contract. They do the admin checks: 

* Check that the the set of signers (the Guardian Set) is the latest one.  Separately it check that the Guradian set is active.
* Check that at least a threshold number of signers have signed.
* Check that all signers are separate.
* Check that the signatures are valid.
* The message was emitted from the governance contract on the governance chain.
* There is replay protection.


# Accounts / Addresses on Binance Chain:

Wormhole: Binance Smart Chain Core Bridge: Proxy contract
[https://bscscan.com/address/0x98f3c9e6e3face36baad05fe09d375ef1464288b](https://bscscan.com/address/0x98f3c9e6e3face36baad05fe09d375ef1464288b)

Core Bridge: Old Implementation
[https://bscscan.com/address/0x736d2a394f7810c17b3c6fed017d5bc7d60c077d#code](https://bscscan.com/address/0x736d2a394f7810c17b3c6fed017d5bc7d60c077d#code)

Core Bridge: New Implementation
[https://bscscan.com/address/0xb8c99a5812159a412c5bd5823d35e32e61ef6135#code](https://bscscan.com/address/0xb8c99a5812159a412c5bd5823d35e32e61ef6135#code)

Wormhole: Token Bridge: Proxy contract: 
[https://bscscan.com/address/0xb6f6d86a8f9879a9c87f643768d9efc38c1da6e7](https://bscscan.com/address/0xb6f6d86a8f9879a9c87f643768d9efc38c1da6e7)

Wormhole Token Bridge: New Implementation:
[https://bscscan.com/address/0x666ff2211b2228cc629d8969f9c857c295db3840#code](https://bscscan.com/address/0x666ff2211b2228cc629d8969f9c857c295db3840#code)


Wormhole deployer:
[https://bscscan.com/address/0x5b3899809ae2c87fda11280b7c61c06a5f4db1de](https://bscscan.com/address/0x5b3899809ae2c87fda11280b7c61c06a5f4db1de)

Relayer account used to submit transactions on Binance chain:
[https://bscscan.com/address/0xe2e2d9e31d7e1cc1178fe0d1c5950f6c809816a3](https://bscscan.com/address/0xe2e2d9e31d7e1cc1178fe0d1c5950f6c809816a3)



# Communications Flow

Relayer (an EOA) -> Token Bridge.completeTransfer -> Core Bridge.parseAndVerifyVM

Relayer (an EOA) -> Token Bridge.(some governane action on the token bridge) -> Core Bridge.parseAndVerifyVM

Relayer (an EOA) -> Core Bridge.(some governane action on the core bridge)

Note that the governance action request verification is different for the Core Bridge and the Token Bridge. 

