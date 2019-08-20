all: datacube-notebook

geo-base: Dockerfile.geo
	docker build -t $@ --file $< .

geo-jupyter: Dockerfile.geo-jupyter geo-base
	docker build -t $@ --file $< .
	docker build -t tbutzer/jupyter --file $< .
	docker push tbutzer/jupyter

datacube-notebook: Dockerfile.datacube geo-jupyter
	docker build -t $@ --file $< .

run:
	docker run -it -v /home/ubuntu:/home/jovyan -p 9999:8888 tbutzer/jupyter jupyter notebook --ip 0.0.0.0 --allow-root --NotebookApp.token='yaml'

bash:
	docker run -it -v /home/ubuntu:/home/jovyan -p 9999:8888 tbutzer/jupyter bash

.PHONY: all geo-jupyter geo-base datacube-notebook
