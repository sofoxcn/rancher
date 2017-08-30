FROM redis:3.2.10-alpine

# add our user and group first to make sure their IDs get assigned consistently, regardless of whatever dependencies get added
#RUN addgroup -S redis && adduser -S -G redis redis

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories
RUN apk update

# grab su-exec for easy step-down from root
RUN apk add --no-cache 'su-exec>=0.2'
COPY redis-trib.rb /usr/local/bin
 
RUN apk add --no-cache \
	ruby \
	ruby-irb \
	ruby-rdoc \
	ruby-bundler \
	curl	\
	bash	

RUN gem sources --remove https://rubygems.org/; \
	gem sources -a https://gems.ruby-china.org/; \
	gem install redis

RUN mkdir /data 
VOLUME /data
WORKDIR /data

COPY redis-trib.rb /usr/local/bin/
 
# Add config file
ADD conf/redis.conf /etc/redis.conf
CMD [ "redis-server", "/etc/redis.conf" ]

EXPOSE 6379
EXPOSE 16379

