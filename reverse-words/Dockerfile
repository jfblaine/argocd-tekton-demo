# FROM golang:latest
FROM golang:1.15
WORKDIR /go/src/reverse-words/
COPY main.go .
RUN go get github.com/gorilla/mux && go get github.com/prometheus/client_golang/prometheus/promhttp
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main .

FROM scratch
COPY --from=0 /go/src/reverse-words/main .
EXPOSE 8080
CMD ["/main"]
