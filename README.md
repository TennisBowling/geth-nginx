# geth-nginx
A reverse proxy for geth's rpc endpoint. 

## Requirements
```nginx``` \ 
```geth``` \ 
port ```80``` or ```443```(OPTIONAL: FOR SSL) open. \

## Installation
Run geth with the ```--http``` flag. Wait for this to sync. This could take a long time and upwards of a day. \
Replace ```default``` in ```/etc/nginx/sites-available/``` with ```nginx-config```. \
Edit ```nginx-config``` with ```sudo nano /etc/nginx/sites-available/nginx-config``` or ```sudo nano /etc/nginx/sites-available/default```. \
Add the ip/url you are going to access the website from after ```server_name```. \
Also replace IP (after ```ALLOW```) with the IP that you are allowing to connect to the rpc endpoint. Make a new line with the same format for every new ip. \
Add ```403.html``` into ```/var/www/html/``` \
Run ```sudo systemctl restart nginx.service``` \

## Connecting With MetaMask
1. Inside of MetaMask, click the toggle that by default says "Ethereum Mainnet". \
2. Then select "Custom RPC". \
3. Set the name to whatever you like. \
4. Set the "New RPC URL", set it to ```http://<THEIPOFYOURSERVER>``` (We will go into using HTTPS in the next section). \
5.  Set "Chain ID" to 1.
The rest is optional and not required, MetaMask will work just the same if you do not enter anything.\ 
Enjoy!

##SSL support
**WILL NOT WORK IF YOU DO NOT HAVE A DOMAIN**
Install ```certbot``` with ```sudo apt-get install certbot python3-certbot-nginx -y``` \
Run ```sudo certbot --nginx``` and follow the prompts

