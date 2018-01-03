# BLOCKNET

![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/block.PNG "Logo Title Text 1")

Internet delle Blockchains


## Documento FAQ prodotte dalla community


### Cos'é Blocknet?
Blocknet é un'infrastruttura a uso generale per servizi inter-blockchain. é progettata per per abilitare gli ecosistemi token emergenti. il primo prodotto costruito su questa infrastruttura é un exchange decentralizzato.

### Che cosa fa?
Blocknet abilita servizi inter-blockchain, come exchange decentralizzo, monetizzazione sfruttamente API, e consegna di servizi digitali p2p. Queste sono le funzionalitá principali delle daaps inter-chain.

### Come funziona?
Per supportare servizi inter-blockchain, blocknet ha 3 compenenti principali, i quali lavorano insieme per fornire tre servizi principali.

* I componenti principali sono:

  * Un router blockchain, xbridgep2ptm

  * Un protocollo per un exchange di monete

  * Un sistema di trasporto di dati inter-chain

* I servizi principali sono:

  * Exchange decentralizzato per le monete

  * Consegna del servizio inter-blockchain

  * Monetizzazione del servizio
  
  
### Cos'é un exchange decentralizzato?
un exchange decentralizzato é un servizio che permette alle controparti (che possono essere persone o macchine) di scambiare una valuta o un token per un'altra, senza il coninvolgimento di nessuna terza parte come intermediario.

Il termine "decentralizzato" denota la questione di controllo piú che la distribuzione del processo; L'idea di una soluzione decentralizzate é per le parti  una determinata interazione di essere attori auto-sovrani, nel senso che nessuna terza parte é richiesta per agire in loro conto al fine di permettere l'avvenimento dell'interazione.

### Come funziona un exchange decentralizzato?
Gli exchanges hanno 4 funzioni principali:

  * Deposito di capitali

  * Trasmissione di un ordine

  * Accoppiamento di un ordine

  * Scambio dei tokens

Perció, al fine di essere un exchange decentralizzato, ogniuna di queste funzioni deve essere decentralizzata.

Blocknet le decentralizza nel seguente modo:

* Il capitale dei traders rimane nel loro wallet, e non viene affidata ad alcuna terza parte in nessuna fase.

* Gli ordini vengono trasmessi direttamente da trader a trader su un overlay di rete inter-blockchain DHT. Le app dei traders compilano il libro ordini da sole invece di far affidamente su un libro ordini centralizzato.

* Orders are matched directly between traders. When one accepts another’s order, their apps communicate to set up the coin exchange process, and this is broadcast over the inter-chain network.

* The exchange of tokens is achieved without the involvement of an intermediary, in a manner that does not require counterparties to trust one another beforehand. An atomic protocol is utilised (meaning that either the exchange of both currencies takes place, or nothing takes place), which employs  OP_CHECKLOCKTIMEVERIFY to nullify transaction malleability-based attacks. More details on the protocol are available here: http://kaykurokawa.blogspot.co.za/2015/10/atomic-cross-chain-transfer-overview.html


### Why Is a Decentralized Exchange a Key Enabler Of the Token Ecosystem?
Decentralized exchange makes blockchain services intrinsically monetizable, removing the friction and high costs of traditional payment networks that have prevented the monetisation of the bulk of the API ecosystem.

Due to the decentralized exchange, consumers of a service may pay in their native token even if the service consumes a different token. In a world in which (a) there are already thousands of blockchains, and (b) blockchains bloat inexorably, and so it is advisable not to support many services per blockchain, monetising inter-chain services is both an operational necessity and an ecosystem-enabling service.


### What Coins Does the Decentralized Exchange Support?
The Blocknet was designed to maximise interoperability, and so most blockchain tokens may be integrated with no coding required.

The current integration requirements are:

* Support for OP_CHECKLOCKTIMEVERIFY

* A stock JSON RPC interface from Bitcoin Core

As a result, the Blocknet supports the majority of cryptocurrencies in existence, and no permission from anyone is required for these to be traded on the exchange.


### How Fast Is the Decentralized Exchange?
Instant.

However, note that once you have completed a trade and received coins, you will be dependent on their blockchain’s accepted confirmation time before your coins will be spendable again.

*Note: A future enhancement to the decentralized exchange may include a filter on the order book to enable traders to trade coins with less than the number of confirmations conventionally agreed upon as “safe.” This incurs a degree of risk for the benefit of supporting trading styles that require rapidly entering and exiting a position, such as scalping.*


### How Private Is the Decentralized Exchanged?
Because decentralized exchanges do not require traders to submit KYC information or divulge anything else about themselves to a third party, traders enjoy a naturally high degree of privacy.

However, for most wallets, aspects of transactions are linkable to IP addresses, so in order to obfuscate that, one might use TOR or I2P. The Blocknet’s DHT network overlay does not use IP addresses, however.

Combined with any privacy-centric coin, a decentralized exchange run over IP-obfuscating tech is a near-perfect mixing solution. For example, one may trade some coins for Zcash, sends them to a different address, and then trade back again.

### What Are the Possible Applications Of the xBridge Protocol Other Than a Decentralized Exchange?
The Blocknet is designed as infrastructure for the emerging token ecosystem. Any service or orchestrated sequence of microservices provided by dapps may be delivered over the Blocknet's infrastructure.

Using decentralized exchange, these services are intrinsically monetizable, removing the friction and high costs of traditional payment networks - friction which has prevented the monetisation of the bulk of the API ecosystem.

Due to the decentralized exchange, consumers of a service may pay in their native token even if the service consumes a different token.
 
 
### What Are the Benefits Of Running a Node? How Many Blocks Do I Need To Run One?
There are two types of node: a "service node" and a “trader node”. Service nodes do not handle or control any trader's coins. Their function is to collect and distribute trade fees. Typically a service node operator will run multiple full node wallets of whichever coins (s)he wants to support, in order to garner as many trade fees as possible. Trader nodes enable one to trade on the decentralized exchange.The amount of BLOCK currently needed to run a service node is 5,000 BLOCK. To use the exchange you will not need any BLOCK.
 
 
### Will There Be Fees For Buying/Trading On the Blocknet Exchange?
Yes, there are fees, though they are significantly lower that centralised exchanges.

The fee structure is as follows:
  * Transactions over the networks of each of your currency pairs will remain subject to their normal network fees for P2SH transactions

  * A tiny trade fee is charged in BLOCK and the software takes care of securing some BLOCK to pay the fee.


### Will A User Need BLOCK To Participate On An Exchange?
No, to use the exchange you will NOT need any BLOCK. Only the service node operators will need BLOCK in order to collect and distribute trade fees. Additionally, the service nodes do not handle or control and trader’s coins. The sole purpose of the service node is to only collect and distribute trade fees.

---
Ongoing questions/answers can be found on Reddit: [Reddit Blocknet Q/A](https://www.reddit.com/r/theblocknet/comments/676buj/ask_anything_about_blocknet_qa/)
