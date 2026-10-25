FROM golang:1.27

WORKDIR /usr/src/app


ENV PATH="/usr/local/go/bin:${PATH}"
COPY . .
RUN go build -o server .

ENV PORT=8080
ENV REQUEST_ORIGIN=http://localhost:8080
EXPOSE 8080
CMD [ "./server" ]