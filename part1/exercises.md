# Exercises for part 1

## 1.1

```

^Cvili@T490:~/projects/hy-docker/part1$ docker run -d nginx
6aa6f35258c4e29712897f276b731cdd075001138b921f20a5e326a727e91880
vili@T490:~/projects/hy-docker/part1$ docker run -d nginx
b6b5573b43675437559426dadb21b68d010957da8c5371d3be1f7437fa26f245
vili@T490:~/projects/hy-docker/part1$ docker run -d nginx
7f2be2d58a89ecb093f8e54089c95f3e337589bb12e1b0701fee2a555fd2ffe3
vili@T490:~/projects/hy-docker/part1$ docker stop 6aa b6b
6aa
b6b
vili@T490:~/projects/hy-docker/part1$ docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                      PORTS               NAMES
7f2be2d58a89        nginx               "nginx -g 'daemon of…"   23 seconds ago      Up 21 seconds               80/tcp              elastic_wilbur
b6b5573b4367        nginx               "nginx -g 'daemon of…"   24 seconds ago      Exited (0) 5 seconds ago                        vigilant_shtern
6aa6f35258c4        nginx               "nginx -g 'daemon of…"   26 seconds ago      Exited (0) 5 seconds ago                        fervent_booth
e66d0a06e79c        nginx               "nginx -g 'daemon of…"   39 seconds ago      Exited (0) 30 seconds ago                       flamboyant_goldberg
vili@T490:~/projects/hy-docker/part1$ 
```

## 1.2

```
vili@T490:~/projects/hy-docker/part1$ docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
vili@T490:~/projects/hy-docker/part1$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
vili@T490:~/projects/hy-docker/part1$ 
```

## 1.3 

```
vili@T490:~/projects/hy-docker/part1$ docker run -it devopsdockeruh/pull_exercise
Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"

vili@T490:~/projects/hy-docker/part1$ 
```

## 1.4

```
vili@T490:~/projects/hy-docker/part1$ docker run -d devopsdockeruh/exec_bash_exercise
ca468df5e4f09c55e3c93b279c72e882fca1ce41ca2769ec4d2cffcd2a5c3586
vili@T490:~/projects/hy-docker/part1$ docker ps
CONTAINER ID        IMAGE                               COMMAND             CREATED             STATUS              PORTS               NAMES
ca468df5e4f0        devopsdockeruh/exec_bash_exercise   "node index"        17 seconds ago      Up 17 seconds                           compassionate_burnell
vili@T490:~/projects/hy-docker/part1$ docker exec -it compassionate_burnell bash
root@ca468df5e4f0:/usr/app# ll
bash: ll: command not found
root@ca468df5e4f0:/usr/app# ls
Dockerfile  README.md  index.js  logs.txt
root@ca468df5e4f0:/usr/app# cat logs.txt 
Thu, 23 May 2019 13:23:08 GMT
Thu, 23 May 2019 13:23:11 GMT
Thu, 23 May 2019 13:23:14 GMT
Thu, 23 May 2019 13:23:17 GMT
Secret message is:
"Docker is easy"
Thu, 23 May 2019 13:23:23 GMT
Thu, 23 May 2019 13:23:26 GMT
Thu, 23 May 2019 13:23:29 GMT
Thu, 23 May 2019 13:23:32 GMT
Secret message is:
"Docker is easy"
Thu, 23 May 2019 13:23:38 GMT
Thu, 23 May 2019 13:23:41 GMT
Thu, 23 May 2019 13:23:44 GMT
Thu, 23 May 2019 13:23:47 GMT
root@ca468df5e4f0:/usr/app# 
```

## 1.5

```
vili@T490:~/projects/hy-docker/part1$ docker run -d --rm -it --name curler ubuntu:xenial sh -c 'echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
62ecda9e1231aed8913e09f812c6ee98af07ac509b9d0f12c0ddc00642028de3
vili@T490:~/projects/hy-docker/part1$ docker exec -it curler apt-get update

...

vili@T490:~/projects/hy-docker/part1$ docker exec -it curler apt-get install curl wget

...

vili@T490:~/projects/hy-docker/part1$ docker attach curler 
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
vili@T490:~/projects/hy-docker/part1$ 

```

## 1.6

```
vili@T490:~/projects/hy-docker/part1/docker-clock$ docker build -t docker-clock .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM devopsdockeruh/overwrite_cmd_exercise
 ---> 0f7f459b76c9
Step 2/2 : CMD ["-c"]
 ---> Running in 88a390f1e954
Removing intermediate container 88a390f1e954
 ---> 8f74ecf55214
Successfully built 8f74ecf55214
Successfully tagged docker-clock:latest
vili@T490:~/projects/hy-docker/part1/docker-clock$ docker run docker-clock
1
2
3
4
5
6
7
```

[Dockerfile](./docker-clock/Dockerfile)

## 1.7

```
vili@T490:~/projects/hy-docker/part1/docker-curler$ docker build -t curler .
Sending build context to Docker daemon  3.072kB
Step 1/4 : FROM ubuntu:xenial
 ---> 2a697363a870
Step 2/4 : RUN apt-get update && apt-get install -y curl
 ---> Using cache
 ---> b9e5192302ac
Step 3/4 : COPY curler.sh .
 ---> 2b657f8a457c
Step 4/4 : CMD ["./curler.sh"]
 ---> Running in b7395e224602
Removing intermediate container b7395e224602
 ---> f12ddde6286f
Successfully built f12ddde6286f
Successfully tagged curler:latest
vili@T490:~/projects/hy-docker/part1/docker-curler$ docker run -it curler
Input website:
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
vili@T490:~/projects/hy-docker/part1/docker-curler$ 

```

[Dockerfile](./docker-curler/Dockerfile)

## 1.8

Create the logs.txt file to docker-test directory

`vili@T490:~/projects/hy-docker/part1/docker-test$ touch logs.txt`

run container with volume bind mount

`vili@T490:~/projects/hy-docker/part1$ docker run -v $(pwd)/docker-test/logs.txt:/usr/app/logs.txt devopsdockeruh/first_volume_exercise`

## 1.9

```
vili@T490:~/projects/hy-docker/part1/youtube-dl$ docker run -d -p 4321:80 devopsdockeruh/ports_exercise
13cfabe1c116ac8ebd92a20451d53ffeff1ca13e6ea936d328cd91693e09f8aa
```

## 1.10

```
EXPOSE 5000
```

## 1.11

