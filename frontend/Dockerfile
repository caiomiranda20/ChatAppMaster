#Imagem
FROM node:13-alpine

#Diretório de trabalho
WORKDIR /app

#Copiar para o contâiner
COPY . .

#Adicionando "/app/node_modules/.bin" para o PATH
ENV PATH /app/node_modules/.bin:$PATH

#Instalando dependências
COPY package.json /app/package.json

RUN npm install
RUN npm install react-scripts@3.3.1 -g

#Expondo a porta do contâiner
EXPOSE 3000

#Comando a ser executado após iniciar contâiner
CMD ["npm", "start"]
