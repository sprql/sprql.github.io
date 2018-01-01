---
layout:  post
title:   "Let's Encrypt + nginx = https"
date:    2018-01-01 00:00:00 +0000
excerpt: "Short introduction how to obtain free SSL certificates for sites from letsencrypt.org"
image:   "https://certbot.eff.org/images/certbot-logo-1A.svg"
---

Do You want to start using https for your sites?! There is nothing easier — thanks we have [Let's Encrypt][letsencrypt] project now!

Ok, so how to setup SSL/HTTPS for [nginx][nginx]:

I assume you have installed [nginx][nginx], and have installed [certbot][certbot].

I will consider a scenario where is used [nginx][nginx] as the server for responding to [ACME][acme].

So as the first step we will create default directory where [certbot][certbot] would create files for all our sites.

```
mkdir -p /srv/www/acme
```

Which use [/srv vs /var][srv-vs-var] no matter, it's you choose.

Next step is to configure your nginx. 

Create `/etc/nginx/conf.d/acme.conf`:

```
location ~ /.well-known {    
    root /srv/www/acme;
}
```

And include this config for all your sites:

```
server {
   ...
   server_name example.com;

   include conf.d/acme.conf;
   ...
}
```
  

Don't forget to reload nginx to update config.

And finally we're ready to obtain certificates:

```
certbot certonly --webroot  -w /srv/www/acme/ --agree-tos --email mail@example.com -d example.com -d www.example.com
```

When the procedure would be successful you should get a message like this: 

```
...
IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at
   /etc/letsencrypt/live/example.com/fullchain.pem. Your cert will
   expire on 2018-01-01. To obtain a new or tweaked version of this
   certificate in the future, simply run certbot again. To
   non-interactively renew *all* of your certificates, run "certbot
   renew"
...   
```

Well done!

How to configure nginx to use new certs see in my next post...

[letsencrypt]: https://letsencrypt.org
[nginx]: https://nginx.org
[srv-vs-var]: http://www.codeghar.com/blog/should-web-apps-go-in-srv-or-var-www.html 
[certbot]: https://certbot.eff.org
[acme]: https://tools.ietf.org/html/draft-ietf-acme-acme-09