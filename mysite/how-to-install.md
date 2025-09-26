## Як встановити
1. Скачати репозиторій або лише папку `/mysite`
2. Помістити його за шляхом `/var/www/sites/mysite`
3. Створити файл `mysite` за шлахом `/etc/nginx/sites-available`
4. Конфіг, що прикріплений нижче, вставити у файл `mysite`
5. Створити посилання на `mysite` у шляху `/etc/nginx/sites-enabled` командою нижче
   ```terminal
   sudo ln -s /etc/nginx/sites-available/mysite /etc/nginx/sites-enabled/
   ```
6. Перезапустити nginx сервер і готово 👍

## nginx config
```nginx
server {
    listen 80;
    root /var/www/sites/mysite/src/;
    index index.html;

    location /loc2 {
        root /location1;
    }

    location /test {
        alias /var/www/sites/mysite/src/location1;
    }

    location /alt {
        try_files /alt/main.html /fallback.html =404;
    }
}
```
