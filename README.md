# Black Mirror

A small Go server for testing deployments. Its Docker image is less than 14 MB.

### Install

A Docker image is available on [Docker Hub](https://hub.docker.com/r/aodin/blackmirror/).

    docker pull aodin/blackmirror
    docker run -p 8080:8080 aodin/blackmirror

It was built and tagged with:

    docker build . -t aodin/blackmirror

The server can be built locally with [go](https://golang.org/):

    go build .


### Usage

The server will respond to a request for any method and path with the HTTP/1.1 wire format as a text/plain document.

Request:

    GET localhost:8080/yo

Response:

    GET /yo HTTP/1.1
    Host: localhost:8080
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
    Accept-Encoding: gzip, deflate, sdch
    Accept-Language: en-US,en;q=0.8
    Cache-Control: max-age=0
    Connection: keep-alive
    Upgrade-Insecure-Requests: 1
    User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/50.0.2661.102 Safari/537.36

It accepts `PORT` / `HOST` environment variables and `-port` / `-host` flags, with the flags taking precendence. Its default address is `:8080`.

    PORT=8081 HOST=0.0.0.0 go run blackmirror.go -port=8082 -host="localhost"

The server purposefully uses the `/vendor` directory to test Go 1.5+ vendoring.

Happy hacking!

aodin, 2018
