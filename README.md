# Hot to create a daemon in linux

## Step 1

Go to 

```
$ cd /etc/systemd/system/
```

## Step 2
create a new service
```
$ sudo touch myservice.service
```

##Step 3
open it with vim, nano or whatever editor what do you want, put this test code

```.env
[Unit]
Description=Testing service

[Service]
Type=simple
ExecStart=/usr/bin/last_connection
ExecSTop=/usr/bin/remove_connection
RemainAfterExist=yes

[Install]
WantedBy=multi-user.target
```

## Step 4
Copy the two scripts last_connection and remove_connection to /usr/bin and make it executable:
```bash
$ sudo cp last_connetion /usr/bin/
$ sudo cp remove_connection /usr/bin/
$ sudo chmod 644 /usr/bin/last_connetion
$ sudo chmod 644 /usr/bin/remove_connection
```

## Step 5
now start and enable the service

```
$ sudo systemctl start myservice
```

## Step 6

check if service is running

```
$ systemctl list-unit-files -t service|grep last_connection
```

The service can be stopped or restarted using standard systemd commands:
```
$ sudo systemctl stop myservice
$ sudo systemctl restart myservice
```

## Step 7

Finally, use the enable command to ensure that the service starts whenever the system boots

```bash
$ sudo systemctl enable myservice
```
