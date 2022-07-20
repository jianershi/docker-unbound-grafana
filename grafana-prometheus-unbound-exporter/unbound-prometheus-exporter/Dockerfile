FROM golang:latest

WORKDIR /app
RUN git clone https://github.com/letsencrypt/unbound_exporter.git /app
RUN go get -d ./...
ARG UNBOUND_CONTAINER_NAME
RUN sed -i "s/localhost/${UNBOUND_CONTAINER_NAME}/g" unbound_exporter.go
RUN CGO_ENABLED=0 GOOS=linux go build --ldflags '-extldflags "-static"' -o unbound_exporter
RUN strip unbound_exporter

FROM alpine:latest  
WORKDIR /root
COPY --from=0 /app/unbound_exporter .

EXPOSE 9167
CMD ["./unbound_exporter"]  

# COPY app.go .
# RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o app .
