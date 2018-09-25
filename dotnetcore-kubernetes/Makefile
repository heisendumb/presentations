VERSION := "1.0.0"
MYAPP := "apicontagem"
SECRET_NAME := ""
RESOURCE_GROUP := ""
CLUSTER_NAME := ""
YOUR_MAIL := ""
CLIENT_ID := ""
CLIENT_SECRET := ""

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

k8sdash:
	az aks browse -g $(RESOURCE_GROUP) -n $(CLUSTER_NAME)

k8secret:
	kubectl create secret docker-registry $(SECRET_NAME) --docker-server= --docker-username $(CLIENT_ID) --docker-password $(CLIENT_SECRET) --docker-email $(YOUR_MAIL)