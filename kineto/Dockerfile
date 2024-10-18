FROM golang:1.22 as build
WORKDIR /build
RUN git clone https://git.sr.ht/~sircmpwn/kineto
WORKDIR /build/kineto
RUN go mod download \
  && CGO_ENABLED=0 GOOS=linux go build -o kineto

FROM alpine:3.19
WORKDIR /app
COPY --from=build /build/kineto/kineto /app/kineto
ENTRYPOINT ["/app/kineto"]
