---
layout: default
title: Docker Jekyll
tagline: The Foundation for Innovation
---

This is Docker Jekyll

Here's the Dockerfile

    
	# docker build -t="johnw/docket" .
	# docker run -p 3000:3000 -d johnw/docket
	# now visit at http://host:3000/

	FROM ubuntu
	MAINTAINER John Wetherill, bcferrycoder@gmail.com

	RUN apt-get update

	## GIT
	RUN apt-get install -y git-core

	## NODE
	RUN apt-get install -y nodejs

	## RUBY AND MARKDOWN
	RUN apt-get install -y -q ruby1.9.1 ruby1.9.1-dev rubygems1.9.1 irb1.9.1 build-essential libopenssl-ruby1.9.1 libssl-dev zlib1g-dev markdown

	## JEKYLL
	RUN gem install jekyll --no-ri --no-rdoc
	RUN echo date

	## CONTENT
	RUN git clone https://github.com/bcferrycoder/docker-jekyll-mr-hyde /jekyll

	EXPOSE 3000

	ENTRYPOINT jekyll serve --host 0.0.0.0 --port 3000 --source /jekyll
