# BLOCKNET
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/block.PNG "Logo Title Text 1")

Internet delle Blockchains

## Guida Alla Configurazione Dell'Exchange Decentralizzato Blocknet

**Queste istruzioni servono per fare trading sull'exchange decentralizzato di Blocknet** 

* Il DX di Blocknet utilizza la tecnologia router blockchain xbridgep2p™ per permettere agli utenti di scambiare tokens e assets, e di utilizzare gli smart contracts tra blockchains.

## Panoramica
Il setup richiede un'integrazione tra il wallet Blocknet e i wallet delle moente con le quali vuoi fare trading. A questo punto, niente é automatizzato e l'UI sul nuovo wallet di Blocknet sará usata finché l'UI finale non é completa. La configurazione va effettuata manualmente creando (o modificando) i files .conf:

 * xbridge.conf

 * Il file di configurazione di ogni moneta con la quale vuoi fare trading

L'integrazione avviene attraverso le API del wallet RPC. Per ragioni di sicurezza raccomandiamo di eseguire tutti i wallet in un singolo box e comunicare sul localhost (127.0.0.1), sebbene i wallet possono essere anche eseguiti su differenti macchine ed essere connessi tramite indirizzo IP. La documentazione generale sulle funzionalitá JSON RPC é disponibile a https://en.bitcoin.it/wiki/Running_Bitcoin.


## Video Tutorial Blocknet DX Exchange
 * [DX Exchange Tutorial](https://www.youtube.com/watch?v=DlYbDzG_l5w)


## Requisiti

* Versione piú recente del client installata, criptata, completamente sincronizzata. [GitHub Releases](https://github.com/BlocknetDX/BlockDX/releases)

* Versione piú recente del wallet di ogni cryptovaluta con la quale vuoi fare trading (completamente sincronizzato, criptato)

     * Le cryptovalute con quali vuoi fare trading devono essere inviate a ogni indirizzo specifico etichettato 

* Aver configurato adeguatamente ogni files .conf per ogni wallet

---

## Configurazione Files .conf Files Per i Wallets di Trading
Il wallet di ogni moneta con la quale vuoi fare trading deve essere configurato con un usarname/password e un permesso dall'IP, se stai usando soltanto una macchina locale usa l'IP:127.0.0.1

 * Per vedere la lista completa di tutte le configurazioni compatibili con il wallet vai a: [Configurazioni Wallet](https://github.com/BlocknetDX/blocknet-docs/blob/master/walletsCONF.md)

 * Scarica l'ultima versione del wallet, lascialo sincronizzare completamente, poi chiudi il wallet

 * Clicca il bottone START sul tuo desktop, dove dice "Ricerca programmi e files" scrivi “%appdata%” e la directory roaming dovrebbe saltar fuori. Clicca su "Roaming o clicca invio
 
 * Trova la cartella del tuo wallet nella directory data, es: Bitcoin
 
 * Se non hai un file .conf avviato devi aprire Notepad e crearne uno.

 * Naviga a [Configurazioni Wallet](https://github.com/BlocknetDX/blocknet-docs/blob/master/walletsCONF.md) e copia/incolla le informazioni di configurazione per il wallet che stai eseguendo. (Ció puó essere aggiunto a quanto giá presente nel file che hai "addnodes" o un'altra configurazione:
 
   * Es: bitcoin.conf
   
   ```
   server=1
   listen=1
   rpcuser=yourusername
   rpcpassword=yourpassword
   rpcallowip=127.0.0.1
   ```
   
   * Assicurati che la configurazione sia corretta. Non aspettarti che le configurazioni siano le stesse per ogni wallet.

 * Cambia `rpcuser` e `rpcpassword` in qualcosa di unico per te. Per ragioni di sicurezza dovresti avere un username RPC username e password differenti per ogni wallet

 * Se stai usando una singola macchina usa l'IP: `127.0.0.1`

 * Quando hai finito, clicca File, Salva come, Scrivi: `bitcoin.conf`
    * Assicurati che il file non sia `bitcoin.conf.txt`

 * Salvalo e poi colloca il file .conf nella cartella del wallet corrispondente
    * Per questo esempio: %Appdata%/Roaming/Bitcoin 

 * Ricorda cosa hai scritto per username, password, e IP

 * Creare i files .conf per ogni wallet che utilizzerai sull'exchange decentralizzato.
    * Assicurati che `rpcuser` e `rpcpassword` siano differenti in ongi wallet per ragioni di sicurezza
 
---

## Configurare gli Indirizzo delle Monete
In ogni wallet, crea un nuovo indirizzo ed etichettalo in modo informativo, come "indirizzo DX" (xbridge si aspetta un indirizzo in ricezione etichettato)
 
 * Per creare un nuovo indirizzo, vai all'icona del wallet "receive" e clicca "new address" 
 
 * Per etichettare un indirizzo, puoi fare doppio clic sullo stesso o cliccare il campo "etichettato" 
 
 ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/labelledaddress.PNG "Logo Title Text 1") 

 * Invia i fondi con i quali vuoi fare trading al tuo indirizzo etichettato
 
 * Ció va portato a compimento per tutti i wallet con i quali vuoi fare trading
 
---

## Setup xbridge.conf

The Blocknet’s Xbridge technology is integrated into the latest client release. See [GitHub](https://github.com/BlocknetDX/BlockDX) for the source code.

 * To see the full list of coin .conf's see: [xbridge.conf](https://github.com/BlocknetDX/blocknet-docs/blob/master/xbridgeCONF.md)

 * Create/edit an `xbridge.conf` file and place the following configuration file in the blocknet wallet data directory (for Windows) C:\Users\[yourusername]\AppData\Roaming\blocknetdx\

 * Note: to avoid crashes or failed trades, please edit your `xbridge.conf` to feature only and all the coins you wish to trade with

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
 * Start the currency pair(s) you are trading with
    * Ensure every wallet is fully sync'd and unlocked

 * Start the Blocknet wallet after starting the other wallets.
     
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
 
## Place an Order
Once you’ve confirmed that the wallets are communicating and setup has been successful, do the following:

* In the “BlocknetDX” tab of the Blocknet wallet, click on the “New Transaction” button. A new window will open:
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/newTX.PNG "Logo Title Text 1")   

* Click on the “Address book” icon. This opens up a new window that displays the addresses you created in each currency pair wallet.
   
   ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/address_book.PNG "Logo Title Text 1")   

  * Notes: 
  
    * If you do not see these addresses, it means that your wallets are not communicating over RPC
    
    * It may take up to about 30 seconds for xbridge to connect with your wallets, but once startup has completed it will populate your currency pair addresses

    * Do not manually paste an address into the “from” and “to” fields. Select addresses that xbridge has been given by your currency pair wallets.
      
* On the "from" and "to" sides, click the "Address Book" and double-click the currency's you want to trade
    
* Your address and account balance will populate for each currency
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/btc_dyn_newtx.PNG "Logo Title Text 1")
    
   * In this example we are trading Bitcoin for Dynamic
   
* Choose the amount you wish to trade for and click "New Transaction"
   
* The new TX will then be posted to the Blocknet DX for someone to accept.
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/btc_dyn_posted.PNG "Logo Title Text 1")
    
   * In this example TX we are trading 0.0006 BTC for 1 DYN
   
