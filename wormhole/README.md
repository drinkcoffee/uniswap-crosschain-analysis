

Wormhole architecture:
https://book.wormhole.com/wormhole/2_architectureOverview.html 

Wormhole contract addresses: 
https://book.wormhole.com/reference/contracts.html


# Based on Binance Chain code

For an app to request a function call on a remote chain, call Implementation.publishMessage.

An app contract can verify a message by calling Messages.parseAndVerifyVM. Note that replay protection is the responsibility of the app contract.

Admin functions (shown below) are public and permissionless (that is, no msg.sender == ). They do the admin checks: the signatures and threshold are correct for the VM, the message was emitted from the governance contract on the governance chain, and there is replay protection.

* submitContractUpgrade
* submitSetMessageFee
* submitNewGuardianSet
* submitTransferFees

