# Pactus-Mainnet on Ubuntu 22.04
Pactus v1.0.0-rc-0 (Release Candidate)

	wget https://github.com/pactus-project/pactus/releases/download/v1.0.0/pactus-cli_1.0.0_linux_amd64.tar.gz
	tar -xvzf pactus-cli_1.0.0_linux_amd64.tar.gz
	cd pactus-cli_1.0.0
 
New working

	./pactus-daemon init  -w=working1

save seeds pls

You can start the node by running this command:

	./pactus-daemon start -w /root/pactus-cli_1.0.0/working1
 To leave the screen ctrl + C

	sudo nano /etc/systemd/system/pactusd.service
paste 

 	[Unit]
	Description=pactus-Mainnet
	After=network.target
	
	[Service]
	User=root
	Group=root
	ExecStart= /root/pactus-cli_1.0.0/./pactus-daemon start -w /root/pactus-cli_1.0.0/working1 --password <your-wallet-pass> 
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

