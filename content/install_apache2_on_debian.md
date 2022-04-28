Title: Installing Apache2 on Debian linux
Date: 2022-04-28 16:00
Modified: 2022-04-28 16:10
Category: Linux
Tags: linux, http, howto
Slug: installing-apache2-on-debian-linux
Authors: Tamas Molnar

# Installing Apache2 on Debian 11

The expected outcome is 

* To open a browser
* Type the IP address of the machine (DNS configuration is a topic for later)
* It must serve a new, custom html file called `index.html` with our string `"Hello, How are you?"`

# Preparation work

* Debian 11 netinstall in a VM is ready (it will be the server)
* The network configuration is ready (IP and port 80 are reachable)
* Root access on the VM

Some links about the topic I visited before starting the installation:

* The official website of the HTTP server is noted: [Apache2](https://httpd.apache.org/)
* The documentaion is already under our pillow: [Documentation](https://httpd.apache.org/docs/2.4/)
* A basic and **safe** installation is the plan: [Security Tips](https://httpd.apache.org/docs/2.4/misc/security_tips.html)
* The main site will go to the `/var/www/html` directory
* Protecting the system settings and information is a must
* Do **NOT** allow directory listing for clients

# Installation and configuration

* SSH to the target server machine
* Use `su -` to elevate the privileges to `root`
* Search for the `apache2` package in the Debian apt repo with `apt search apache2`
* We will find it in the default Debian repository like the followings:
```
apache2/stable 2.4.53-1~deb11u1 amd64
  Apache HTTP Server
```
* Install the package with the `apt install -y apache2` command
* The HTTP service will start immediately with serving the default Debian Apache2 page
* Stop the service with the `systemctl stop apache2` command
* Open the `/etc/apache2/apache2.conf` file in a text editor and configure it carefully

## ServerTokens

The `ServerTokens` default configuration will display the Operating System and Apache version.
Giving out this information to the possible attackers is not wise. Let them work for getting it. :)

Setting this option to `Prod` will only show that we run an Apache web server.

```
ServerTokens Prod
```

## ServerSignature

Pushing our security it even further we can turn off the whole server signature with the following configuration:
```
ServerSignature Off
ServerTokens Prod
```
After reloading the Apache configuration the service will not give out any hints about our system and server version.

## Directory listing

By the default configuration in the lack of an index file Apahce will show the contents of the directory.

**We do not want it at all!**

With the `-Indexes` option the browser will get an access denied message.
```
<Directory />
        Options -Indexes
        Options FollowSymLinks
        AllowOverride None
        Require all denied
</Directory>
```

# Change the default site

Now we can upload our new site that will be served by our Apache2 installation.

```
rm -f /var/www/html/index.html
echo "Hello, How are you?" > /var/www/html/index.html
systemctl start apache2
```

Open a browser and check the site!