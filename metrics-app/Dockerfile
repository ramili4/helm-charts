FROM golang:1.21-alpine as builder

WORKDIR /app
COPY main.go .
COPY go.mod .

RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -o metrics-app

FROM alpine:3.18
WORKDIR /app
COPY --from=builder /app/metrics-app .

EXPOSE 8080
CMD ["./metrics-app"]