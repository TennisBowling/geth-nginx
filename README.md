# geth-nginx
A reverse proxy for geth's rpc endpoint. 

## Requirements
```nginx```  
```geth```  
port ```80``` or ```443```(OPTIONAL: FOR SSL) open.  

## Installation
Run geth with the ```--http``` and `--http.vhosts="*"` flags. Wait for this to sync. This could take a long time and upwards of a day.  
Replace ```default``` in ```/etc/nginx/sites-available/``` with ```nginx-config```.  
Edit ```nginx-config``` with ```sudo nano /etc/nginx/sites-available/nginx-config``` or ```sudo nano /etc/nginx/sites-available/default```.  
Add the ip/url you are going to access the website from after ```server_name```.  
Add ```403.html``` into ```/var/www/html/```  
Run ```sudo systemctl restart nginx.service```  

## Connecting With MetaMask
1. Inside of MetaMask, click the toggle that by default says "Ethereum Mainnet".  
2. Then select "Custom RPC".  
3. Set the name to whatever you like.  
4. Set the "New RPC URL", set it to ```http://<THEIPOFYOURSERVER>``` (We will go into using HTTPS in the next section).  
5.  Set "Chain ID" to 1.  
The rest is optional and not required, MetaMask will work just the same if you do not enter anything.  
Enjoy!  

## SSL support  
**WILL NOT WORK IF YOU DO NOT HAVE A DOMAIN**  
Install ```certbot``` with ```sudo apt-get install certbot python3-certbot-nginx -y```  
Run ```sudo certbot --nginx``` and follow the prompts  
Change the RPC in MetaMask from ```http://<THEIPOFYOURSERVER>``` to ```https://<THEIPOFYOURSERVER>```.  
To do this  
 1. Click on your account icon  
 2. Click on settings  
 3. Scroll down to Networks  
 4. Click on the network you made earlier, changing the url from ```http://<THEIPOFYOURSERVER>``` to ```https://<THEIPOFYOURSERVER>```.
