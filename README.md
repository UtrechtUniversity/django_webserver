# django_webserver
Basic installation of Django on SurfCloud.

In development (todo)

add gunicorn folders in var/{log, run}
add site config in nginx conf
shell commands to connect django with gunicorn and nginx (after development is finished)

add host info django settings.py
sudo sed -i "s/ALLOWED_HOSTS = []/ALLOWED_HOSTS = ["$(curl ifconfig.me)", "127.0.0.1" , "$(sed -ne '/server_name/{s/.server_name //; s/[; ].//; p; q}' /etc/nginx/conf.d/ssl_main.conf)"]/g" ~/settings.py
sudo systemctl restart nginx
sudo gunicorn -c ~/config/gunicorn/dev.py