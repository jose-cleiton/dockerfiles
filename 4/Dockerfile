FROM golang:1.17 as build
WORKDIR /app

COPY go.mod ./

COPY main.go ./
RUN go build -o /main 



FROM gcr.io/distroless/base-debian10
WORKDIR  /
COPY --from=build /main /main

EXPOSE 8080

USER nonroot:nonroot

ENTRYPOINT ["/main"]