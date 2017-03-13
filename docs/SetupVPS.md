# Setup for my VPS

#### Download/Erase/Upload
- Backup all your important files<br>
`scp -r your_username@remotehost.edu:~/* .`
- Set SSH Key to your account settings
- Install Debian 8 : Jessie
- Remove old entry from your hosts<br>
`ssh-keygen -R ip|hostname`
- `ssh root@ip|hostname`
- Restore all your important files<br>
`scp -r * your_username@remotehost.edu:~/`

#### Web
- `apt-get install nginx`
- `curl -sL https://deb.nodesource.com/setup_6.x -o nodesource_setup.sh`
- `bash nodesource_setup.sh`
- `apt-get install nodejs`
- `apt-get install build-essential`

#### Utilities
- `npm install pm2 -g`
- `pm2 install pm2-logrotate`
- `pm2 set pm2-logrotate:max_size 5M`
- `pm2 set pm2-logrotate:retain 10`
- Copy dump.pm2 into ~/.pm2/ for loading previous configuration

#### TeamSpeak Server
- `adduser tsserver && su tsserver && cd /home/tsserver`
- `wget http://dl.4players.de/ts/releases/3.0.11.2/teamspeak3-server_linux-amd64-3.0.11.2.tar.gz`
- `tar -xvzf teamspeak3-server_linux-amd64-3.0.11.2.tar.gz`
- `mv teamspeak3-server_linux-amd64 teamspeak3 && cd teamspeak3`
- `./ts3server_startscript.sh start`
- Save token and Id ServerAdmin
- `crontab -e`
- Add at the end `@reboot cd /home/serveur/teamspeak3 && ./ts3server_startscript.sh start`

#### Help commands
- PM2 # Start app with name test and pass option "-a 34" as argument
`pm2 start app.js --name="test" -- -a 34`