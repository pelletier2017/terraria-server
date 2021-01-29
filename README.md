# terraria-server

Simple vanilla terraria server

## Prerequisites
docker and docker-compose installed

## Create initial world
Go into the same directoryFirst create a new world by running this command and following prompts. 
```
sudo docker run --rm -it -v $PWD/config:/config --name=terraria beardedio/terraria
```
After answering a few prompts it will return to the world screen which shows your newly created world as option 1.
Ctrl+C to exit when you finish with all the prompts.
The newely created world file can be found in the `config` folder in the same directory.

## Setting a password for the server
To set a password for the server or change any other settings go to `config/serverconfig.txt` and uncomment any lines to change. Restart the server for the change to take effect.

## Start up Server
Start the server running in the background.
```
docker-compose up -d
```

## Connect client to the server
Open up terraria and go to Multiplayer. Select "Join via IP" then type the public IP of your server and port 7777.

## Troubleshooting
After the server has started, you can check logs with `docker logs terraria`.

1. Error: Garbage collector could not allocate 16384 bytes of memory for major heap section.
This happens when the server does not have enough memory to create or load the given world size. To get around it, choose a smaller world size or allocate more RAM to the server.

1. NullReferenceException
```
Exception: System.NullReferenceException: Object reference not set to an instance of an object
```
Make sure `tty` and `stdin_open` fields are present in the docker-compose.yaml
