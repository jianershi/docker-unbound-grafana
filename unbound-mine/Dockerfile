FROM alpine:latest

WORKDIR /app
RUN apk add --no-cache g++ make openssl openssl-dev expat-dev libevent-dev
RUN wget https://nlnetlabs.nl/downloads/unbound/unbound-latest.tar.gz
RUN mkdir unbound-latest
RUN tar zxf unbound-latest.tar.gz --strip-components 1 -C unbound-latest

WORKDIR /app/unbound-latest
RUN ./configure \
	--prefix= \
	--with-username=unbound \
	--with-libevent \
	--with-ssl \
	--with-pthreads
RUN make -j

EXPOSE 53
EXPOSE 8953

VOLUME /etc/unbound
CMD ["./unbound","-c","/etc/unbound/unbound.conf"]
