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

* Gli ordini vengono abbinati direttamente tra traders. Quando uno accetta l'ordine di un altro, le loro app comunicano per far avvenire il processo di scambio delle loro monete, e ció viene trasmesso sulla rete inter-chain.

* Lo scambio di tokens viene realizzato senza il coinvolgimento di un intermediario, in una maniera che non richiede alle controparti di fidarsi l'una con l'altra in anticipo. Viene utilizzato un protocollo Atomic (singifica che o avviene lo scambio di entrambe le monete, o non viene scambiato nulla), il quale impiega  OP_CHECKLOCKTIMEVERIFY per annullare gli attacchi basati su transazioni malleabili. Maggiori dettagli sul protocollo sono disponibili qui: http://kaykurokawa.blogspot.co.za/2015/10/atomic-cross-chain-transfer-overview.html

### Perché un exchange decentralizzato é un elemento chiave dell'ecosistema token?
Gli exchange decentralizzati rendono i servizi blockchain intrinsecamente monetizzabili, rimuovendo le frizioni e gli alti costi delle reti di pagamento tradizionali che hanno prevenuto la monetizzazione dell'ecosistema API.

Grazie agli exchange decentralizzati, i consumatori di un servizio possono pagare con i loro token nativi anche se il servizio consuma un token differente. In un mondo in cui (a) sono presenti centinaia di blockchains, e (b) le blockchains sono sovraccaricate inesorabilmente, é consigliabile di supportare troppi servizi sulla stessa blockchain, monetizzare i servizi inter-chain é sia un'operazione necessaria e sia un servizio che aiuta l'ecosistema in generale.

### quali monete l'exchange decentralizzato supporta?
Blocknet é stato progettato per massimizzare l'interoperabilitá, quindi molti tokens possono essere integrati senza la necessitá di codice.

I requisiti di integrazione correnti sono:

* supporto di OP_CHECKLOCKTIMEVERIFY

* Un'interfaccia JSON RPC dal Core di Bitcoin

Come risultato, Blocknet supporta la maggioranza delle cryptomonete esistenti, e non é richiesto alncun permesso da nessuno per poter scambiate sull'exchange.


### Quanto é veloce l'exchange decentralizzato?
Istantaneo.

Comunque, nota che una volta che hai completato uno scambio e ricevuto le monete, dipenderai dal tempo di conferma impiegato dalla rispettiva blockchain prima che le tue monete siano nuovamente spendibili dinuovo.

*Nota: Un futuro miglioramento agli exchange decentralizzati potrebbe includere un filtro sul libro degli ordini per permettere ai traders di scambiare monete con un numero inferiore di conferme convenzionalmente accettate come "sicure". Ció comporta un certo grado di rischio a vantaggio del supporto di stili di trading che richiedono di entrare e uscire rapidamente  da una posizione esistente, come lo scalping.*

### Quanto é privato un exchange decentralizato?
Perché decentralizzato l'exchanges non richiede l'invio di informazioni KYC o divulgare nient'altro a proposito di te stesso a una terza parte, i traders godono naturalmente di un elevato grado di privacy.

Comunque, per molti wallets, alcuni aspetti delle transazioni sono collegabili all'indirizzo IP, quidni al fine offuscarlo, si potrebbe usare TOR o I2P. La rete overlay DHT di Blocknet non richiede l'uso di indirizzo IP, comunque.

Combinato con ogni moneta centrata sulla privacy, un exchange decentralizzato viene eseguito su tecniche di offuscamento dell'indirizzo IP in una soluzione mix quasi perfetta. Per esempio, é possibile scambiare alcune monete per Zcash, inviarle a un indirizzo differente, e dopo scambiare nuovamente.

### Qauli sono le possibili applicazioni del protocollo xBridge oltre all'exchange decentralizzato?
Blocknet é progettata come infrastruttura per gli emergenti ecosistemi token. Ogni servizio o sequenza orchestrata di microservizi fornita dalle daaps potrebbe essere fornita sulla struttura della blockchain

Usando gli exchange decentralizzati, questi servizi sono intrinsecamente monetizzabili, rimuovendo le frizioni e gli alti costi delle tradizionali reti di pagamento - frizione che ha prevenuto la monetizzazione dell'ecosistema API.

Grazie agli exchange decentralizzati, i consumatori di un servizio possono pagara con i loro token nativi anche se il servizio consuma un token differente.

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
