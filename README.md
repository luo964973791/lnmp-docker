#nginx/conf.d/default.conf 设置成php容器的目录，否则无法解析php
fastcgi_param  SCRIPT_FILENAME  /var/www/html$fastcgi_script_name;
