

### Setting up microservice application 

setting up mongodb with docker

creating folder structure for applcation


prometheus.Handler() is depricated thus use below command

// http.Handle("/metrics", prometheus.Handler())
	http.Handle("/matric", promhttp.Handler())


graphana 
sudo chown -R aachi:aachi (mount) dir location

- ./metrics/grafana/mount:/var/lib/grafana


git pull --rebase origin master


### Setting up passwordless git

http://infoheap.com/how-to-setup-password-less-git-push-for-github/
http://infoheap.com/ssh-keygen-create-public-private-key-pair/


git config  remote.origin.url git+ssh://git@github.com/aachigolang/postapp.git

### Push to github

git pull --rebase origin master

https://github.com/anabiozz/lapkins-api/tree/master

