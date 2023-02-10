FROM --platform=$BUILDPLATFORM golang:1.19.3-alpine3.15 as BUILDER

COPY cmd/helloworld /helloworld
RUN ls /
RUN cd /helloworld \
  && GOARCH=${TARGETARCH} go build -o /usr/local/bin/helloworld . \
  && chmod +x /usr/local/bin/helloworld

FROM alpine:3.15

COPY --from=BUILDER /usr/local/bin/helloworld /usr/local/bin/

ENTRYPOINT ["helloworld"]
