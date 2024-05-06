# Pactus-Mainnet on Ubuntu 22.04
Pactus v1.1.4 

	wget https://github.com/pactus-project/pactus/releases/download/v1.1.4/pactus-cli_1.1.4_linux_amd64.tar.gz
	tar -xvzf pactus-cli_1.1.4_linux_amd64.tar.gz
	mv pactus-cli_1.1.4 pactus
İlk Çalıştırma

	cd pactus
	./pactus-daemon init

Kelimeleri kaydet, onlar senin cüzdan kelimelerin

Aşağıdaki komutla çalıştırıp logları görelim. Biraz çalıştıktan sonra kapat

	./pactus-daemon start
 
parola gir ve unutma / save pass pls
Çıkış ctrl + C

Şimdi aşağıdaki komutları bir defada gir pactus service oluşsun

	sudo tee /etc/systemd/system/pactusd.service > /dev/null <<EOF
	[Unit]
	Description=pactus-Mainnet
	After=network.target
	
	[Service]
	User=root
	Group=root
	ExecStart= /root/pactus-cli_1.1.4/./pactus-daemon start -w /root/pactus --password Pac27tus*
	Restart=always
	RestartSec=15
	
	[Install]
	WantedBy=multi-user.target
	EOF


 
başlatma

	sudo systemctl daemon-reload && sudo systemctl enable pactusd && sudo systemctl start pactusd
	journalctl -u pactusd -f -o cat

durdurma

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
