# terraria-server

Simple vanilla terraria server

## Create initial world
Go into the same directoryFirst create a new world by running this command and following prompts. Ctrl+C to exit after creating the world.
The world file can be found in a newly created `config` folder in the same directory.
```
sudo docker run --rm -it -v ./config:/config --name=terraria beardedio/terraria
```

## Start up Server
Start the server running in the background.
```
docker-compose up -d
```

## Connect client to the server
Open up terraria and go to Multiplayer. Select "Join via IP" then type the public IP of your server and port 7777.

## Troubleshooting
After the server has started, you can check logs with `docker logs terraria`.

1. Server is running but client is unable to connect
// TODO try curling or PING to diagnose problems
// TODO add info about firewalls
// TODO potentially add a link to port forwarding article

1. NullReferenceException
```
Exception: System.NullReferenceException: Object reference not set to an instance of an object
```
Make sure `tty` and `stdin_open` fields are present in the docker-compose.yaml
