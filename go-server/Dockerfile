FROM golang:latest AS builder
ADD . src/github.com/imazik/hacktoberfest-demo/go-server
WORKDIR src/github.com/imazik/hacktoberfest-demo/go-server
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -a -o /main .

# final stage
FROM alpine:latest
RUN apk --no-cache add ca-certificates
COPY --from=builder /main ./
RUN chmod +x ./main
ENTRYPOINT ["./main"]
EXPOSE 8003
