#!/bin/sh

ncore:=24
nginx_etc:=$(nginx_etc)
docker_tag:=latest
docker_file:=Dockerfile_latest

.PHONY: ngxquic-perf
ngxquic-perf: ## Run builder for producing ngxquic-image
	@docker run --rm \
		-v $(nginx_etc):/root/nginx_etc \
		-v /var/cache/nginx/ramcache:/var/cache/nginx/ramcache \
		--network=host \
		--cpus=$(ncore) \
		chao123/ngxquic:${docker_tag} 

.PHONY: ngxquic-builder
ngxquic-builder: ## Build ngxquic docker image
	@docker build \
		-f ${docker_file} \
		--network=host \
		--build-arg http_proxy=${HTTP_PROXY} \
		-t chao123/ngxquic:${docker_tag} .

.PHONY: init ## Build ngxquic-builder and ngxquic image
init:ngxquic-build ngxquic-image

.PHONY: ngxquic-sh
ngxquic-sh: ## run ngxquic and shell in this container
	@docker run --rm \
		--privileged \
		-v $(nginx_etc):/root/nginx_etc \
		-v /var/cache/nginx/ramcache:/var/cache/nginx/ramcache \
		--network=host \
		--cpus=$(ncore) \
		-it \
		chao123/ngxquic:${docker_tag}

.PHONY: ngxquic-exp-img
ngxquic-exp-img: ## export docker image
	@docker save chao123/ngxquic:${docker_tag} > ngxquic_${docker_tag}.tar

.PHONY: help
help: ## Show this help menu.
	@grep -E '^[a-zA-Z1-9_%-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'
