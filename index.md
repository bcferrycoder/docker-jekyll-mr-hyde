---
layout: default
title: BCFerryCoder
tagline: The Foundation for Innovation
---

Welcome to John Wetherill's resume, provided as a dockerfile which I
built during a recent flight from Canada. Click the tabs above for 
content.


Here's the Dockerfile

    # My resume as a Dockerfile
    
    # docker build -t="jdw/docket" .
    # docker run -p 3000:3000 -d jdw/docket
    # now visit at http://host:3000/

    FROM ubuntu:12.10
    MAINTAINER John Wetherill, jdw@bcferrycoder.com
    
    RUN apt-get update
    
    ## GIT
    RUN apt-get install -y git-core
    
    ## RUBY AND MARKDOWN
    RUN apt-get install -y -q ruby1.9.1 ruby1.9.1-dev rubygems1.9.1 irb1.9.1 build-essential libopenssl-ruby1.9.1 libssl-dev zlib1g-dev markdown
    
    ## JEKYLL
    RUN gem install jekyll --no-ri --no-rdoc
    
    ## CONTENT
    RUN git clone https://github.com/bcferrycoder/bcferrycoder.github.com.git /jdwdocket
    
    EXPOSE 3000

    ENTRYPOINT jekyll -w serve --port 3000 --source /jdwdocket
