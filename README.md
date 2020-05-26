# Hot to create a daemon in linux

## Step 1

Go to 

```
$ cd /etc/systemd/system/
```
## Step 2
create a new service
```
$ touch mydaemon.service
```

##Step 3
open it with vim, nano or whatever editor what do you want, put this test code

```.env
[Unit]
Description=Testing service

[Service]
Type=simple
ExecStart=~/shell/last_connection
ExecSTop=~/shell/remove_connection
RemainAfterExist=yes

[Install]
WantedBy=multi-user.target
```

## Step 4
now reload services

```.env
$ systemctl daemon-reload
```

## Step 5

check if service is running

```
$ systemctl list-unit-files -t service|grep last_connection
```
