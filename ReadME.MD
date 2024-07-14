curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | sudo gpg --dearmor -o /usr/share/keyrings/microsoft-prod.gpg

curl https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc

curl -fsSL https://packages.microsoft.com/config/ubuntu/22.04/mssql-server-2022.list | sudo tee /etc/apt/sources.list.d/mssql-server-2022.list

:: Need to download & install libldap-2.5

curl -OL http://archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.5-0_2.5.18+dfsg-0ubuntu0.22.04.1_amd64.deb

sudo apt-get install ./libldap-2.5-0_2.5.18+dfsg-0ubuntu0.22.04.1_amd64.deb

sudo apt-get update

sudo apt-get install -y mssql-server

sudo /opt/mssql/bin/mssql-conf setup		####!

systemctl status mssql-server --no-pager

sudo ufw allow 1433/tcp

sudo ufw enable

sudo ufw status

