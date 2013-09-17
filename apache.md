# General
- Always set ``AllowOverride`` to ``None`` on debugging unexpected configuration behaviour, chances are that an ``.htaccess``-file is causing the trouble.
- Set ``AllowOverride`` to ``None`` permanently and put everything into the vhost/main configuration files. Makes your setup a bit more secure and because not every directory has to be traversed recursively to search for an ``.htaccess``-file, also more performant.

# How-Tos
## Allow Hosts with Certain IP-Addresses to Bypass HTTP Basic Authentication on a Webserver behind a Proxy (Requires ``X-Forwarded-For`` to be Set)

    <Directory /var/www/>
      SetEnvIf X-Forwarded-For 172.16.37.1 allow
      SetEnvIf X-Forwarded-For 172.16.37.4 allow
      Order deny,allow
      deny from all
      Allow from env=allow
      AuthType Basic
      AuthName login
      AuthUserFile /etc/httpd/passwd
      Require valid-user
      Satisfy any
      Options Indexes FollowSymLinks MultiViews
    </Directory>

## Serve an Maintenance Page Except for Some Hosts
    RewriteEngine On
    RewriteBase /
    RewriteCond %{REMOTE_ADDR} !^(144\.257\.357\.328|127\.0\.0|172\.16\.30|728\.420\.650\.210) # internal or external networks you don't want to serve the maintenance page for.
    RewriteCond %{REQUEST_URI} !^/maintenance\.html$
    RewriteCond %{REQUEST_URI} !^/maintenance\.jpg$
    RewriteRule ^(.*)$ http://www.example.com/maintenance.html [L]

## Set PHP Errors for Debugging
    php_flag display_startup_errors on
    php_flag display_errors on
    php_flag html_errors on
    php_flag  log_errors on
    php_value error_log  /var/www/html/phperrors.log

## Improve Security
    Header always append X-Frame-Options SAMEORIGIN
    TraceEnable Off
    ServerSignature Off
    ServerTokens Prod

## Permissions
    HTTPDUSER=www-data; HTTPUSER=foo HTTPDOCS=/var/www;
    usermod -a -G $HTTPDUSER $HTTPUSER;
    chown root:$HTTPDUSER $HTTPDOCS
    chmod 2775 $HTTPDOCS
    echo 'umask 002' >> /etc/apache2/envvars
    echo 'umask 002' >> /home/$HTTPUSER/.zshrc.local
    echo 'umask 002' >> /home/$HTTPUSER/.bashrc
    find $HTTPDOCS -type d -exec chmod 2775 {} \;
    find $HTTPDOCS -type f -exec chmod 0664 {} \;

<!---
 vim: expandtab tabstop=4 shiftwidth=4
-->
