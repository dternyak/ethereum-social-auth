# ethereum-social-identity

A spec of public social identity for an ethereum address.


### What?
A public, smart contract + IPFS based public identity for Ethereum accounts.

### Why?
Web3, and more general, address based authentication (read: message signing) leaves some to be desired. 
Projects like [uPort](https://developer.uport.me/) are building SSO (Single Sign On) for Ethereum. While this effort is to be applauded, I envision a simpler system.

### Why would I want to associate my identity with an Ethereum address? Isn't Blockchain supposed to be private?
While some users of various chains may want complete privacy around their transactions, other users desire the exact opposite. 
For example, at [Grant.io](http://grant.io), we're building a platform for decentralized [crowd]funding.
Users on our platform may desire to be very public indeed, especially so that they can show the various projects they have granted money to.
In other cases, proposers on our platform will be required to provide _some_ additional identifying information, so that potential donors can properly vet them. 
Think associatiating an ethereum address with a (potentially anonymous) GitHub profile.

### Ok, so what's a typical flow?
1. User navigates to dapp.
2. User fills out form about themselves to sign in. This ONLY includes non-sensitive data, e.g. Name, Short bio, social media accounts. 
3. User signs a message with their form data to prove they filled it out, and is prompted to understand that the data they are signing will be made public. 
4. Data is sent to backend for processing.
5. Backend checks and validates social media accounts (presumably there is some oAuth done on the client as well)
6. Backend uploads the user’s form data + signed message to IPFS.
7. Backend updates an existing smart contract with userAddressHash->[userProfileIPFSDocument].
    7a. NOTE, in cases where a use is updating an already existing profile, a new IPFS document will be created and pushed to the above mapping. Thus, the current user account state will be found on HEAD.
    7b. While not fully outlined, the user will need to authorize (read: message sign) another address to act on behalf of them to update the contract, unless the user wants to pay for gas gasts (they don't).
8. Dapp can now hit contract, resolve the IPFS document, and get user identity on next sign in
9. Dapp can now hit contract, resolve IPFS data to provide to other users using the dapp.

### WHERES THE SPEC!?!?!
I'm working on it.

