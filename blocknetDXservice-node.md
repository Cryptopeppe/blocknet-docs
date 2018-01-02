# BLOCKNET
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/block.PNG "Logo Title Text 1")

Internet Delle Blockchains

## Exchange Decentralizzato Blocknet Configurazione Del Nodo Di Servizio

**Queste istruzioni devono essere eseguite come nodo di servizio per l'exchange decentralizzato Blocknet.** 

* Il DX di Blocknet usa la tecnologia blockchain router xbridgep2p™ per consentire agli utenti di scambiare monete e assets, e utilizzare contratti smart tra blockchains.

## Panoramica
La configurazione richiede un'integrazione tra il wallet Blocknet e il wallet delle monete volute come coppia di valuta. A questo punto, niente é automatizzato e la UI sul nuovo wallet Blocknet sará usata fino a che la UI finale non sia completa. Configurazione creata manualmente (o modifiche) .conf dei files:  

 * blocknetdx.conf
 
 * servicenode.conf

 * xbridge.conf

 * file di configurazione per ogni valuta si desidera supportare

L'integrazione avviene tramite le API RPC del wallet. Per ragioni di sicurezza raccomandiamo di eseguire tutti i wallets su un'unica box e comunicare su localhost (127.0.0.1), anche se i wallets possono anche essere eseguiti su macchine differenti ed essere connessi tramite indirizzo IP. La documentazione generale e le funzionalitá JSON RPC sono disponibili a https://en.bitcoin.it/wiki/Running_Bitcoin.

## Requisiti
* Due computers con l'ultimo client di Blocknet installato, criptato, completamente sincronizzato 
   * Il computer #1 sará il Service Node Server il quale dovrá essere operativo 24/7
      * Questa guida si riferirá a questo computer come " SNODE SERVER "
      
   * Il computer #2 sará il computer client dove sono bloccati 5000 blochi. Non vi é bisogno di un'operativitá 24/7.
      * Questa guida si riferirá a questo computer come " CLIENT "

* L'indirizzo pubblico IP del tuo computer SNODE SERVER. O l'indirizzo IP pubblico se stai usando una VPS/VPN per il computer SNODE SERVER.

* 5000 Block bloccati all'indirizzo del nodo di servizio sul computer CLIENT (i 5000 Block non possono essere soggetti a stake finché rimangono bloccati)

* L'ultima versione del wallet di ogni criptovaluta che vuoi supportare sul tuo nodo di servizio (completamente sincronizzato, criptato)

* I files .conf propriamente configurati per ogni wallet


## Impostazione Del Nodo Di Servizio

* scarica l'ultima versione del wallet su due computer o VPS 
   * [GitHub Releases](https://github.com/BlocknetDX/BlockDX/releases)
   
* Su ogni computer lascia sincronizzare completamente il wallet. Una volta completato cripta entrambi i wallets con una password a tua scelta 
   * Se stai facendo testing per favore usa `testnet=1` o `-testnet` per `blocknetdx-qt.exe`
   
### Impostazione Del Wallet Del Computer Client   
   
* Navigare dalla barra degli strumenti a: `Tools > Debug console`
   * Scrivi `getaccountaddress <name>` (Questo genera una chiave a indirizzo pubblico per il tuo nodo di servizio. Crea un unico nome per il nodo di servizio.)
      * Es: `getaccountaddress snode01`
      
   * Scrivi `servicenode genkey` (Ció genera e produce la chiave privata del tuo nodo di servizio)
   
   * Prendi nota di questi prodotti generati siccome saranno necessari nei files di configurazione
   
* Qualsiasi sia il wallet sul quale i tuoi fondi sono situati invia esattamente 5000 Block (tBlock in testnet) all'indirizzo pubblico che hai creato nello step precedente
   * L'indirizzo deve avere ESATTAMENTE 5000 Block (o tBLock) per lavorare adeguatamente
   
   * Sotto l'opzione "Send", clicca il bottone "Choose..." accanto l'opzione Transaction Fee. Quando invii i 5000 Block, assicurati che "Send as zero-fee transaction if possible" sia spuntato. 
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/send_5000.PNG "Logo Title Text 1")
   
