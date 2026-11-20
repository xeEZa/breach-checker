zad1
[+] up 6/6
 ✔ Image breach-checker-frontend       Built                                                                        2.2s
 ✔ Image breach-checker-backend        Built                                                                        2.1s
 ✔ Network breach-checker_default      Created                                                                      0.1s
 ✔ Container breach-checker-db-1       Healthy                                                                      6.3s
 ✔ Container breach-checker-backend-1  Healthy                                                                     11.4s
 ✔ Container breach-checker-frontend-1 Started


 PS C:\Users\Student_PL\cyberMW5\breach-checker> docker ps
CONTAINER ID   IMAGE                     COMMAND                  CREATED              STATUS                        PORTS                                     NAMES
a883d107c784   breach-checker-frontend   "/docker-entrypoint.…"   About a minute ago   Up About a minute             0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   breach-checker-frontend-1
b06c535663bb   breach-checker-backend    "python app.py"          About a minute ago   Up About a minute (healthy)   5000/tcp                                  breach-checker-backend-1
8116e9538e40   postgres:16-alpine        "docker-entrypoint.s…"   About a minute ago   Up About a minute (healthy)   5432/tcp                                  breach-checker-db-1


zadanie 2
S C:\Users\Student_PL\cyberMW5\breach-checker> docker compose down
[+] down 4/4
 ✔ Container breach-checker-frontend-1 Removed                                                                      0.4s
 ✔ Container breach-checker-backend-1  Removed                                                                      3.3s
 ✔ Container breach-checker-db-1       Removed                                                                      0.3s
 ✔ Network breach-checker_default      Removed                                                                      0.2s"
PS C:\Users\Student_PL\cyberMW5\breach-checker> docker compose up -d
[+] up 4/4
 ✔ Network breach-checker_default      Created                                                                      0.0s
 ✔ Container breach-checker-db-1       Healthy                                                                      6.2s
 ✔ Container breach-checker-backend-1  Healthy                                                                     11.3s
 ✔ Container breach-checker-frontend-1 Started                                                                     11.4s
PS C:\Users\Student_PL\cyberMW5\breach-checker> docker compose exec db psql -U breach -d breachdb -c "INSERT INTO leaked_hashes VALUES ('bc45408273d7e1914b741c3407b0b559764f7876');"
ERROR:  duplicate key value violates unique constraint "leaked_hashes_pkey"
DETAIL:  Key (hash)=(bc45408273d7e1914b741c3407b0b559764f7876) already exists.

What's next:
    Debug this Compose error with Gordon → docker ai "help me fix this compose error"


PS C:\Users\Student_PL\cyberMW5\breach-checker> docker compose down -v
[+] down 5/5
 ✔ Container breach-checker-frontend-1 Removed                                                                      0.4s
 ✔ Container breach-checker-backend-1  Removed                                                                      3.2s
 ✔ Container breach-checker-db-1       Removed                                                                      0.3s
 ✔ Network breach-checker_default      Removed                                                                      0.2s
 ✔ Volume breach-checker_pgdata        Removed                                                                      0.0s
PS C:\Users\Student_PL\cyberMW5\breach-checker> docker compose up -d
[+] up 5/5
 ✔ Network breach-checker_default      Created                                                                      0.0s
 ✔ Volume breach-checker_pgdata        Created                                                                      0.0s
 ✔ Container breach-checker-db-1       Healthy                                                                      6.2s
 ✔ Container breach-checker-backend-1  Healthy                                                                     11.3s
 ✔ Container breach-checker-frontend-1 Started                                                                     11.4s
PS C:\Users\Student_PL\cyberMW5\breach-checker> docker compose exec db psql -U breach -d breachdb -c "INSERT INTO leaked_hashes VALUES ('bc45408273d7e1914b741c3407b0b559764f7876');"
INSERT 0 1


zad 3
PS C:\Users\Student_PL\cyberMW5\breach-checker> docker compose ps
NAME                        IMAGE                     COMMAND                  SERVICE    CREATED              STATUS                        PORTS
breach-checker-backend-1    breach-checker-backend    "python app.py"          backend    About a minute ago   Up About a minute (healthy)   5000/tcp
breach-checker-backend-2    breach-checker-backend    "python app.py"          backend    46 seconds ago       Up 44 seconds (healthy)       5000/tcp
breach-checker-backend-3    breach-checker-backend    "python app.py"          backend    46 seconds ago       Up 44 seconds (healthy)       5000/tcp
breach-checker-db-1         postgres:16-alpine        "docker-entrypoint.s…"   db         About a minute ago   Up About a minute (healthy)   5432/tcp
breach-checker-frontend-1   breach-checker-frontend   "/docker-entrypoint.…"   frontend   About a minute ago   Up About a minute             0.0.0.0:8080->80/tcp, [::]:8080->80/tcp


PS C:\Users\Student_PL\cyberMW5\breach-checker> docker compose exec frontend nslookup backend
Server:         127.0.0.11
Address:        127.0.0.11:53

Non-authoritative answer:

Non-authoritative answer:
Name:   backend
Address: 172.19.0.3
Name:   backend
Address: 172.19.0.6
Name:   backend
Address: 172.19.0.5
backend-1   | 172.19.0.6 - - [20/Nov/2026 10:35:00] "POST /check HTTP/1.1" 200 -
backend-1   | check: hash=4ce91...
backend-1   | 172.19.0.6 - - [20/Nov/2026 10:35:00] "POST /check HTTP/1.1" 200 -
backend-1   | check: hash=4ce91...
backend-1   | 172.19.0.6 - - [20/Nov/2026 10:35:01] "POST /check HTTP/1.1" 200 -
backend-1   | check: hash=4ce91...


backend-1   | check: hash=4ce91...
backend-1   | 172.19.0.6 - - [20/Nov/2026 10:35:01] "POST /check HTTP/1.1" 200 -
backend-1   | check: hash=4ce91...
backend-1   | 172.19.0.6 - - [20/Nov/2026 10:35:01] "POST /check HTTP/1.1" 200 -
backend-1   | check: hash=4ce91...
backend-1   | 172.19.0.6 - - [20/Nov/2026 10:35:02] "POST /check HTTP/1.1" 200 -
backend-1   | check: hash=4ce91...

backend-2   | 172.19.0.6 - - [20/Nov/2026 10:35:00] "POST /check HTTP/1.1" 200 -
backend-2   | check: hash=4ce91...
backend-2   | 172.19.0.6 - - [20/Nov/2026 10:35:00] "POST /check HTTP/1.1" 200 -
backend-2   | check: hash=4ce91...
backend-2   | 172.19.0.6 - - [20/Nov/2026 10:35:01] "POST /check HTTP/1.1" 200 -
backend-2   | check: hash=4ce91...

backend-3   | 172.19.0.6 - - [20/Nov/2026 10:35:01] "POST /check HTTP/1.1" 200 -
backend-3   | check: hash=4ce91...
backend-3   | 172.19.0.6 - - [20/Nov/2026 10:35:01] "POST /check HTTP/1.1" 200 -
backend-3   | check: hash=4ce91...
backend-3   | 172.19.0.6 - - [20/Nov/2026 10:35:01] "POST /check HTTP/1.1" 200 -
backend-3   | check: hash=4ce91...
