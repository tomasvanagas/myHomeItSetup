# Nextcloud setup

Server operating system: Ubuntu 18.04 LTS  
Web server: nginx  

# Nextcloud custom apps
For additional functionality I need some apps which can be downloaded directly from nextcloud app store:  

## Splash
Displays custom images on your background and login screen.

## Impersonate
Useful to help users setup their accounts so you can login as them.

## Metadata
Show image metadata, so you can crosscheck if photos are in right folders.

## Preview Generator
This one takes little more effort to setup, but greatly increases performance loading photos from nextcloud app or browser.

### Instalation:
Step 1: Running initial preview generation
Run these commands:
```bash
sudo chmod +x /var/www/nextcloud/occ
sudo -u www-data /var/www/nextcloud/occ preview:generate-all -vvv
```

Step 2: Automating repetitive future preview generation jobs with cron
Open cron of web server user:
```bash
sudo -u www-data crontab -e
```
Add this line at the end of text file:
```bash
  0  3  *  *  * /var/www/nextcloud/occ preview:pre-generate 
```
