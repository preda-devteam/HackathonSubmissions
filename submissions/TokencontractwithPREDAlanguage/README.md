I'm submitting a FungibleToken contract based on the token variables in PREDA. 

Three interface contracts: IFungileToken.prd, defining the behavior of FungibleToken; IWallet.prd, defining transfer of tokens; and IStorage.prd, defining storage of tokens.

A Wallet contract is also implemented for the transfer of tokens between wallets. As the Wallet contract has the IStorage interface, tokens can be transferred to other contracts implementing the IStorage interface. So that tokens can be transferred with flexibility between different contracts and addresses, independent of the issuer contract's control.




