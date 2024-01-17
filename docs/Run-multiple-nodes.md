# Run multiple nodes

1. The first one, You have to run a Sequencer node (Feed relay) by adding this to your node config (./config/nodeConfig.json) within the `node` field

```
    "feed": {
        "output": {
            "enable": true,
            "addr": "0.0.0.0",
            "port": 9642
        }
    }
```

2. Adjust `docker-compose.yaml` to export port 9642 on Nitro container

3. Then, run the node by `docker-compose up -d`. Now this node is your sequencer node.

4. Connect to another computer (or server) you want to run other node. Copy the `nodeConfig` file and add the below to `node` field also:

```
    "feed": {
        "input": {
            "url": "wss://<your_sequencer_url>
        }
    }
```

5. Delete those fields: `sequencer`, `delayed-sequencer`, `batch-poster`, `staker`

6. Add your sequencer's RPC to `forwarding-target` field

7. Then, run the node by `docker-compose up -d`. Now, you already run two nodes on your chain
