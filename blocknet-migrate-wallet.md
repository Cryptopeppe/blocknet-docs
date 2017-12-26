## Passi per migrare dalla vecchia chain alla nuova chain
- Fare il backup del file wallet.dat prima di fare qualsiasi altra cosa (farne 2 copie separate)
- Per Windows, il file wallet.dat puó essere trovato in C:\Users\User\AppData\Roaming\blocknet (o nelle nuove versioni di \BlocknetDX)
- Per OSX, il file wallet.dat puó essere trovato in ~/Library/Application Support/blocknet (o nelle nuove versioni di /BlocknetDX)
- Sblocca completamente il wallet (non solo per lo staking) dalla UI (nel menu principale, "Settings" > "Unlock Wallet")
- Usa la console per il debug (nel menu principale, "Tools" > "Debug Console") e scrivi ```dumpwallet filename.txt``` (rimpiazza "filename.txt" con un nome di tua scelta)
- Il file sará collocato nella directory dalla quale hai lanciato il wallet 

## Scarica un nuovo wallet
- Lancia il wallet
- Usa la console per il debug e scrivi ```importwallet filename.txt``` (rimpiazza filename.txt con il nome del file usato nel comdando dumpwallet sopra)
- Verifica i vecchi indirizzi che sono stati importati dalla consele debug scrivendo ``` listreceivedbyaddress 0 true```

## When to move your wallet.dat and start using the new wallet
- Any time there is a chain fork you will need to move your wallet.dat file
- If a specific wallet version is needed for a fork, may download the new wallet, sync up, and move your wallet.dat to it's directory prior to the fork
- However, the new wallet's balance will remain zero until the migration(fork)
- A snapshot will be taken at the time of the final block on the old chain
- Once the snapshot is applied to the new chain, your balance will reflect in the new wallet
- It can be expected that (centralized) exchanges will re-enable trading once they have confirmed that the new chain is functioning as expected.

## Trouble syncing the new chain
- Close the wallet
- Backup the wallet.dat file before doing anything (make 2 separate copies)
- Backup the blocknetdx.conf file if running a service node (make 2 separate copies)
- Open the wallet and let the chain sync
- Replace the created wallet.dat anf blocknetdx.conf file with the backed-up copy
