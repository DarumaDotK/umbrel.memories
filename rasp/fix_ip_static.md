# login problem

After I've been using umbrel for a while. For 1 year I have been using it, I have never turned it off. and it's never been a problem. until one day I have moved the location of the node run. Then it started having access issues. I think I should save it. so that in the future I may have to use it again. And this may help you get through the chaos that may happen to you.

If you are having trouble logging in. For me, I use A2F for security. But now I can't access it, although my A2F code is absolutely correct. Including time update with Google. So, How do we solve it?

If unable to login from the web page. But, You can also access the umbrel via the command line, And you can access your node via SSH. Let you do the following.

1. Open your terminal, then enter the following commands : `ssh umbrel@umbrel.local` or `ssh umbrel@(ip address of umbrel node)`
2. Answer "yes" to confirm.
3. Enter your umbrel node password.
4. Edit `dhcpcd.conf` by the command `sudo nano /etc/dhcpcd.conf`
6. Add these notes to the bottom of the file.

~~~
#Configuration static IP address (CHANGE THE VALUES TO FIT FOR YOUR NETWORK)
interface eth0
static ip_address=192.168.1.xxx/24
static routers=192.168.1.1
static domain_name_servers=8.8.8.8, 8.8.4.4
~~~

7. Restart networking system by the command `sudo /etc/init.d/networking restart`
8. Log in via the web page again. hope to succeed

**NOTE** : Disconnecting the power supply is incorrect and should not be done. sudden disconnection of power supply This directly destroys your SSD. and you should avoid
