[![dockeri.co](http://dockeri.co/image/blizarazu/burstcoin)](https://registry.hub.docker.com/blizarazu/burstcoin/)

Docker image of the Burstcoin wallet.
https://github.com/burst-team/burstcoin

# Start Burstcoin
Start Burstcoin with dafault settings:

```console
$ docker run -p 8125:8125 -p 8123:8123 --name burstcoin blizarazu/burstcoin
```

# Configuration and data storage
- Create a `conf` directory and place your [nxt-default.properties](https://raw.githubusercontent.com/burst-team/burstcoin/master/conf/nxt-default.properties) and [logging-default.properties](https://raw.githubusercontent.com/burst-team/burstcoin/master/conf/logging-default.properties) files in it. If you want to accept request from all network interfaces set `nxt.apiServerHost` and `nxt.uiServerHost` to `0.0.0.0` and, `nxt.allowedBotHosts` and `nxt.allowedUserHosts` to `*`:
```
nxt.allowedBotHosts=*
nxt.apiServerHost=0.0.0.0
nxt.allowedUserHosts=*
nxt.uiServerHost=0.0.0.0
```

- Create a `burst_db` directory to persist the downloaded blockchain.

Mount the directories inside the conainer when you run the container.

```console
$ docker run -p 8125:8125 -p 8123:8123 -v /my/conf:/usr/src/burstcoin/conf -v /my/burst_db:/usr/src/burstcoin/burst_db --name burstcoin blizarazu/burstcoin
```

You can access the Wallet by opening http://localhost:8125 in your browser.
