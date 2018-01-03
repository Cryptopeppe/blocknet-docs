# BLOCKNET
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/block.PNG "Logo Title Text 1")

Internet delle Blockchains

## Guida Alla Configurazione Dell'Exchange Decentralizzato Blocknet

**Queste istruzioni servono per fare trading sull'exchange decentralizzato di Blocknet** 

* Il DX di Blocknet utilizza la tecnologia router blockchain xbridgep2p™ per permettere agli utenti di scambiare tokens e assets, e di utilizzare gli smart contracts tra blockchains.

## Panoramica
La configurazione richiede un'integrazione tra il wallet Blocknet e i wallet delle monete con le quali vuoi fare trading. A questo punto, niente é automatizzato e l'UI sul nuovo wallet di Blocknet sará usata finché l'UI finale non é completa. La configurazione va effettuata manualmente creando (o modificando) i files .conf:

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

## Configurare gli Indirizzi delle Monete
In ogni wallet, crea un nuovo indirizzo ed etichettalo in modo informativo, come "indirizzo DX" (xbridge si aspetta un indirizzo in ricezione etichettato)
 
 * Per creare un nuovo indirizzo, vai all'icona del wallet "receive" e clicca "new address" 
 
 * Per etichettare un indirizzo, puoi fare doppio clic sullo stesso o cliccare il campo "etichettato" 
 
 ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/labelledaddress.PNG "Logo Title Text 1") 

 * Invia i fondi con i quali vuoi fare trading al tuo indirizzo etichettato
 
 * Ció va portato a compimento per tutti i wallet con i quali vuoi fare trading
 
---

## Configurare xbridge.conf

