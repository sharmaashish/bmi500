# Outline
* Install Docker (based on your operating system)

https://docs.docker.com/install/linux/docker-ce/centos/ 

* Run the Docker Hello world Example

$ docker run hello-world

More details - https://docs.docker.com/install/linux/linux-postinstall/#manage-docker-as-a-non-root-user

* Create Image with Python and your average container from #4.

* Put image on DockerHub

* Get the container uploaded by the person next to you.

* Docker run the container from #4.2.

* Create a dockerfile

```
FROM python:3

ADD distros.py /
COPY distros.json /
RUN pip install tornado

CMD [ "python", "distros.py" ]
```

Save the above text as Dockerfile (in the same folder as the previous exercise Python code).

* Build from the Docker directory

$ docker build -t mydockerimage:1.0.0 .

Sending build context to Docker daemon  9.216kB
Step 1/5 : FROM python:3
3: Pulling from library/python
05d1a5232b46: Pull complete
5cee356eda6b: Pull complete
89d3385f0fd3: Pull complete
80ae6b477848: Pull complete
28bdf9e584cc: Pull complete
523b203f62bd: Pull complete
e423ae9d5ac7: Pull complete
adc78e8180f7: Pull complete
5c4f0bc7295a: Pull complete
Digest: sha256:68dc1ce187dd2c32f4b237e44610d9f4f34add97f9c5c7c92268db14c77fb5c2
Status: Downloaded newer image for python:3
 ---> a9d071760c82
Step 2/5 : ADD distros.py /
 ---> d0018d212ba7
Removing intermediate container 31999451ef18
Step 3/5 : COPY distros.json /
 ---> 4c6585e8c11d
Removing intermediate container 54c0abd7b694
Step 4/5 : RUN pip install tornado
 ---> Running in 3d1e993a74e0
Collecting tornado
  Downloading https://files.pythonhosted.org/packages/e6/78/6e7b5af12c12bdf38ca9bfe863fcaf53dc10430a312d0324e76c1e5ca426/tornado-5.1.1.tar.gz (516kB)
Building wheels for collected packages: tornado
  Running setup.py bdist_wheel for tornado: started
  Running setup.py bdist_wheel for tornado: finished with status 'done'
  Stored in directory: /root/.cache/pip/wheels/6d/e1/ce/f4ee2fa420cc6b940123c64992b81047816d0a9fad6b879325
Successfully built tornado
Installing collected packages: tornado
Successfully installed tornado-5.1.1
 ---> 7704ee82271d
Removing intermediate container 3d1e993a74e0
Step 5/5 : CMD python distros.py
 ---> Running in 80ec5b96dcf3
 ---> 32580403e23d
Removing intermediate container 80ec5b96dcf3
Successfully built 32580403e23d
Successfully tagged MyDockerImage:1.0.0



* Confirm the images

$ docker image ls

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
MyDockerImage             1.0.0               32580403e23d        2 minutes ago       933MB
hello-world         latest              4ab4c602aa5e        2 weeks ago         1.84kB
python              3                   a9d071760c82        3 weeks ago         923MB

* Create account on hub.docker.com

Tag the image with the user name:

$ docker tag mydockerimage:1.0.0 yourhubusername/mydockerimage:1.0.0


* Log in and push the image to the Docker repository:

$ docker login --username=yourhubusername 

$ docker push yourhubusername/mydockerimage:1.0.0

The push refers to repository [docker.io/pradeeban/mydockerimage]
47a067f69600: Pushed
e889ceffa1a8: Pushed
18c8d1560302: Pushed
c9701db5aa5b: Mounted from library/python
590ee04d598a: Mounted from library/python
a62b97ef6d9f: Mounted from library/python
be59bd55864a: Mounted from library/python
a19cb627cc73: Mounted from library/python
ab016c9ea8f8: Mounted from library/python
2eb1c9bfc5ea: Mounted from library/python
0b703c74a09c: Mounted from library/python
b28ef0b6fef8: Mounted from library/python
1.0.0: digest: sha256:a668a1d1a1271d0f21972f0b0f0502c123a905a8f97fe98fc9d4f4bee91a25d6 size: 2843



* To get your docker container into another computer/host

$ docker run --name mycontainername -p host_port:container_port username/container_name:version

For example,

$ docker run --name mydockercontainer-1 -p  8888:8888 pradeeban/mydockerimage:1.0.0

* Now you can access the APIs as you were running the code previously on your computer, without going through all the steps from the last class.

http://localhost:8888/?oid=Debian