* Aspetta che il computer CLIENT riceva i 5000 Block e abbia almeno 15 confermazioni sulla TX

* Una volta che la TX é completamente confermata torna indietro a: `Tools > Debug console`
   * Scrivi `servicenode outputs` (Ció produce le informazioni TX sul nodo di servizio necessarie nel `servicenode.conf`)
   
   * Prendi nota di questi outputs generati siccome saranno necessari nei files di configurazione
   
* Adesso hai bisogno di recuperare l'indirizzo IP pubblico del tuo computer SNODE SERVER. Se usi solamente un indirizzo IP pubblico, vai su Google e cerca "what's my ip". Ti verrá mostrato il tuo indirizzo IP pubblico. Prendi nota di questo indirizzo siccome sará necessario per la configurazione dei files
   * Se stai usando una VPN o una VPS per il computer SNODE SERVER, devi recuperare quell'indirizzo IP pubblico.
   * Gli utenti della Main-net usano YOUR_PUBLIC_IP:41412
   * Gli utenti della Test-net usano YOUR_PUBLIC_IP:41474
   
* Naviga fino alla tua BLOCKENT directory (la predefinita é: `%appdata%/roaming/blocknetdx/`)
   * Creare/modificare il file `servicenode.conf` (`/blocknetdx/testnet4/` per utenti testnet)
   
   * Vi é un esempio di come la configurazione dovrebbe essere fatta in questo file: (puoi eliminarlo dopo che il tu)
  o é stato scritto) ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/snode_conf_ex.PNG "Logo Title Text 1")
   
   * Inserisci le informazioni generate da sopra nel format mostrato in questo esempio:
   ```
   snode01 <YOUR_PUBLIC_IP:41474> <YOUR_SERVICENODE_PRIVATE_KEY> <COLLATERAL_TX_OUTPUT> <TX_OUTPUT_INDEX>
   ```
   
   * Salva `servicenode.conf` 
   
   * Creare/Modificare `blocknetdx.conf`. Aggiungere `staking=0`. Salvare `blocknetdx.conf`
  
   * Riavviare il wallet. Sbloccare completamente il wallet.
   
### Configurazione wallet computer SNODE SERVER

* Naviga fino alla tua directory Blocknet data (la predefinita é: `%appdata%/roaming/blocknetdx/`)
   * Creare/modificare il file `blocknetdx.conf` 
     * Se stai usando la testnet, `blocknetdx.conf` deve rimanere in `%appdata%/roaming/blocknetdx/` e NON nella cartella `/testnet4/` 
     
   * Scrivi le seguenti informazioni nel tuo file `blocknetdx.conf`: (usa staking=1 se vuoi fare stake sul client SNODE SERVER client)
   
   ```
   staking=1
   servicenode=1
   servicenodeaddr=YOUR_PUBLIC_IP:41412
   servicenodeprivkey=YOUR_SERVICENODE_PRIVATE_KEY
   ```
   
   * Salva la `blocknetdx.conf` e riavvia il wallet. Sblocca completamente il wallet.
   
### Avvio Del Nodo(i) Di Servizio

* Sul computer CLIENT navigare fino al bottone "Servicenodes" sulla GUI. Se la configurazione é stata fatta correttamente dovresti vedere tutti i tuoi "Aliases"

#### Attiva Tramite La Console Di Debug

* Navigare a `Tools > Debug console`

* Scrivere: `servicenode start-alias <name>` es: `servicenode start-alias snode1`

* Lo status del tuo nodo(i) dovrebbe essere "ENABLED" e mostrare un "Active time"
   * Potrebbe richiedere un momento per mostrare enabled e/o un active time.
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/snode_alias.PNG "Logo Title Text 1")    
   
