## Docker Installation
1. Install Docker
```bash
bash <(curl -Ls https://raw.githubusercontent.com/koopichi/ocserv/master/dk.sh)
```
2. Build docker image
```bash
docker build -t ocserv https://github.com/koopichi/ocserv.git
```

3. Run docker container
```bash
docker run --name ocserv --privileged -p 8443:443 -p 8443:443/udp -v ocserv:/etc/ocserv -d ocserv
```
4. Set container to run at Startup
```bash
docker update --restart unless-stopped $(docker ps -q)
```
5. Add user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd test
```

6. Change user password
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd test
```

7. Delete user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -d test
```

8. Lock user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -l test
```

9. Unlock user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -u test
```

10. Show all users and their hashed password
```bash
docker exec -ti ocserv cat /etc/ocserv/ocpasswd
```
11. enable BBR
```bash
bash <(curl -Ls https://raw.githubusercontent.com/koopichi/ocserv/master/bbr.sh)
```
