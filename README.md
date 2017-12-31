# [LiveConfig](https://www.liveconfig.com/]) Let's Encrypt Cert for Backend System
This script takes from a vhost / domain the LE Cert an create the SSL Cert for the LiveConfig backend.
# The script currently only supports Debian and Apache! Not for Nginx and / or CentOS / Fedora / RHEL

## Installation
To install the script, do following command:
```bash
wget https://raw.githubusercontent.com/beli3ver/LCSSLUpdate/master/updateLCSSLCert.sh && chmod 700 updateLCSSLCert.sh
```
Then update the two main variables:
```bash
LC_DOMAIN="example.de"
LC_VHOSTS_PATH="/etc/apache2/sites-available/example.conf"
```
* **LC_DOMAIN** ==> the domain for liveconifg ==> example.de:8443
* **LC_VHOSTS_PATH** ==> the path to the vhost config for the **LC_DOMAIN**

## Usage
To run the script, do 
```bash
./updateLCSSLCert.sh
```
The last command shows the status from liveconfig. If there is an error, run this command to set all back to default:
```bash
rm /etc/liveconfig/sslcert.pem && service liveconfig restart
```

### Cron
At this time, the easiest way is to do this every every 4th hour.
Do as root
```bash
crontab -e
```
add this line:
```bash
0 */4 * * * /bin/bash /path/to/file/updateLCSSLCert.sh
```
## Todo
* [ ] MySQL SSL Setup
* [ ] Call arguments
    * [ ] --domain=exmaple.de
    * [ ] --vhost-file=/etc/apache2/sites-available/example.conf
* [ ] Support
    * [ ] nginx
    * [ ] OS: RHEL/Fedora/CentOS
