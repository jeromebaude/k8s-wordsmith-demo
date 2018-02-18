# BUILD
FROM golang:1.9.1-alpine3.6 as builder

COPY dispatcher.go .
RUN go build dispatcher.go

# RUN
FROM alpine:edge
ENV API_HOST=api
ENV API_PORT=8080
ENV BIND_HTTP_PORT=80
ENV BIND_HTTP_HOST=0.0.0.0
EXPOSE 80
CMD ["/dispatcher"]

COPY --from=builder /go/dispatcher /
COPY static /static/
