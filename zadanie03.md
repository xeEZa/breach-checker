PS C:\Users\Student_PL\cyberMWgr5\breach-checker> docker inspect --format '{{json .Config.Labels}}' miron-rokita-frontend:v1
{"data":"2026-10-14","maintainer":"miron.rokita@example.com"}
PS C:\Users\Student_PL\cyberMWgr5\breach-checker> docker inspect --format '{{json .Config.Labels}}' miron-rokita-frontend:latest
{"data":"2026-10-14","maintainer":"miron.rokita@example.com"}

 root   /usr/share/nginx/html;
PS C:\Users\Student_PL\cyberMWgr5\breach-checker> docker exec frontend ls /usr/share/nginx
html
index.html
script.js
style.css
PS C:\Users\Student_PL\cyberMWgr5\breach-checker> docker exec frontend ls /usr/share/nginx/html
50x.html
build.txt
index.html

PS C:\Users\Student_PL\cyberMWgr5\breach-checker> docker rmi breach-checker-frontend:latest
Untagged: breach-checker-frontend:latest

PS C:\Users\Student_PL\cyberMWgr5\breach-checker> docker rmi breach-checker-frontend:v2
Untagged: breach-checker-frontend:v2
Deleted: sha256:30fbc04088e2182ead662bd50a5899d84ad1317ffceaa59f79aa95c519d4ead9
