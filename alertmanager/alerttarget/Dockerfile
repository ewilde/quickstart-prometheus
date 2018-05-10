FROM golang:1.10-alpine AS build-env

ENV SRCPATH $GOPATH/src/github.com/ewilde/alert-target
RUN apk update && apk add build-base
COPY ./ $SRCPATH
RUN go install github.com/ewilde/alert-target

FROM alpine

ENV BUILD_TAGS=latest
WORKDIR /app
COPY --from=build-env /go/bin/alert-target /app/
EXPOSE 5001
ENTRYPOINT ["/app/alert-target"]