* To accept a trade, side click the posted TX and click accept

* To cancel your TX post, side click your TX and click cancel

---

## Problem Diagnosis
* To verify that each wallet is communicating with xbridge make sure the created receive addresses for each wallet is listed in the address book. If this part fails, close your wallets and review their configuration files.

* Ensure you have sent the funds you wish to trade with to the labelled address. Ensure these are confirmed.

* If you made changes to any .conf file you need to close and restart that wallet, including Blocknet 

* Verify the ports are actually open. You may use Command Prompt to do so by typing in `netstat -an` and reviewing the print. Check that the ports you specified in the .conf files (ex: 8332 for Bitcoin) are open over localhost (127.0.0.1).

* Ensure all .conf files are configured properly. These configurations are very case-sensitive. Any wrong data entered in them could be causing the issues.

* Check that no OS-based firewall is blocking communication. You may do this through your firewall’s interface.

* Check the xbridge log for any errors in: C:\Users\yourusername\AppData\Roaming\blocknetdx\log

* Check on general wallet events in C:\Users\yourusername\AppData\Roaming\walletname\debug.log

---

## Security Tips
(With thanks to threepwood)

Since our technology essentially makes you your own exchange, here are some tips on how to keep your money safe.

   * The Blocknet’s team will never ask for your private keys or coins. Do not get fooled by impersonators.
Exchanges

   * Always move your coins from exchange to your private wallet.

   * Use long and random password.

   * Set up 2FA on logins and any withdrawals.

   * Disable password recovery via SMS/phone service. Disable all password recovery options for maximum security.

   * Recovery passwords are fine but keep them printed and offline.

   * Make sure your stored emails do not contain any extra information such as passwords or social security numbers.

   * Use different email addresses where possible. This limits the ability for hackers to run their automated "Forgot my password" links. 
   
   * Online Activity / Personal Information Disclosure. Do not promote your coin count etc online.

   * Limit your online public persona. This can attract unwanted attention which can make you a target.

   * Disable any online accounts you no longer use.

   * Assume hacking groups are building up social profiles on yourself. Your interests, time you are usually online, who you interact with.

   * Hacking groups use automated scripts so if those resources are exhausted they will try to social engineer your contacts.

   * Hacking groups are experts at social engineering. They have done this thousands of times.

   * Do not open random links and files provided in Slack, etc.

   * Do not fall for sob stories (Boohoo I lost all my coins) without proper due diligence.

   * Take multiple backups of your private keys regularly.

   * Verify backup by importing keys to the client.

   * Store your backups in M-DISC or in paper format.

   * Use dedicated wallet / staking PC and make it your safe haven. DO NOT USE IT FOR ANY OTHER ONLINE ACTIVITIES.

   * Encrypt your hard drives.

   * Use open source where possible.

   * Keep your software updated.

   * Do not install software from unknown 3rd party actors.

   * Use network level segmentation and mitigate attack surface against your wallet PC.
