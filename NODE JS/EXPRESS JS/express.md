## BEM VINDO A DOCUMENTAÇÃO PESSOAL REFERENTE AO EXPRESS.JS

# Nesta documentação vou falar do setup do express com typescript (se for usar o js normal não precisa instalar algumas coisas que explicitarei);

## *SETUP INICIAL*

### PRECISAMOS INSTALAR AS DEPENDENCIAS DE DESENVOLVIMENTO NECESSARIAS QUEN SÃO ELAS:
### *npm i -D typescript @types/node @types/express*

### DEPENDENCIAS OBRIGATORIAS PARA TRABALHAR COM O EXPRESS
### *npm i express cors*

## após a instalação voce so precisa utilizar a arquitetura abaixo:

## O template inicial para a utilização do express basicamente é essa!

import express, { Request, Result } from "express";
import cors from "cors";

const app = express();

app.use(cors);

app.get("/hello", (request: Request, response: Response) => {
    response.status(200).send("Hello World!");
})