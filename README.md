# free-ssl
This script will help you to generate a trusted SSL certificate issued by [Let's Encrypt](letsencrypt.org) using [certbot](https://github.com/certbot/certbot).<br>

## Prerequisites
In order to complete this script, you will need:
* Have a working [Shift](docs.shiftnrg.net) instance
* Your own domain. You can get a free one for one year at [dot.tk](dot.tk)
	* Your domain will look something like this --> `subdomain.domain.tk`
* An [A Record](https://my.freenom.com/knowledgebase.php?action=displayarticle&id=4) that points your domain to the public IP address of your server
* To know your network interface
	* Run `ifconfig` and write it down (normally it is eth0, eth1, eth2, ens1, ens2, ens3...) <br>

## Install trusted SSL certificate issued by Let's Encrypt
First of all you'll need to clone this repository:
```
cd ~
git clone https://github.com/nytrobound/free-ssl.git
cd free-ssl
```
To generate and install the trusted SSL certificate, run: `bash installssl.sh`<br>
The script will guide you through the installation process.<br>
You can find the logs at: **~/free-ssl/logs/installssl.log**

#### Renew letsencrypt certificate
After running `installssl.sh`, it will give a line that you should add to your cronjobs. You can do this by typing `cronjob -e`. After adding, it will automatically check the expiring date of your certificate and renew it, if needed.<br>
It is recommended to use https://www.crontab-generator.org/ to help you with your cronjob.<br>
Example: `* 12 * * WED bash /home/$SSLUSER/free-ssl/start_renew.sh >> /home/$SSLUSER/free-ssl/logs/cron.log`<br>
`renewssl.sh` will only renew your certificate, if the expiration date is less than 30 days.<br>
To see the result of the script go to: **~/free-ssl/logs/renewssl.log**<br>

## Links
Documentation: https://certbot.eff.org/docs <br>
Software project: https://github.com/certbot/certbot <br>
Notes for developers: https://certbot.eff.org/docs/contributing.html <br>
Main Website: https://certbot.eff.org <br>
Let's Encrypt Website: https://letsencrypt.org <br>
Community: https://community.letsencrypt.org <br>
ACME spec: http://ietf-wg-acme.github.io/acme/ <br>
ACME working area in github: https://github.com/ietf-wg-acme/acme <br>
