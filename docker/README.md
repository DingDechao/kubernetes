## Check docker is installed
```
docker version
Client:
 Cloud integration: v1.0.35+desktop.10
 Version:           25.0.3
 API version:       1.44
 Go version:        go1.21.6
 Git commit:        4debf41
 Built:             Tue Feb  6 21:13:26 2024
 OS/Arch:           darwin/arm64
 Context:           desktop-linux

Server: Docker Desktop 4.27.2 (137060)
 Engine:
  Version:          25.0.3
  API version:      1.44 (minimum version 1.24)
  Go version:       go1.21.6
  Git commit:       f417435
  Built:            Tue Feb  6 21:14:22 2024
  OS/Arch:          linux/arm64
  Experimental:     false
 containerd:
  Version:          1.6.28
  GitCommit:        ae07eda36dd25f8a1b98dfbf587313b99c0190bb
 runc:
  Version:          1.1.12
  GitCommit:        v1.1.12-0-g51d5e94
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0

docker --version
Docker version 25.0.3, build 4debf41

docker-compose --version
Docker Compose version v2.24.5-desktop.1
```

##
```
docker run -d -p 80:80 --name webserver nginx
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
f546e941f15b: Pull complete
2d258780861a: Pull complete
a7d6e9feb830: Pull complete
42e0f9421c7a: Pull complete
14a95f763a2f: Pull complete
164c21b63fde: Pull complete
5b452a5fd809: Pull complete
Digest: sha256:c26ae7472d624ba1fafd296e73cecc4f93f853088e6a9c13c0d52f6ca5865107
Status: Downloaded newer image for nginx:latest
7e08ea51d7c5a8c708adc818605b2a50d1ea9f8f543d8699d4fa81e7d6debad3
```

```
 docker ps
 
 CONTAINER ID   IMAGE     COMMAND                   CREATED          STATUS          PORTS                NAMES
7e08ea51d7c5   nginx     "/docker-entrypoint.…"   23 seconds ago   Up 22 seconds   0.0.0.0:80->80/tcp   webserver

Open url : http://0.0.0.0/
Welcome to nginx!
If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

For online documentation and support please refer to nginx.org.
Commercial support is available at nginx.com.

Thank you for using nginx.
```

## Docker pull
```
docker [image] pull NAME[:TAG]

NAME : Image repo name
TAG : Image's tag

docker pull ubuntu:18.04
18.04: Pulling from library/ubuntu
064a9bb4736d: Pull complete
Digest: sha256:152dc042452c496007f07ca9127571cb9c29697f42acbfad72324b2bb2e43c98
Status: Downloaded newer image for ubuntu:18.04
docker.io/library/ubuntu:18.04

What's Next?
  1. Sign in to your Docker account → docker login
  2. View a summary of image vulnerabilities and recommendations → docker scout quickview ubuntu:18.04
  
docker pull registry.hub.docker.com/ubuntu:18.04

docker run -it ubuntu:18.04 bash
root@35a265056994:/# echo "Hello World"
Hello World
root@35a265056994:/# exit
exit  

```

## docker images or docker image ls
```
docker images
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
nginx        latest    760b7cbba31e   10 days ago    192MB
ubuntu       18.04     d1a528908992   9 months ago   56.7MB

docker image ls
REPOSITORY   TAG       IMAGE ID       CREATED        SIZE
nginx        latest    760b7cbba31e   10 days ago    192MB
ubuntu       18.04     d1a528908992   9 months ago   56.7MB
```

