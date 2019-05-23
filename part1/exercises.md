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

# 1.4

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

