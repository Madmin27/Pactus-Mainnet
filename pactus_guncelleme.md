Terminale gir
    
    systemctl daemon-reload &&  systemctl disable pactusd &&  systemctl stop pactusd
    wget https://github.com/pactus-project/pactus/releases/download/v1.1.8/pactus-cli_1.1.8_linux_amd64.tar.gz
    tar -xvzf pactus-cli_1.1.8_linux_amd64.tar.gz

aşağıdaki ile service dosyasına gir

    nano /etc/systemd/system/pactusd.service

içerisine aşağıdakileri gir veya versiyon numarasını değiştir

    [Unit]
    Description=pactus-Mainnet
    After=network.target
    
    [Service]
    User=root
    Group=root
    ExecStart= /root/pactus-cli_1.1.8/./pactus-daemon start -w /root/pactus --password Pac27tus* 
    Restart=always
    RestartSec=15
    
    [Install]
    WantedBy=multi-user.target

Ctrl +X ile çık
aşağıdaki komutla çalıştır
    
    systemctl daemon-reload &&  systemctl enable pactusd &&  systemctl start pactusd
