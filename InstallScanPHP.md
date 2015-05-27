# Introduction #
If you want a lightweight GUI for your scanner this is your best bet. A very lightweight GUI easily deployed on all your LAN (it's web-based) so it is very easy to acquire scans. Scanning can be easily done also outside the LAN, since any machine which access the web-server can scan - if you have your media at the scanner ;)



# Details #
  1. After you have installed a web server (any web server is good) make sure you install PHP
  1. Check if PHP is working fine by putting a file info.php in /var/www (or depends of your OS)
```
<?PHP 
         phpinfo();
?>
```
  1. Install saned on your machine :- For debian based: sudo apt-get install saned
  1. Follow details [here](http://www.sane-project.org/README.linux) on how to set up SANE
  1. Follow details [here](http://www.sane-project.org/man/saned.1.html) on how to set up SANEd
  1. Check that the configuration is working fine and using sudo do scanimage -L
  1. If it works, check that using a non-admin user can do scanimage -L. If the output is different, and says that there is no scanner installed, it means you do not have any right on the scanner
  1. Add yourself to the group scanner by doing:
```
usermod -a -G scanner your_username 
```
  1. Now you should do **scanimage -L** and have the name of your scanner outputted.
  1. Now add your webserver's username (normally _www-data_) to the scanner group
  1. Download **sane\_x\_x.tar.gz** using wget or similar
  1. Untar the downloaded file using
```
tar xzvf sane_*_*.tar.gz
```
  1. Copy the file to a folder readable and writable (/var/www-data for example) by your web server
  1. Open the file using your favourite text editor (vi/vim/nano/others) and change the config section to suit your needs
  1. Restart your web server
  1. Point your web browser to the scan.php file
  1. You should have a scanned image asking you to be saved