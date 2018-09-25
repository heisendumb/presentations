VERSION := "1.0.0"
MYAPP := "apicontagem"

all: compose

build:
	docker build --compress --force-rm -t $(MYAPP):$(VERSION) .

run: build
	docker run -d -p 80:80 --name $(MYAPP) $(MYAPP):$(VERSION)

compose:
	docker-compose up -d --build

tag:
	docker tag $(MYAPP):$(VERSION) [azure-container-registry-name].azurecr.io/$(MYAPP)

push: tag
	docker push [azure-container-registry-name].azurecr.io/${MYAPP}