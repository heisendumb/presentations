VERSION := "1.0.0"
MYAPP := "apicontagem"

all: run

build:
	docker build --compress --force-rm -t $(MYAPP):$(VERSION) .

run: build
	docker run -d -p 80:80 --name $(MYAPP) $(MYAPP):$(VERSION)