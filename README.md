# Pactus-Mainnet on Ubuntu 22.04
Pactus v1.0.0 

	wget https://github.com/pactus-project/pactus/releases/download/v1.0.0/pactus-cli_1.0.0_linux_amd64.tar.gz
	tar -xvzf pactus-cli_1.0.0_linux_amd64.tar.gz
	mv pactus-cli_1.0.0 pactus

New working

	cd pactus
	./pactus-daemon init

save seeds pls

You can start the node by running this command:

	./pactus-daemon start
save pass pls
 To leave the screen ctrl + C

	sudo nano /etc/systemd/system/pactusd.service
paste 

	[Unit]
	Description=pactus-Mainnet
	After=network.target
	
	[Service]
	User=root
	Group=root
	ExecStart= /root/node_pactus/./pactus-daemon start --password "<your-pass>" 
	Restart=always
	RestartSec=15
	
	[Install]
	WantedBy=multi-user.target

 
start

	sudo systemctl daemon-reload && sudo systemctl enable pactusd && sudo systemctl start pactusd
	journalctl -u pactusd -f -o cat

stop

	sudo systemctl daemon-reload && sudo systemctl disable pactusd && sudo systemctl stop pactusd
 	

Recover wallet

	./pactus-daemon init --restore "<your-mnemonic>"

 view logs

 	journalctl -u pactusd -f -o cat

useful commands

		./pactus-wallet seed
		./pactus-wallet address all
		/root/node_pactus/./pactus-wallet address balance "<your-wallet>" 
		/root/node_pactus/./pactus-wallet tx bond <Reward address>   <Validator address> <AMOUNT>
  		/root/node_pactus/./pactus-wallet tx transfer <sender address> <receiver address> <AMOUNT>
