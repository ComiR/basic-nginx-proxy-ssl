# Nginx Reverse Proxy with SSL

This is a config template for a nginx reverse proxy with SSL termination.

## Requirements

### Extra Files
* You'll need a `nginx.conf` which will `include conf.d/*.conf;` in the `http` section.  
  Otherwise, you'll need to figure out what's the best way for you to include the configuration.
* SSL certificate files `server.pem` and `server-key.pem` in directory `certs/`.
* `extra/dhparam.pem`, which you'll have to generate via `openssl dhparam -out extra/dhparam.pem 4096` (this can happen anywhere, where `openssl` is available, i.e. this does not have to happen on the server itself).

### Adjustments
* Domain name of the proxy server: `server_name` in [vhost.conf](conf.d/vhost.conf).
* Host of the server without SSL behind this proxy: `proxy_pass` in [vhost.conf](conf.d/vhost.conf).
* If you're not using docker, you need to adjust the IP of the DNS: `resolver` in [ssl.conf](mixins/ssl.conf).
