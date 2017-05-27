> https://gist.github.com/davestevens/c9e437afbb41c1d5c3ab

### nginx
```
server {
    listen              443 ssl;
    server_name         example.com;
    ssl_certificate     /etc/letsencrypt/live/example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
}
```