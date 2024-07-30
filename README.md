# In-Cloud Dashboard

This is just a better looking fork of [Heliactyl](https://github.com/openHeliactyl/heliactyl)

# Installation (No cloudflare tunnels)

1. Install all needed packages
```
apt install git wget
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install node
```
2. Clone this repo
```
git clone https://github.com/sexmastercc/incloud-dash.git
```
3. Install and run
**If your going to use cloudflare tunnels ignore node .**
```
npm install
node .
```

# Cloudflare tunnels
1. Install cloudflare tunnels
```
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
```
2. Setting it up
```
cloudflared login
```
**You will need to connect a domain**
```
cloudflared tunnel create (name)
```
**After it creates it will give you a UUID keep your UUID in mind**
```
cd ~/.cloudflared
apt install nano
nano config.yml
```
3. Configs
**Put this in the config.yml file**
```
url: http://localhost:(port)
tunnel: <UUID>
credentials-file: /root/.cloudflared/.json
```
**Connect a domain**
```
cloudflared tunnel route dns (UUID) (Domain)
```
**Install pm2**
```
cd (your incloud-dash folder)
npm install pm2 -g
```
4. Start
```
pm2 start index.js
cd ~/.cloudflared
cloudflared tunnel run (UUID)
```



