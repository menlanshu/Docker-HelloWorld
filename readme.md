# build docker image
docker built -t helloworld .

# run docker image
docker run -p 4000:80 helloworld

# tag docker image
docker tag dockerid menlans/helloworld

# push docker image
docker push menlans/helloworld

# test docker
docker run -p 4000:80 helloworld
-- check docker running list
docker ps
-- check docker running result
curl http://localhost:4000

# docker commit
when you do some change when docker is running
docker exec -it dockerid /bin/sh
=> after change some file
=> you can use docker commit to submit the latest docker image

# check docker actual pid
docker inspect --format '{{ .State.Pid }}' dockerid

# check actual namespace configuration
ls -l /proc/dockerPid/ns
-- a new process can be added to existing namespace
-- then the new process enter the docker, this is how docker exec realize

when you use docker, you can use --net to entoerh to another docker's network namespace``

# mount folder for docker
docker run -v /test => create a temp folder /var/lib/docker/volumes/[volume_id]/_data
docker run -v /home:/test

-- dockerinit after initialization use execv() make application process to be the PID=1 process`
**bind mount**

# check volume
docker run -d -v /test dockerid
docker volume ls
ls /var/lib/docker/volumes/51d191160a833d9b2eca1788f1428db9096e2f0be7062b515faf94df5feb7391/
> all files in volume will be saved in uphere fodler

