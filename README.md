# docker-iop-location

Docker container for running Internet of People Location Network

Available Architectures:

AMD64
ARM7

## Ports

 * 16980 for node2node communication
 * 16981 for client2node queries
 * 16982 for interprocess communication between local services

## Volumes

/data/ipfs is the container directory that ipfs uses

Do note: The mounted directory on the device needs to be owned by user with uid 1000

If you do not want the data persisted you can leave the -v command

###

* nodeid YourNodeIdHere 
* latitude 48.2081743 
* longitude 16.3738189

## Running the container

```
docker run -d --name iop-loc -p 16980:16980 -p 16981:16981 -p 127.0.0.1:16982:16982 -e  -v /opt/loc:/data/locnet/ libertaria/iop-loc

```
## Stopping container

```
docker stop iop-loc

```

## Starting container

```
docker start iop-loc

```


## Running with Docker compose

```
version: '2'
services:
  iop-can:
    image: libertaria/iop-loc
    ports:
      - 16980:16980
      - 16981:16981
      - 127.0.0.1:16982:16982
    environment:
      - NODEID=YourNodeIdHere  
      - LATITUDE=48.2081743 
      - LONGITUDE=16.3738189
    volumes:
      - /opt/loc:/data/locnet
```  