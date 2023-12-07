## BEM VINDO A DOCUMENTAÇÃO PESSOAL REFERENTE AO EXPRESS.JS

# Nesta documentação vou falar do setup do express com typescript (se for usar o js normal não precisa instalar algumas coisas que explicitarei);

## _SETUP INICIAL_

### PRECISAMOS INSTALAR AS DEPENDENCIAS DE DESENVOLVIMENTO NECESSARIAS QUEN SÃO ELAS:

### _npm i -D typescript @types/node @types/express_

### DEPENDENCIAS OBRIGATORIAS PARA TRABALHAR COM O EXPRESS

### _npm i express cors_

## após a instalação voce so precisa utilizar a arquitetura abaixo:

## O template inicial para a utilização do express basicamente é essa!

import express, { Request, Result } from "express"; import cors from "cors";

const app = express();

app.use(express.json()); app.use(cors);

app.get("/hello", (request: Request, response: Response) => {
response.status(200).send("Hello World!"); })