## docker inspect
```
docker [image] inspect ubuntu:18.04
docker  inspect ubuntu:18.04
[
    {
        "Id": "sha256:d1a528908992e9b5bcff8329a22de1749007d0eeeccb93ab85dd5a822b8d46a0",
        "RepoTags": [
            "ubuntu:18.04"
        ],
        "RepoDigests": [
            "ubuntu@sha256:152dc042452c496007f07ca9127571cb9c29697f42acbfad72324b2bb2e43c98"
        ],
        "Parent": "",
        "Comment": "",
        "Created": "2023-05-30T09:39:10.501607889Z",
        "Container": "cfcab231b973ad2c5360326261cdee41a46da2ca56f8bf81a944c56ced8b9781",
        "ContainerConfig": {
            "Hostname": "cfcab231b973",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/sh",
                "-c",
                "#(nop) ",
                "CMD [\"/bin/bash\"]"
            ],
            "Image": "sha256:483413ae33b16734d5b0df37452ffabea713aed7af2715ddc31bdae5f713f7c6",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.opencontainers.image.ref.name": "ubuntu",
                "org.opencontainers.image.version": "18.04"
            }
        },
        "DockerVersion": "20.10.21",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/bash"
            ],
            "Image": "sha256:483413ae33b16734d5b0df37452ffabea713aed7af2715ddc31bdae5f713f7c6",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.opencontainers.image.ref.name": "ubuntu",
                "org.opencontainers.image.version": "18.04"
            }
        },
        "Architecture": "arm64",
        "Variant": "v8",
        "Os": "linux",
        "Size": 56661781,
        "GraphDriver": {
            "Data": {
                "MergedDir": "/var/lib/docker/overlay2/cdd2b852c34c15b70f8dd4def8d920eb129690ccd6fee56195a7d9e9619c8f29/merged",
                "UpperDir": "/var/lib/docker/overlay2/cdd2b852c34c15b70f8dd4def8d920eb129690ccd6fee56195a7d9e9619c8f29/diff",
                "WorkDir": "/var/lib/docker/overlay2/cdd2b852c34c15b70f8dd4def8d920eb129690ccd6fee56195a7d9e9619c8f29/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:c09969dbc5e84ea45848232c61ee613e2283d20a03d72bb98bc819d2fbeb3218"
            ]
        },
        "Metadata": {
            "LastTagTime": "0001-01-01T00:00:00Z"
        }
    }
]

 docker  inspect -f {{".Architecture"}} ubuntu:18.04
 arm64

```

## docker history
```
docker history ubuntu:18.04
IMAGE          CREATED        CREATED BY                                       SIZE      COMMENT
d1a528908992   9 months ago   /bin/sh -c #(nop)  CMD ["/bin/bash"]             0B
<missing>      9 months ago   /bin/sh -c #(nop) ADD file:f56078e320535ad36…   56.7MB
<missing>      9 months ago   /bin/sh -c #(nop)  LABEL org.opencontainers.…   0B
<missing>      9 months ago   /bin/sh -c #(nop)  LABEL org.opencontainers.…   0B
<missing>      9 months ago   /bin/sh -c #(nop)  ARG LAUNCHPAD_BUILD_ARCH      0B
<missing>      9 months ago   /bin/sh -c #(nop)  ARG RELEASE                   0B
```

## docker search
```
docker search [option] keyword

docker search --filter=is-official=true nginx
NAME      DESCRIPTION                                      STARS     OFFICIAL
nginx     Official build of Nginx.                         19641     [OK]
unit      Official build of NGINX Unit: Universal Web …   21        [OK]

docker search --filter=stars=4 tensorflow
NAME                             DESCRIPTION                                      STARS     OFFICIAL
tensorflow/tensorflow            Official Docker images for the machine learn…   2285
tensorflow/serving               Official images for TensorFlow Serving (http…   138
tensorflow/build                 Containers for building TensorFlow, provided…   7
bitnami/tensorflow-serving       Bitnami Docker Image for TensorFlow Serving      33
tensorflow/tfx                                                                    8
tensorflow/tf_grpc_test_server   Testing server for GRPC-based distributed ru…   4
jupyter/tensorflow-notebook      Scientific Jupyter Notebook Python Stack w/ …   362
tensorflow/syntaxnet             Official docker images for running DRAGNN/Sy…   13
tensorflow/magenta               Official Docker images for Magenta (https://…   19
tensorflow/tf_grpc_server        Server for TensorFlow GRPC Distributed Runti…   8
opensciencegrid/tensorflow-gpu   TensorFlow GPU set up for OSG                    12
rocker/tensorflow                Tensorflow & Keras libraries for machine lea…   4

```

## docker rm
```
docker rmi or docker image rm
docker rmi IMAGE [image...]
docker rmi myubuntu:latest
```

## docker prune
```
docker image prune -f
Total reclaimed space: 0B
```

## create image