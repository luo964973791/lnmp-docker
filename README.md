1.docker network create lnmpr</br>
2.docker-compose up --build -d</br>
3.#nginx/conf.d/default.conf 设置成php容器的目录，否则无法解析php</br>
本docker-compose nginx 挂载为 ./app:/usr/share/nginx/html</br>
php 挂载为 ./app:/var/www/html</br>
4.例如1</br>
##################################################</br>
location / {</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;root /usr/share/nginx/html; #注意路径</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;index index.html index.htm index.php;</br>
}</br>
location ~ .php$ {</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;root /var/www/html; #这里为php容器挂载路径注意否则无法解析php</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fastcgi_pass php:9000;</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fastcgi_index index.php;</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;include fastcgi_params;</br>
}</br>
##################################################</br>
例如2</br>
location / {</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;root /usr/share/nginx/html/test; #注意路径</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;index index.html index.htm index.php;</br>
}</br>
location ~ .php$ {</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;root /var/www/html/test; #和上面的路径对应</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fastcgi_pass php:9000;</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fastcgi_index index.php;</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;</br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;include fastcgi_params;</br>
}
##################################################
