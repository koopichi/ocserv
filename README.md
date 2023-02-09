# OpenConnect-VPN-Server
## Script Installation
Tested on ubuntu 18.04 and 16.04.

Download and saving script on your server:
```bash
curl -O https://raw.githubusercontent.com/koopichi/ocserv/master/ocserv-install.sh
```

Making script executable
```bash
chmod +x ocserv-install.sh
```

And then just run it:
```sh
./ocserv-install.sh
``` 
or
```sh
sudo bash ocserv-install.sh
``` 

## Docker Installation
1. Install Docker
2. Build docker image
```bash
docker build -t ocserv https://github.com/koopichi/ocserv.git
```

3. Run docker container
```bash
docker run --name ocserv --privileged -p 443:443 -p 443:443/udp -d ocserv
```
4. Run container at Startup
```bash
docker update --restart unless-stopped $(docker ps -q)
```
5. Add user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd testUserName
```

6. Change user password
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd testUserName
```

7. Delete user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -d testUserName
```

8. Lock user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -l testUserName
```

9. Unlock user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -u testUserName
```

10. Show all users and their hashed password
```bash
docker exec -ti ocserv cat /etc/ocserv/ocpasswd
```

## Features
- Easy install
- Easy uninstall
- Add User
- Change Password
- Show All Users
- Delete User
- Lock User
- Unlock User

## How to connect to it?
For making connection to your server, you can use `AnyConnect`, `OpenConnect` or other alternative clients.

- AnyConnect: [GUI AnyConnect client for available platforms](https://it.umn.edu/vpn-downloads-guides).
- OpenConnect: [OpenConnect client for Linux](https://computingforgeeks.com/how-to-connect-to-vpn-server-with-openconnect-ssl-vpn-client-on-linux/).

And one more thing, contributions are welcome.

## More
The script is based on [here](https://ocserv.gitlab.io/www/recipes-ocserv-configuration-basic.html)