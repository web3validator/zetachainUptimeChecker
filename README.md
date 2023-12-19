# Zetachain Uptime Checker bot

Web3 Validator team has developed the checker bot that can monitor your node uptime. We can implement it on various Cosmos SDK networks and will gladly add it to Zetachain mainnet network as soons as it will alive!

To run the bot, you need to do three things:

1) Start Redis
2) Install the necessary libraries
3) Make changes to the configuration
4) Run it through the service

**Running Redis via Docker**
```
sudo docker pull redis
sudo docker run --name my-redis-container --restart=always -p 6379:6379 -d redis --requirepass <your_password>

```

**(You must have Python version 10 or higher).**

**Install the necessary libraries**
```
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

**Make changes to the configuration**
```
nano .env.exemple .env
nano .env
```
You should change everything according to your own parameters.

**Run it through the service**
```
nano /etc/systemd/system/zetachain_bot.service
```
```
[Unit]
Description=Humans bot
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/path/to/web3validator-zetachain_Uptime_Checker_bot
ExecStart=/path/to/web3validator-zetachain_Uptime_Checker_bot/venv/bin/python bot.py
Restart=on-failure
RestartSec=10
LimitNOFILE=65535

[Install]
WantedBy=multi-user.target
```

Start service
```
systemctl enable zetachain_bot
systemctl start zetachain_bot
```

## Functionality

It's just super convenient:

*Without installing any software (grafana, tenderduty, prometheus or etc.)

*That bot not only warns that the validator is already in jail but pings you when your validator starts skipping blocks to keep you out of jail

*Сan tell you about the time left before being sent to jail.

*Clear and pleasant interface and validator status check. Also this bot can be customizable and it may add many other functions. We already implement it in many known cosmos-networks.

*Auto-reporting bug/errors mechanism

### how to add checker to your validator:
Start your bot in your telegram account [https://t.me/ZetaChainUpTime_bot](https://t.me/ZetaChainUpTime_bot)

Then you can add validator checker through create checker button. 
 - This will make the bot check your validator for missing blocks. 

You can show your validator checker through list checker command.
You can delete your validator checker through delete checker command.

<img width="390" alt="image" src="https://github.com/web3validator/zetachainUptimeChecker/assets/59205554/89a8d7c8-6889-4cb5-8511-da4672eb4a66">

enter your validator moniker 

<img width="404" alt="image" src="https://github.com/web3validator/zetachainUptimeChecker/assets/59205554/c5fba4d7-5629-4cd9-93cd-258afda9b04a">

you will se this massage : 

<img width="410" alt="image" src="https://github.com/web3validator/zetachainUptimeChecker/assets/59205554/4302d6b0-ced1-417c-8cac-73532f098e6c">
<img width="379" alt="image" src="https://github.com/web3validator/zetachainUptimeChecker/assets/59205554/b9a5e537-c9c8-412e-85f0-c34eb96955d3">


If you will start skip the blocks , bot will ping ypu every 5 minutes 

<img width="427" alt="image" src="https://github.com/web3validator/zetachainUptimeChecker/assets/59205554/b6b87070-f2e3-4f9f-a885-e9c33254efc1">

