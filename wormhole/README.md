

Wormhole architecture:
https://book.wormhole.com/wormhole/2_architectureOverview.html 

Wormhole contract addresses: 
https://book.wormhole.com/reference/contracts.html


# Based on Binance Chain code

For an app to request a function call on a remote chain, call Implementation.publishMessage.

An app contract can verify a message by calling Messages.parseAndVerifyVM.

Admin functions (shown below) are public and don't do any authentication beyond checkinf that the signatures and threshold are correct for the VM.

* submitContractUpgrade
* submitSetMessageFee
* submitNewGuardianSet
* submitTransferFees

