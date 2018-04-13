# https://hub.docker.com/_/golang/

FROM golang:alpine
RUN apk add --no-cache ca-certificates
# gcc for cgo
# Install git in order to run "go get"
RUN apk update && \
    apk upgrade && \
    apk add git

WORKDIR /go/src/app
# Copy the local package files to the container's workspace.
COPY . .

# In order to run the application, you need one dependency: "github.com/lib/pq".
RUN go get -d -v ./...
RUN go install -v ./...

CMD ["app"]

# Document that the service listens on port 8080.
EXPOSE 8080
