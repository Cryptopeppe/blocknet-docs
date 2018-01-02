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
   * L'indirizzo deve avere ESATTAMENTE 5000 Block (or tBLock) per lavorare adeguatamente
   
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

## Setup  .conf Files for the Wallets on Your Service Node:
The wallet of each coin you want to host needs to be configured with a username/password and an allow from IP, if you’re using only a local machine use IP:127.0.0.1

 * To see the full list of compatible wallet configurations go to: [Wallet Configurations](https://github.com/BlocknetDX/blocknet-docs/blob/master/walletsCONF.md)

 * Download the latest wallet, let it sync up fully, then close the wallet

 * Click the START button on your desktop, where it says “Search program and files” then type “%appdata%” and the “Roaming” directory should pop up. Click on “Roaming” or hit enter

 * Find your wallet’s designated data directory folder, ex: Bitcoin

 * If you don’t have a .conf file started you will need to open up Notepad to create one.

 * Navigate to [Wallet Configurations](https://github.com/BlocknetDX/blocknet-docs/blob/master/walletsCONF.md) and copy/paste the configuration information for the wallet you are running. (this can be added to what is already present in file if you have “addnodes” or other configurations already):
   * Ex: bitcoin.conf
   
   ```
   server=1
   listen=1
   rpcuser=yourusername
   rpcpassword=yourpassword
   rpcallowip=127.0.0.1
   ```
   
   * Ensure the configuration is correct. Do not assume the configurations are the same for each wallet.

 * Change `rpcuser` and `rpcpassword` to something unique to you. For security reasons you should have a different RPC username and password for each wallet

 * If you’re using a single machine use IP: `127.0.0.1`

 * When you are done, click File, Save as, Type in: `bitcoin.conf`
    * Ensure the file is not `bitcoin.conf.txt`

 * Save it and then place the .conf into its corresponding wallet folder
    * For this example: %Appdata%/Roaming/Bitcoin 

 * Remember what you wrote for the username, password, and IP

 * Create .conf files for each wallet you are going to be using on the decentralised exchange.
    * Ensure `rpcuser` and `rpcpassword` are different on each wallet for security purposes
 
---

## Configure Coin Addresses
In each hosted coin wallet, create a new address and label it something informative, like “DX address” (xbridge expects a labelled receive address)

 * To create a new address, go to your wallet’s “receive” tab and click “new address”

 * To label an address, you may either right-click on it or click the “label” field.
 
 ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/labelledaddress.PNG "Logo Title Text 1") 

 * This needs to be done for all wallets being used

---

## Setup xbridge.conf

The Blocknet’s Xbridge technology is integrated into the latest client release. See [GitHub](https://github.com/BlocknetDX/BlockDX) for the source code.

 * To see the full list of coin .conf's see: [xbridge.conf](https://github.com/BlocknetDX/blocknet-docs/blob/master/xbridgeCONF.md)

 * Create/edit an `xbridge.conf` file and place the following configuration file in the blocknet wallet data directory (for Windows) C:\Users\[yourusername]\AppData\Roaming\blocknetdx\

 * Note: to avoid crashes or failed trades, please edit your `xbridge.conf` to feature only and all the coins you wish to have on your service node

 * Paste the RPC usernames and passwords you created for each currency pair into the “Username” and “Password” fields
 
 * Paste the address of the "labelled receive address" you created for each currency pair
 
 * Ensure the rest of the configuration matches [xbridge.conf](https://github.com/BlocknetDX/blocknet-docs/blob/master/xbridgeCONF.md) for each coin

 * Save the File (if you just edited the existing file, just click save, if you made a new file then click file, save as, and in the file name type: `xbridge.conf`
    * Ensure the file is not `xbridge.conf.txt`

 * Place this file into the Blocknet data directory folder: "C:\Users\[yourusername]\AppData\Roaming\blocknetdx\"

 * You will be coming back to this to edit it in the future to add future coins, and change `RPCusername` `RPCpassword` `Port` `Address` 
 
 * Do not change the other settings in the .conf file unless you are on testnet conducting tests.
 
---

## Startup Sequence
 * Start the currency pair(s) you are running on your service node
    * Ensure every wallet is fully sync'd and unlocked
    

 * Start the Blocknet wallet on the SNODE SERVER computer with `-enableexchange`
    * ex: blocknetdx-qt.exe -enableexchange

 * If you want to always start in exchange mode, right click on desktop/folder icon of your node blocknetdx-qt. Then choose properties. Then change "...blocknetdx-qt.exe" to "...blocknetdx-qt.exe -enableexchange". Save. Now it always start with these attributes.
 
     * When you click the "BlocknetDX" tab on the wallet it should say "Exchange node".
     * In the console type: `dxGetCurrencyList` to show your list of wallets running on your xbridge
     * In the console type: `servicenode list`, search for your SNODE, under `xwallets` it will show the wallets you are hosting
       
 * Ensure your servicenode is activated.
  
---

## Verify communication between wallets.
In order to ensure that the xbridge client is communicating with your wallets and the .conf files are setup properly, navigate to the Blocknet data dir: C:\Users\yourusername\AppData\Roaming\blocknetdx\

   * Open the "log" folder. Open up the log file with the current date/time. Ex: `xbridgep2p_20170831T181856.log`
   * Each log file will update until the client instance is close. If a new client instance is opened a new log file will be created.

As the wallet starts up, you’ll see the DX initialise using the values you entered into your `xbridge.conf` file:

![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/dxstart.PNG "Logo Title Text 1") 

 * Wait until you see “HTTP: resp 200” messages. This signifies that the wallets are communicating over RPC and setup has been successful. Ensure each wallet you are running displays a “HTTP: resp 200” and displays your labelled receive address name.
 
 ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/resp_200.PNG "Logo Title Text 1") 

 * Note: If, amidst the “HTTP: resp 200” messages, you see a message similar to `[I] 2017-Apr-19 17:48:31 [0x2],listaccounts exception couldn't connect to server`, then it is likely that at least one of your specified trading wallets have not been run.

 * Note: If you fail to get “HTTP: resp 200” messages, it’s possible that the ports assigned to wallets differ from those specified in your .conf file. To check this, open Command Prompt, type `netstat -an`, and take a look which ports are being used over localhost (127.0.0.1), or sometimes over 0.0.0.0.
 
---

## Problem Diagnosis
* To verify that each wallet is communicating with xbridge make sure the created receive addresses for each wallet is listed in the address book. If this part fails, close your wallets and review their configuration files.

* If you made changes to any .conf file you need to close and restart that wallet, including Blocknet 

* Verify the ports are actually open. You may use Command Prompt to do so by typing in `netstat -an` and reviewing the print. Check that the ports you specified in the .conf files (ex: 8332 for Bitcoin) are open over localhost (127.0.0.1).

* Ensure all .conf files are configured properly. These configurations are very case-sensitive. Any wrong data entered in them could be causing the issues.

* Check that no OS-based firewall is blocking communication. You may do this through your firewall’s interface.

* Check the xbridge log for any errors in: C:\Users\yourusername\AppData\Roaming\blocknetdx\log

* Check on general wallet events in C:\Users\yourusername\AppData\Roaming\walletname\debug.log
