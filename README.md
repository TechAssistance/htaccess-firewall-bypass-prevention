# htaccess-firewall-bypass-prevention
A small compilation of htaccess snippets that will deny all requests that do not include firewall headers 

The gist being something like this for almost all of them. Now some do not include the headers in their docs or do not add them unless you enable debug mode. I would recommend adding your own inserted header in this case. Especaill for AWS, AKAMI, etc. 
```
# BEGIN Website Firewall Bypass Prevention
RewriteEngine On
RewriteCond %{HTTP_HOST} ^(www.)?defaultdomain.com$
RewriteCond %{HTTP:HEADER-GOES-HERE} ^$
RewriteRule ^(.*)$ - [F,L]
ErrorDocument 403 Forbidden
# END Website Firewall Bypass Prevention
```
