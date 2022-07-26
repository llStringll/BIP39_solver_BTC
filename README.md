# BIP39_solver_BTC
A GPU orchestraded BIP39 mnemonic solver for BTC blockchain

## bip39_solver
This project was used to iterate through all possible BIP39 mnemonics given a certain amount of known words and a target address.  It utilizes all available GPUs on the system.  This is not high quality production ready code, it was thrown together as quickly as possible.

## bip39_solver_server
This project was used to help orchestrate the distribution of work for a pool of GPU workers.  It logs work in batches as they are distributed and then updates the batch status once we a notification from the worker that it is complete.  It allows for fetching the status, updating the mnemonic, and updating the batch size.  One piece of missing functionality is to automatically serve batches that have status=0 and are older than some threshold age.  Workers would fail sometimes in the middle of a batch and without this functionality the batch would never get completed.  I ended up manually querying and starting a worker specifically to handle these failed batches but could easily be fixed in the server itself.  This is not high quality production ready code, it was thrown together as quickly as possible.