La tecnologia Xbridge di Blocknet é integrata nell'ultima versione del client. vedi [GitHub](https://github.com/BlocknetDX/BlockDX) per il codice sorgente
 
 * Per vedere la lista completa delle monete .conf vedi: [xbridge.conf](https://github.com/BlocknetDX/blocknet-docs/blob/master/xbridgeCONF.md)
 
 * Creare/Modificare file `xbridge.conf` e collocare la seguente configurazione nel wallet Blocknet nella directory data (per Windows) C:\Users\[yourusername]\AppData\Roaming\blocknetdx\

 * Nota: per evitare crash o scambi falliti, per favore modifica solo le funzionalitá del tuo `xbridge.conf` su tutte le moente con le quali vuoi fare trading

 * Incolla l'username e password RPC che hai creato per ogni coppia di criptovalute nel campo “Username” e “Password” 
 
 * Incolla l'indirizzo del "labelled receive address" che hai creato per ogni coppia di criptovaluta
 
 * Assicurati che il resto della configurazione combaci per ogni moneta [xbridge.conf](https://github.com/BlocknetDX/blocknet-docs/blob/master/xbridgeCONF.md) 

 * Salva il file (se hai modificato il file esistente, clicca salva, se hai creato un nuovo file clicca su file, salva come, e nel file scrivi: `xbridge.conf`
    * Assicurati che il file non sia `xbridge.conf.txt`

 * Colloca questo file nella cartella della directory data di Blocknet: "C:\Users\[yourusername]\AppData\Roaming\blocknetdx\"

 * Dovrai tornare indietro a questo passaggio se nel futuro deciderai di aggiungere altre monete, e cambiare `RPCusername` `RPCpassword` `Port` `Address` 
 
 * Non cambiare altre impostazioni nel file .conf a meno che non sia in testnet a condurre dei tests.
 
---

## Sequenza di Avvio
 * Avvia le coppie di valute con le quali stai facendo trading
    * Assicurati che ogni wallet sia completamente sincronizzato e sbloccato

 * Avvia il wallet Blocknet dopo aver avviato gli altri wallets.
     
---

## Verifica la Comunicazione tra Wallets
Al fine di assicurarti che il client xbridge stia comunicando con i tuoi wallets e i files .conf siano configurati correttamente, naviga al dir da di blockcnet: C:\Users\yourusername\AppData\Roaming\blocknetdx\

   * Apri la cartella "log". Apri il file log con ora/data correnti. Es: `xbridgep2p_20170831T181856.log`
   * Ogni file log si aggiornerá fino alla chiusura dell'istanza. Se una nuova istanza del client viene aperta un nuovo file log verrá creato.

All'avvio del wallet, vedrai il DX inizializzarsi usando i valori che hai inserito nel tuo file `xbridge.conf`:

![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/dxstart.PNG "Logo Title Text 1") 

 * Aspetta fino a vedere “HTTP: resp 200” messages. Ció significa che i wallet stanno comunicando su RPC e la configurazione é avvenuta con successo. Assicurati che ogni wallet che stai eseguendo mostri “HTTP: resp 200” e mostri il nome del tuo indirizzo in entrata etichettato.
 
 ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/resp_200.PNG "Logo Title Text 1") 

 * Nota: Se, in mezzo al messaggio “HTTP: resp 200”, vedi un messaggio simile a `[I] 2017-Apr-19 17:48:31 [0x2],listaccounts exception couldn't connect to server`, allora é probabile che uno dei tuoi wallet non stia funzionando correttamente.

 * Nota: se fallisci nel ricevere il messaggio “HTTP: resp 200”, é possibile che le porte assegnate ai wallets differiscano da quelle nel tuo file .conf. Per controllare, apri il Prompt dei Comandi, digita `netstat -an`, e dai un'occhiata a quali porte sono usate sul localhost (127.0.0.1), o a volte sopra 0.0.0.0.

--- 
 
## Piazza un Ordine
Una volta che hai confermato che i wallets stanno comunicando e la configurazione é avvenuta con successo, prosegui come segue:

* nell'icona “BlocknetDX” del wallet Blocknet, clicca sul bottone “New Transaction”. Si aprirá una nuova finestra:
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/newTX.PNG "Logo Title Text 1")   

* Clicca sull'icona “Address book”. Ció aprirá una nuova finestra che visualizza l'indirizzo che hai creato in ongi wallet coppia di criptovaluta.
   
   ![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/address_book.PNG "Logo Title Text 1")   

  * Note: 
  
    * Se non vedi questi indirizzi, significa che il tuo wallet non sta comunicando tramite RPC
    
    * Potrebbero volerci 30 secondi per connettere xbridge con i tuoi wallets, ma una volta che l'avvio é stato completato verranno mostrate le tue coppie di criptovalute

    * Non incollare manualmente un indirizzo nei campi “from” e “to”. Seleziona gli indirizzi che ti sono stati dati da xbridge dalle tue coppie di criptovalute.
      
* Sui lati "from" e "to", clicca su "Address Book" e fai doppio clic sulla criptomoneta con la quale vuoi fare trading 
    
* Il tuo indirizzo e il saldo del tuo account verrá riempito di ogni criptomoneta
   
![alt text](https://github.com/BlocknetDX/blocknet-docs/blob/master/pictures/btc_dyn_newtx.PNG "Logo Title Text 1")
    
   * In questo esempio stiamo facendo trading di Bitcoin per Dynamic
   
* Scegli la quantitá che vuoi commerciare e clicca "New Transaction"
   
* Il nuovo TX verrá pubblicato sul DX di Blocknet per qualcuno che voglia accettare.
   
![alt text](https://github.com/BlocoknetDX/blocknet-docs/blob/master/pictures/btc_dyn_posted.PNG "Logo Title Text 1")
    
   * In questo esempio TX stiamo scambiando 0.0006 BTC per 1 DYN
   
* Per accettare lo scambio, clicca lateralmente i TX pubblicati e poi clicca accetta

* per cancellare la tua pubblicazione TX, clic laterale sul tuo TX e poi clicca cancella

---

## Diagnosi dei Problemi
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
