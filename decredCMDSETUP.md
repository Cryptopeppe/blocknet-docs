# Configurare Decred CMD Line Per Blocknet DX

GRAZIE A @86b (Slack) per aver trascorso ore e ore su questa configurazione!

*Questa configurazione otterrá un resp di 200 sul blocco DX w/ un errore, questo é stato esaminato.* 

* Vai a: https://github.com/decred/decred-release/releases/tag/v1.0.5

* Scarica: `dcrinstall-windows-amd64-v1.0.5.exe`

* Esegui il .exe

* Trova la directory, dovrebbe essere: `C:\Users\<NAME>\decred\ `

---

* Apri 3 fineste cmd prompt 
  * Su tutte e 3, cambia la directory con la directory sorgente:
  
	  `cd C:\Users\<NAME>\decred` o dovunque sia installata
    
## primaa CMD PROMPT 

* Scrivi:

  * `dcrd --notls --rpcuser=CHANGE --rpcpass=CHANGE --minrelaytxfee=0.01 --rpclisten=127.0.0.1`
  	* (change rpc user/pass)

* Dovrebbe connettersi e scaricare la blockchain. Lascialo in esecuzione in background

## 2ndo CMD PROMPT WINDOW

* Type: `dcrwallet --create`

* Create and enter a password (it wont display anything when you type a password) 

* Type it again to confirm

* Type `n` on addition security

* Type: `n` on an existing wallet

* Copy your Seed and Hex into a document and save it

* Type: `OK`  (capital letters)

* Your wallet should be created successfully!

## 3RD CMD PROMPT WINDOW

* Type:

	* `dcrwallet --username=CHANGE --password=CHANGE --noclienttls --noservertls --walletpass public --dcrdusername=CHANGE --dcrdpassword=CHANGE --txfee=0.01`
		* (enter the same user/pass as the above RPC for both user/pass)

* Enter your password, it should rescan blocks and eventually connect
  
* Leave it running in the background

## BACK TO 2ND CMD PROMPT WINDOW

* Type: 

	* `dcrctl -u CHANGE -P CHANGE --wallet --notls walletpassphrase <password> 1000000`
		* (-u and -P is your user/pass from above)
		* ("password" is your wallet password, but don’t use the <> symbols)

* It should take you back to the directory

* Type: 

	* `dcrctl -u CHANGE -P CHANGE --wallet --notls createnewaccount "testDECRED"`
		* (“testDECRED” is what I am calling my labelled address, use the quotation marks and label it whatever you want)

* It should take you back to the directory

* Type:

	* `dcrctl -u CHANGE -P CHANGE --wallet --notls getnewaddress "testDECRED"`
		* (getnewaddress " " is whatever you wrote on the above command for a label)

* This should output your labelled DCR address

## XBRIDGE.conf

* Go to your xbridge.conf and add this config for DCR:

```
[DCR]
Title=Decred
Address=DCR ADDRESS
Ip=127.0.0.1
Port=9110
Username=YOUR USERNAME
Password=YOUR PASSWORD
AddressPrefix=7
ScriptPrefix=7
SecretPrefix=34
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=1000000
BlockTime=150
FeePerByte=1000
```

* Run xbridge

