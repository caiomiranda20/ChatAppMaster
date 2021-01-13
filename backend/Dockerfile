#Imagem
FROM golang:alpine

#Variáveis de ambiente necessárias para imagem
ENV GO111MODULE=on \
    CGO_ENABLED=0 \
    GOOS=linux \
    GOARCH=amd64

#Mover para o diretório de trabalho
WORKDIR /build

#Copiar e baixar as depêndencias
COPY go.mod .
COPY go.sum .

RUN go mod download
RUN go get -d -v ./...
RUN go install -v ./...
RUN go get golang.org/x/net/html
RUN go get github.com/gorilla/websocket
RUN go get github.com/go-redis/redis

#Copiar para o contâiner
COPY . .

#Executar o APP
RUN go build -o main .

# Mover para a pasta binária
WORKDIR /dist

#Copiar o binário para a pasta
RUN cp /build/main .

#Expondo a porta do contâiner
EXPOSE 8080

#Comando a ser executado após iniciar contâiner
CMD ["/dist/main"]
