FROM centos:latest

# SCMs for "go get", gcc for cgo
RUN yum check-update && yum install -y \
		ca-certificates curl gcc glibc-dev make \
		bzr git mercurial \
	&& yum clean all

ENV GOLANG_VERSION 1.3

RUN curl -sSL https://golang.org/dl/go$GOLANG_VERSION.src.tar.gz \
		| tar -v -C /usr/src -xz

RUN cd /usr/src/go/src && ./make.bash --no-clean 2>&1

ENV PATH /usr/src/go/bin:$PATH

RUN mkdir -p /go/src
ENV GOPATH /go
ENV PATH /go/bin:$PATH
WORKDIR /go

COPY go-wrapper /usr/local/bin/
