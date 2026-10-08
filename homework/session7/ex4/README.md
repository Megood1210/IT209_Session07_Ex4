user@DESKTOP-TLV7LQG:~$ sudo systemctl reload nginx
user@DESKTOP-TLV7LQG:~$ curl -i http://localhost/api/health
HTTP/1.1 200 
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 07 Oct 2026 13:36:53 GMT
Content-Type: text/plain;charset=UTF-8
Content-Length: 30
Connection: keep-alive

Spring Boot backecurl -i http://127.0.0.1:8082/healthi http://127.0.0.1:8082/health
curl -i http://localhost/api/health
HTTP/1.1 200 
Content-Type: text/plain;charset=UTF-8
Content-Length: 30
Date: Wed, 07 Oct 2026 13:37:02 GMT

Spring Boot backend is runningHTTP/1.1 200 
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 07 Oct 2026 13:37:02 GMT
Content-Type: text/plain;charset=UTF-8
Content-Length: 30
Connection: keep-alive

Spring Boot backesudo find /etc/nginx/sites-enabled -mindepth 1 -maxdepth 1 \bled -mindepth 1 -maxdepth 1 \
  ! -name spring-proxy.conf -delete

sudo nginx -t
sudo systemctl reload nginx
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
user@DESKTOP-TLV7LQG:~$ exit
logout
Connection to 160.187.229.99 closed.
user@MacBook-Pro-cua-ang demo1 % cd ..                             
user@MacBook-Pro-cua-ang IT209 % mkdir -p ss07/ex04
user@MacBook-Pro-cua-ang IT209 % cd ss07/ex04
user@MacBook-Pro-cua-ang ex04 % ssh devops@160.178.229.99
^C
user@MacBook-Pro-cua-ang ex04 % ssh devops@160.187.229.99
devops@160.187.229.99's password: 
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 5.15.0-46-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Wed Oct  7 10:20:57 PM +07 2026

  System load:  0.0                Processes:             99
  Usage of /:   32.0% of 19.59GB   Users logged in:       0
  Memory usage: 28%                IPv4 address for eth0: 160.187.229.99
  Swap usage:   0%

 * Canonical Workshop gives developers fast, composable, reproducible, and
   secure developer environments that are perfect for agentic workflows.

   https://ubuntu.com/workshop

Expanded Security Maintenance for Applications is not enabled.

13 updates can be applied immediately.
13 of these updates are standard security updates.
To see these additional updates run: apt list --upgradable

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status

New release '24.04.5 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


*** System restart required ***
Last login: Wed Oct  7 20:27:09 2026 from 27.76.16.89
devops@user:~$ sudo cp /etc/nginx/sites-available/spring-proxy.conf .
[sudo] password for devops: 
devops@user:~$ sudo chown devops:devops spring-proxy.conf 
devops@user:~$ {
    echo "===== KIEM TRA CAU HINH NGINX ====="
    sudo nginx -t 2>&1

    echo
    echo "===== KIEM TRA TRANG TINH ====="
    curl -i http://localhost/

    echo
    echo "===== KIEM TRA SPRING BOOT TRUC TIEP ====="
    curl -i http://127.0.0.1:8082/health

    echo
    echo "===== KIEM TRA API QUA NGINX ====="
    curl -i http://localhost/api/health
} | tee ket-qua-kiem-tra.txt
===== KIEM TRA CAU HINH NGINX =====
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

===== KIEM TRA TRANG TINH =====
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   259  100   259    0     0  38421      0 --:--:-- --:--:-- --:--:-- 43166
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 07 Oct 2026 15:21:59 GMT
Content-Type: text/html
Content-Length: 259
Last-Modified: Wed, 07 Oct 2026 04:00:56 GMT
Connection: keep-alive
ETag: "6ac5c3f8-103"
Accept-Ranges: bytes

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Thông tin học viên</title>
</head>
<body>
    <h1>Spring Boot và Nginx Reverse Proxy</h1>
    <p>Họ tên: Đặng Khánh An</p>
    <p>Mã lớp: PTIT070</p>
</body>
</html>

===== KIEM TRA SPRING BOOT TRUC TIEP =====
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    30  100    30    0     0   2949      0 --:--:-- --:--:-- --:--:--  3333
HTTP/1.1 200 
Content-Type: text/plain;charset=UTF-8
Content-Length: 30
Date: Wed, 07 Oct 2026 15:21:59 GMT

Spring Boot backend is running
===== KIEM TRA API QUA NGINX =====
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100    30  100    30    0     0   2108      0 --:--:-- --:--:-- --:--:--  2307
HTTP/1.1 200 
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 07 Oct 2026 15:21:59 GMT
Content-Type: text/plain;charset=UTF-8
Content-Length: 30
Connection: keep-alive

Spring Boot backecat ket-qua-kiem-tra.txtnh:~$ cat ket-qua-kiem-tra.txt
===== KIEM TRA CAU HINH NGINX =====
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

===== KIEM TRA TRANG TINH =====
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 07 Oct 2026 15:21:59 GMT
Content-Type: text/html
Content-Length: 259
Last-Modified: Wed, 07 Oct 2026 04:00:56 GMT
Connection: keep-alive
ETag: "6ac5c3f8-103"
Accept-Ranges: bytes

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Thông tin học viên</title>
</head>
<body>
    <h1>Spring Boot và Nginx Reverse Proxy</h1>
    <p>Họ tên: Đặng Khánh An</p>
    <p>Mã lớp: PTIT070</p>
</body>
</html>

===== KIEM TRA SPRING BOOT TRUC TIEP =====
HTTP/1.1 200 
Content-Type: text/plain;charset=UTF-8
Content-Length: 30
Date: Wed, 07 Oct 2026 15:21:59 GMT

Spring Boot backend is running
===== KIEM TRA API QUA NGINX =====
HTTP/1.1 200 
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 07 Oct 2026 15:21:59 GMT
Content-Type: text/plain;charset=UTF-8
Content-Length: 30
Connection: keep-alive

Spring Boot backend is runningdevops@user:~$ nano README.md
devops@user:~$ curl -i http://localhost/
curl -i http://127.0.0.1:8082/health
curl -i http://localhost/api/health
HTTP/1.1 200 OK
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 07 Oct 2026 15:23:03 GMT
Content-Type: text/html
Content-Length: 259
Last-Modified: Wed, 07 Oct 2026 04:00:56 GMT
Connection: keep-alive
ETag: "6ac5c3f8-103"
Accept-Ranges: bytes

<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Thông tin học viên</title>
</head>
<body>
    <h1>Spring Boot và Nginx Reverse Proxy</h1>
    <p>Họ tên: Đặng Khánh An</p>
    <p>Mã lớp: PTIT070</p>
</body>
</html>
HTTP/1.1 200 
Content-Type: text/plain;charset=UTF-8
Content-Length: 30
Date: Wed, 07 Oct 2026 15:23:03 GMT

Spring Boot backend is runningHTTP/1.1 200 
Server: nginx/1.18.0 (Ubuntu)
Date: Wed, 07 Oct 2026 15:23:03 GMT
Content-Type: text/plain;charset=UTF-8
Content-Length: 30
Connection: keep-alive

Spring Boot backend is runningdevops@user:~$ 
