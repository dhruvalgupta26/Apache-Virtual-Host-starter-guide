## How to create a virtual APPACHE HOST

**step1: Install apache2 on your system**

```
sudo apt-get install apache2

```

**step2: Create a Document root Directory**

```

sudo mkdir -p /var/www/your_domain

sudo chown -R $USER:$USER /var/www/your_domain

sudo chmod -R 755 /var/www/your_domain


```

**step3: create an index.html file**

```
sudo nano /var/www/your_domain/index.html

```

```
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Welcome to domain1.com</title>
  </head>
  <body>
    <h1>Success! domain1.com home page!</h1>
  </body>
</html>
```

**step4: Create a virtual host**

```

sudo nano /etc/apache2/sites-available/your_domain.com.conf


```
```
<VirtualHost *:80>
    ServerName domain1.com
    ServerAlias www.domain1.com
    ServerAdmin webmaster@domain1.com
    DocumentRoot /var/www/domain1.com/public_html
</VirtualHost>

```

**step5: create a symbolic link**

```
sudo a2dissite 000-default.conf

systemctl reload apache2

sudo a2ensite your_domain.com.conf

```

**step6: Add Host**

``` 
sudo nano /etc/hosts

```

```
127.0.0.1    www.yourdomain.com
```

**step7: Restart Apache**

```
sudo systemctl restart apache2

```

**step8: Test**

```

http://www.yourdomain.com

```

