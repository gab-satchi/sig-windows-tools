FROM golang:1.13 as builder

# Copy in the go src
WORKDIR /wins-controller
COPY vendor/ vendor/
COPY main.go main.go
COPY webhook.go webhook.go
COPY go.mod .

# Build
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 GO111MODULE=on go build -mod vendor -a -o controller

# Use distroless as minimal base image to package the manager binary
# Refer to https://github.com/GoogleContainerTools/distroless for more details
FROM alpine:latest
WORKDIR /
COPY --from=builder /wins-controller/controller .

ENTRYPOINT ["/controller"]
