# Pactus-Mainnet
Pactus v1.0.0-rc-0 (Release Candidate)

	wget https://github.com/pactus-project/pactus/releases/download/v1.0.0-rc-0/pactus-cli_1 
	tar -xvzf pactus-cli_1.0.0-rc-0_linux_amd64.tar.gz
	cd pactus-cli_1.0.0-rc-0

	./pactus-daemon init  -w=working1

save seeds ...

You can start the node by running this command:

	./pactus-daemon start -w /root/pactus-cli_1.0.0-rc-0/working1

See log

	cat ./pactus-cli_1.0.0-rc-0/working1/pactus.log
