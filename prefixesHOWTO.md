# Come Trovare Le Istruzioni Prefix .CONF 

1. Indirizzo Prefix:

    1. Vai a: http://lenschulwitz.com/base58
    2. Inserisci l'indirizzo del wallet nel decodificatore in base 58
    3. Prime 2 cifre della copia HEX in: http://www.binaryhexconverter.com/hex-to-decimal-converter
    4. Valore Decimale = Indirizzo prefix

2. Script Prefix:

    1. Vai alla console del wallet
    2. Scrivi `validateaddress <wallet address>`
    3. Copia `pubkey`
    4. Se dice qualcosa sul wallet bloccato vai a `walletpassphrase <walletpassword> <pick a number in seconds>` esempio: `walletpassphrase password 10000`
    5. Scrivi `decodescript <enter copied pubkey from step iii>`
    6. Prendi l'output p2sh e decodificalo su HEX sul website base58 
    7. Poi converti le prime 2 cifre di HEX. Valore decimale = script prefix

3. Prefix Segreto:

    1. Vai alla console del wallet
    2. Scrivi `dumpprivkey <wallet address>`
    3. Copia la `privkey` 
    4. Decodifica la privkey in HEX sul sitoweb base58 
    5. Poi converti le prime 2 cifre di HEX. Valore decimale = prefix segreto

4.  RPC Port:

    1. Search wallet’s GitHub, official webpage, bitcointalk, general google searches
    2. Try some of the website sources listed below on the next page
    3. Under the wallets Debug or Tool menu, click the Peers tab. The IP address port is sometimes 1 below what is listed. This only works sometimes.
    4. From command line (windows: `netstat -an` / linux: `netstat -anp`) That should show open ports (on windows it wont’ show the process, but there is a GUI that does)

Thanks @86b (Slack) for figuring this method out
