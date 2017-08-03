# htaccess
Redirect Non www urls to www
RewriteBase /
RewriteCond %{HTTPS} off
# First rewrite to HTTPS:
RewriteRule .* https://%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
# Now, rewrite any request to the wrong domain to use www.
# [NC] is a case-insensitive match
RewriteCond %{HTTP_HOST} !^www\. [NC]
RewriteRule .* https://www.%{HTTP_HOST}%{REQUEST_URI} [L,R=301]
