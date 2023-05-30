#!/bin/sh

.PHONY: ngxquic-base
ngxquic-base: ## Build ngxquic docker image
	@docker build --network=host \
		-t chao123/ngxquic-base:latest .

.PHONY: help
help: ## Show this help menu.
	@grep -E '^[a-zA-Z1-9_%-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'
