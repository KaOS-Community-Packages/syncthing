# syncthing

An open source continuous file synchronization

[Homepage](http://syncthing.net/)

Install:
```
kcp -i syncthing
```

To *enable and start the service*, replace “myuser” with the actual Syncthing
user after the @:
```
systemctl enable syncthing@myuser.service
systemctl start syncthing@myuser.service
```

The *admin GUI* starts automatically and remains available on https://localhost:8384/"

![alt tag](http://i.imgur.com/VWzG7V3.png)