* Il tuo nodo(i) é in esecuzione correttamente. Puoi chiuedere il computer CLIENT Blocknet wallet se vuoi.
   
* Il computer CLIENT riceverá il " Servicenode Rewards "


### Controllo Status

* Sul computer SNODE SERVER dal toolbar navigare a: `Tools > Debug console`
   * Scrivere `servicenode debug` (Ció produrrá un messaggio "Servicenode successfully started")
   
   * Scrivere `servicenode status` (Ció produrrá le informazioni sul tuo nodo di servizio e alla fine un messaggio di successo)
   
  ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/snode_status.PNG "Logo Title Text 1")    
   
* Se non hai ricevuto "Servicenode successfully started" procedi a "Troubleshooting section"

* Se hai ricevuto "Servicenode successfully started" procedi nella configurazione dei files .conf per il wallet sul tuo nodo di servizio
   
   
### Risoluzione Dei Problemi

* Assicurati che le informazioni di `servicenode.conf` siano corrette per le tue impostazioni

* Assicurati di non avere nessuna "< >" in ogni tuo files di configurazione: (es: `servicenodeaddr=<your_public_IP:41474>` dovrebbe essere `servicenodeaddr=127.0.0.1:41412`. "127.0.0.1 é un esempio di indirizzo IP")
   * Assicurati di usare la corretta P2P PORT #
     * Main-net=`41412` 
     * Test-net=`41474`

* Assicurati che sul computer CLIENT hai solamente `servicenode.conf`, e `blocknetdx.conf` non é necessario sul computer CLIENT 
   * Per la testnet assicurati che `servicenode.conf` é collocato in `/testnet4/`

* Assicurati che sul computer SNODE SERVER hai solamente`blocknetdx.conf`, e `servicenode.conf` non é necessario sul computer SNODE SERVER 
   * Per la testnet assicurati che `blocknetdx.conf` sia collocato in `/blocknetdx/` e non `/testnet4/`
   * Se sei un tester, ci sará una guida di inizio linea CMD cosí non hai bisogno di modificare questa configurazione quando passi dalla main-net alla test-net
   
* Assicurati che il tuo file di configurazione non sia `servicenode.conf.txt`

* Assicurati che i 5000 Block siano esattamente 5000 Block, non uno in piú non uno in meno e assicurati che siano confermati

* Assicurati di aver l'ultima versione del wallet e che sia completamente sincronizzato e completamente sbloccato   
   
---

## Configurazione Dei Files .conf Per i Wallets Sul Tuo Nodo Di Servizio
Il wallet di ogni moneta che vuoi ospitare deve essere configurato con un username/password e un permesso dall'IP, se stai usando solo una macchina locale usa IP:127.0.0.1

