# Stage 1

FROM golang:1.24.9-alpine3.22 AS builder

WORKDIR /myapp

COPY ./cmd/api/main.go .
COPY ./go.mod .

RUN go mod tidy

RUN go build -o appapi /myapp/main.go

# Stage 2

FROM alpine:3.22

WORKDIR /myapp

COPY --from=builder /myapp/appapi .

CMD [ "/myapp/appapi" ]