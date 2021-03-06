# xbridge.conf

* Sotto l'intestazione ```[Main]```, modifica quanto segue per soddisfare le tue esigenze: 

  * ```ExchangeWallets=``` aggiungi/rimuovi l'intestazione della moneta qui ( aggiungi solamente la moneta che desideri ospitare o tradare sul tuo nodo di servizio)
  * ```LogPath=``` Cambia il percorso del file ad una destinazione desiderata  

* Sotto ogni intestazione ```[COIN]```, modifica quanto segue per soddisfare le configurazione RPC del tuo wallet: 

  * ```Address=```  Modifica questo campo per abbinare il tuo indirizzo di ricezione etichettato
  * ```Username=``` Modifica questo campo per abbinare il RPCuser alla .conf della moneta
  * ```Password=``` Modifica questo campo per abbinare la RPCpassword alla .conf della moneta
  
  * https://github.com/BlocknetDX/blocknet-docs/blob/master/walletsCONF.md

* Questo xbridge.conf master contine tutte le correnti monete tradate con successo sulla Blocknet DX. Se una futura moneta passa per la fase di testing e viene scambiata con successo, sará di conseguenza annunciata. Dopo l'annuncio quei parametri di configurazione saranno rilasciati su questo documento.

```
[Main]
ExchangeWallets=BTC,SYS,LTC,DASH,DGB,DYN,DOGE,PIVX,VIA,VTC,MUE,NMC,QTUM,LBC,MONA,BLOCK,FAIR
FullLog=true
LogPath=
ExchangeTax=300

[BTC]
Title=Bitcoin
Address=
Ip=127.0.0.1
Port=8332
Username=
Password=
AddressPrefix=0
ScriptPrefix=5
SecretPrefix=128
COIN=100000000
MinimumAmount=0
TxVersion=2
DustAmount=0
CreateTxMethod=BTC
MinTxFee=0
BlockTime=600
GetNewKeySupported=false
ImportWithNoScanSupported=false
FeePerByte=105
Confirmations=0

[SYS]
Title=Syscoin
Address=
Ip=127.0.0.1
Port=8370
Username=
Password=
AddressPrefix=0
ScriptPrefix=5
SecretPrefix=128
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
MinTxFee=0
BlockTime=60
GetNewKeySupported=false
ImportWithNoScanSupported=false
FeePerByte=210
Confirmations=0

[LTC]
Title=Litecoin
Address=
Ip=127.0.0.1
Port=9332
Username=
Password=
AddressPrefix=48
ScriptPrefix=5
SecretPrefix=176
COIN=100000000
MinimumAmount=0
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
FeePerByte=200
MinTxFee=0
TxVersion=1
BlockTime=60
Confirmations=0

[DASH]
Title=Dash
Address=
Ip=127.0.0.1
Port=9998
Username=
Password=
AddressPrefix=76
ScriptPrefix=16
SecretPrefix=204
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=150
FeePerByte=200
Confirmations=0

[DGB]
Title=Digibyte
Address=
Ip=127.0.0.1
Port=14022
Username=
Password=
AddressPrefix=30
ScriptPrefix=5
SecretPrefix=128
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=60
FeePerByte=200
Confirmations=0

[DYN]
Title=Dynamic
Address=
Ip=127.0.0.1
Port=33350
Username=
Password=
AddressPrefix=30
ScriptPrefix=10
SecretPrefix=140
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=false
MinTxFee=0
BlockTime=128
FeePerByte=25
Confirmations=0

[DOGE]
Title=Dogecoin
Address=
Ip=127.0.0.1
Port=22555
Username=
Password=
AddressPrefix=30
ScriptPrefix=22
SecretPrefix=158
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=60
FeePerByte=500000
Confirmations=0

[PIVX]
Title=Pivx
Address=
Ip=127.0.0.1
Port=51473
Username=
Password=
AddressPrefix=30
ScriptPrefix=13
SecretPrefix=212
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=60
FeePerByte=110
Confirmations=0

[VIA]
Title=Viacoin
Address=
Ip=127.0.0.1
Port=5222
Username=
Password=
AddressPrefix=71
ScriptPrefix=33
SecretPrefix=199
COIN=100000000
MinimumAmount=0
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=false
FeePerByte=200
MinTxFee=0
TxVersion=1
BlockTime=24
Confirmations=0

[VTC]
Title=Vertcoin
Address=
Ip=127.0.0.1
Port=5888
Username=
Password=
AddressPrefix=71
ScriptPrefix=5
SecretPrefix=199
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=false
MinTxFee=0
BlockTime=150
FeePerByte=110
Confirmations=0

[MUE]
Title=MonetaryUnit
Address=
Ip=127.0.0.1
Port=29683
Username=
Password=
AddressPrefix=16
ScriptPrefix=76
SecretPrefix=126
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=40
FeePerByte=25
Confirmations=0

[NMC]
Title=Namecoin
Address=
Ip=127.0.0.1
Port=8336
Username=
Password=
AddressPrefix=52
ScriptPrefix=13
SecretPrefix=180
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=600
FeePerByte=115
Confirmations=0

[QTUM]
Title=Qtum
Address=
Ip=127.0.0.1
Port=3889
Username=
Password=
AddressPrefix=58
ScriptPrefix=50
SecretPrefix=128
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=150
FeePerByte=450
Confirmations=0

[LBC]
Title=LBRY Credits
Address=
Ip=127.0.0.1
Port=9245
Username=
Password=
AddressPrefix=85
ScriptPrefix=122
SecretPrefix=28
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=150
FeePerByte=60
Confirmations=0

[MONA]
Title=Monacoin
Address=
Ip=127.0.0.1
Port=9402
Username=
Password=
AddressPrefix=50
ScriptPrefix=55
SecretPrefix=176
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=false
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=90
FeePerByte=200
Confirmations=0

[BLOCK]
Title=Blocknet
Address=
Ip=127.0.0.1
Port=41490
Username=
Password=
AddressPrefix=26
ScriptPrefix=28
SecretPrefix=154
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=true
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=60
FeePerByte=20
Confirmations=0

[FAIR]
Title=Faircoin
Address=
Ip=127.0.0.1
Port=40405
Username=
Password=
AddressPrefix=95
ScriptPrefix=36
SecretPrefix=223
COIN=100000000
MinimumAmount=0
TxVersion=1
DustAmount=0
CreateTxMethod=BTC
GetNewKeySupported=true
ImportWithNoScanSupported=true
MinTxFee=0
BlockTime=210
FeePerByte=1000
Confirmations=0

[RPC]
Enable=false
UserName=rpc1
Password=rpc1
UseSSL=false
Port=8080
```
