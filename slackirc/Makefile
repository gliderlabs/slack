.PHONY: build deploy

build:
	docker build -t gliderlabs/slack-irc .

push:
	docker push gliderlabs/slack-irc
	
deploy:
	kubectl apply --namespace gliderlabs -f slack-irc.yaml
