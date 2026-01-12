FROM golang:1.22 AS builder

ENV GOTOOLCHAIN=auto
ENV CGO_ENABLED=0
WORKDIR /src

COPY go-gfs /go-gfs
COPY simple-file-share/go.mod simple-file-share/go.sum /src/
COPY simple-file-share/backend /src/backend
COPY simple-file-share/frontend /src/frontend

RUN go build -o /out/sfs ./backend

FROM alpine:3.20

WORKDIR /app
COPY --from=builder /out/sfs /app/sfs
COPY --from=builder /src/frontend /app/frontend

EXPOSE 8080
CMD ["/app/sfs", "-static", "/app/frontend"]
