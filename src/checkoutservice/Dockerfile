# Copyright The OpenTelemetry Authors
# SPDX-License-Identifier: Apache-2.0


FROM golang:1.21.4-alpine AS builder
WORKDIR /usr/src/app/

COPY ./src/checkoutservice/ ./
RUN go get github.com/instana/go-sensor
RUN go build -o /go/bin/checkoutservice/

# -----------------------------------------------------------------------------

FROM alpine

WORKDIR /usr/src/app/

COPY --from=builder /go/bin/checkoutservice/ ./

EXPOSE ${CHECKOUT_SERVICE_PORT}
ENTRYPOINT [ "./checkoutservice" ]