* Per vedere la lista completa dei wallet compatibili alla configurazione vai a: [Configurazioni Wallets](https://github.com/BlocknetDX/blocknet-docs/blob/master/walletsCONF.md)

 * Scarica l'ultima versione del wallet, lascialo sincronizzare completamente, successivamente chiudi il wallet

 * Clicca il bottone START sul tuo desktop, dove dice "Cerca programmi e files" scrivi “%appdata%”  e poi dovrebbe apparire la directory "Roaming". Clicca su "Roaming" o premi invio.
 
 * Trova le informazioni del tuo wallet nellcartella della sua directory, es: Bitcoin

 * Se non hai un file .conf avviato devi aprire Notepad per crearne uno.

 * Naviga a [Configurazioni Wallet](https://github.com/BlocknetDX/blocknet-docs/blob/master/walletsCONF.md) e copia/incolla le informazioni di configurazione per il wallet che stai eseguendo. (Puó essere agiunto a quanto giá presente nel file se hai “addnodes” o altre configurazioni):
   * Es: bitcoin.conf
   
   ```
   server=1
   listen=1
   rpcuser=yourusername
   rpcpassword=yourpassword
   rpcallowip=127.0.0.1
   ```
   
   * Assicurati che la configurazione sia corretta.Non presupporre che le configurazioni siano uguali per ogni wallet.

 * Cambia `rpcuser` e `rpcpassword` in qualcosa di unico per te. Per ragioni di siscurezza dovresti avere un username e password RPC differente per ogni wallet

 * Se stai usando una singola macchia usa IP: `127.0.0.1`

 * Quando hai finito, clicca File, Salva come, Scrivi: `bitcoin.conf`
    * Assicurati che il file non sia `bitcoin.conf.txt`

 * Salvalo e rimpiazza il .conf nella cartella corrispondente del wallet
    * Per questo esempio: %Appdata%/Roaming/Bitcoin 

 * Ricorda cos'hai scritto per l'username, password, e IP

 * Creare i files .conf per ogni wallet che userai sull'exchange decentralizzato.
    * Assicurati che `rpcuser` e `rpcpassword` siano differenti su ogni wallet per ragioni di sicurezza
 
---

## Configurare Gli Indirizzi Delle Monete
In ogni wallet ospitato, creare un nuovo indirizzo ed etichettarlo con qualcosa di informativo, come "indirizzo DX" (xbridge si aspetta un indirizzo di ricezione etichettato)

 * Per creare un nuovo indirizzo, vi alla scheda del wallet “receive” e clicca “new address”

 * Per etichettare un indirizzo, devi fare doppio clic sopra oppure clicca il campo “label”.
 
 ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/labelledaddress.PNG "Logo Title Text 1") 

 * Ció va fatto per tutti i wallet che vengono usati

---

## Configurazione xbridge.conf

La tecnologia Xbridge di Blocknet é integrata nell'ultima versione del client. Vedi [GitHub](https://github.com/BlocknetDX/BlockDX) per il codice sorgente.

 * Per vedere la lista completa delle monete .conf vedi: [xbridge.conf](https://github.com/BlocknetDX/blocknet-docs/blob/master/xbridgeCONF.md)

 * Creare/modificare un file `xbridge.conf` posizionando il seguente file di configurazione nel wallet Blocknet nelal directory data (per Windows) C:\Users\[yourusername]\AppData\Roaming\blocknetdx\

 * Nota: Per evitare crashes o trade invalidi, per favore modifica le funzionalitá `xbridge.conf` su solo o tutte le coin che desideri avere sul tuo nodo di servizio

 * Incolla l'username e la password RPC che hai creato per ogni coppia di valuta nei campi “Username” e “Password” 
 
 * Incolla l'indirizzo del "labelled receive address" che hai creato per ogni coppia di valuta
 
 * Assicurati che il resto delle configurazioni combaci con [xbridge.conf](https://github.com/BlocknetDX/blocknet-docs/blob/master/xbridgeCONF.md) per ogni moneta

 * Salva il file (se hai appena modificato il file esistente, clicca salva, se hai creato un nuovo file clicca file, salva come, e nel nome file scrivi: `xbridge.conf`
    * Assicurati che il file non sia `xbridge.conf.txt`

 * Posiziona il file nella cartella directory data di Blocknet: "C:\Users\[yourusername]\AppData\Roaming\blocknetdx\"

 * Potrai modificarlo in furuto per aggiungere nuove monete, e cambiare `RPCusername` `RPCpassword` `Port` `Address` 
 
 * Non cambiare altre impostazioni nel file .conf a meno che non stai facendo test in testnet.
 
---

## Sequenza di Avvio
 * Avvia le coppie di valuta che stai eseguendo sul tuo nodo
    * Asicurati che ogni wallet sia completamente sincronizzato e sbloccato
    
 * Avvia il wallet Blocknet sul computer SNODE SERVER con `-enableexchange`
    * es: blocknetdx-qt.exe -enableexchange

 * Se vuoi sempre avviarlo in modalitá exchange, doppio clic sull'icona desktop/cartella del tuo nodo blocknetdx-qt. Poi scegli proprietá. Cambia "...blocknetdx-qt.exe" a "...blocknetdx-qt.exe -enableexchange". Salva. Adesso inizierá sempre con questi attributi.
 
     * Quadno clicchi la finesta "BlocknetDX" sul wallet dovrebbe dire "Exchange node".
     * Nella console scrivi: `dxGetCurrencyList` per mostrare la lista di wallets aperti su xbridge
     * Nella console scrivi: `servicenode list`, cerca il tuo SNODE, sotto `xwallets` mostra i wallets che stai ospitando
       
 * Assicurati che il tuo nodo di servizio sia attivato.
  
---

## Verifica La Comunicazione Tra Wallets.
Al fine di assicurarti che il client xbridge stia comunicando con i tuoi wallets e i files .conf siano configurati correttamente, naviga fino al Blocknet data dir: C:\Users\yourusername\AppData\Roaming\blocknetdx\

   * Apri la cartella "log". Apri il file log con la corrente data/tempo. Es: `xbridgep2p_20170831T181856.log`
   * Ogni file log verrá aggiornato finché l'istanza del client non viene chiusa. Se una nuova istanza del client viene aperta allora verrá creato un nuovo file log.
   
All'avvio del wallet, vedrai il DX usando i valori che hai inserito nel file `xbridge.conf`:

![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/dxstart.PNG "Logo Title Text 1") 

 * Aspetta fino a vedere il messaggio “HTTP: resp 200”. Ció significa che il wallets stanno comunicando tramite RPC e la configurazione é avvenuta con successo. Assicurati che ogni wallet che stai eseguendo mostri “HTTP: resp 200” e mostri anche il tuo indirizzo etichettato.
 
 ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/resp_200.PNG "Logo Title Text 1") 

 * Nota: Se, in mezzo al messaggio “HTTP: resp 200”, vedi un messaggio simile a `[I] 2017-Apr-19 17:48:31 [0x2],listaccounts exception couldn't connect to server`, significa che almeno uno dei tuoi wallets di trading specifici non sta funzionando correttamente.

 * Nota: Se fallisci nell'ottenere il messaggio “HTTP: resp 200” messages, é possibile che le porte assegnate ai wallets differiscano da quelle specificate nel file .conf. Per controllarlo, apri il Prompt dei Comandi, scrivi `netstat -an`, e dai un'occhiata a quale porta viene usata per il localhost (127.0.0.1), o a volte sopra 0.0.0.0.
 
---

## Diagnosi Dei Problemi
* Per verificare che ogni wallet sia in comunicazione con xbridge assicurati che l'indirizzo ricevente creato per ogni wallet sia elencato nel libro degli indirizzi. Se questa parte fallisce, chiudi i tuoi wallets e rivedi i loro file di configurazione.

* Se operi qualche cambio a qualsiasi file .conf devi chiudere e reiniziare quel wallet, incluso Blocknet

* verifica le porte attualmente aperte. puoi usare il Promp dei Comandi per farlo, scrivendovi `netstat -an` e controllando quanto viene visualizzato. Controlla che le porte specificate nei files .config (es: 8332 per Bitcoin) siano aperte sul localhost (127.0.0.1).

* Assicurati che tutti i files .config siano configurati propriamente. Queste configurazioni sono case sensitive. Qualsiasi dato sbagliato inserito potrebbe causare problemi.

* Controlla che nessun firewall basata sull'OS stai bloccando le comunicazione. Puoi farlo attraverso l'interfaccia del firewall.

* Controlla il log di xbridge per qualsiasi errore in: C:\Users\yourusername\AppData\Roaming\blocknetdx\log

* Cerca negli eventi generali del wallet in C:\Users\yourusername\AppData\Roaming\walletname\debug.log
