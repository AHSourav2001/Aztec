✅ Step 1: Create a restart script

Create a script file:
```
nano ~/aztec-runner.sh
```
Paste this:
```
#!/bin/bash

while true; do
  aztec start --node --archiver --sequencer \
    --network alpha-testnet \
    --l1-rpc-urls rpc \
    --l1-consensus-host-urls Beacon_RPC \
    --sequencer.validatorPrivateKey PrivateKey \
    --sequencer.coinbase walletadress \
    --p2p.p2pIp vpsIP \
    --p2p.maxTxPoolSize 1000000000

  echo "Aztec node crashed. Restarting in 5 seconds..."
  sleep 5
done
```
Save and exit.

Make it executable:

```
chmod +x ~/aztec-runner.sh
```

✅ Step 2: Run it in a screen session

```
screen -S aztec
```

Then inside the screen:

```
~/aztec-runner.sh
```

This will now keep running the Aztec node and restart it automatically if it crashes.
