cat:
	cat ./Makefile

all: boot shared notebook cows

boot:
	./bootstrapTheHub.sh


services:
	./installServices.sh
	./installDocker.sh


cows:
	sudo apt-get install cowsay

shared:
	sudo mkdir -p /srv/data/code
	(cd /etc/skel && sudo ln -s /srv/data/code code)
	sudo cp files/* /srv/data/code

notebook:
	(cd /srv/data/; sudo git clone http://github.com/tonybutzer/notebook)
	(cd /etc/skel && sudo ln -s /srv/data/notebook notebook)


jupyter-ubuntu:
	sudo chown -R  jupyter-ubuntu:jupyter-ubuntu /srv/data/code
	sudo chown -R  jupyter-ubuntu:jupyter-ubuntu /srv/data/notebook


ubuntu:
	sudo cp -r files /home/jupyter-ubuntu
	sudo chown jupyter-ubuntu:jupyter-ubuntu -R /home/jupyter-ubuntu


git:
	(cd /opt/notebook && make)

