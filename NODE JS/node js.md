# *Fundamentos do Node.js*

# Ja passei pelas explicações mais básicas;

## MODULO NODE_CORE

### |\_-> **MODULO HTTP** (NODE PURO)

# |\_-> Podemos criar um servidor HTTP com este modulo, ou seja, receber uma requisição e enviar codigo HTML como resposta, por exemplo; 
##                    -> Vamos utilizar alguns metodos, como createServer, para criação do servidor;
###                        -> E tambem listen, para determinar a porta;
####                           -> Veja como Funciona na pratica abaixo:

# ****************************************************************************************************************


const http = require("http");
                |_------\--->  O require HTTP basicamente solicita aos modulos internos do node.js o modulo http
                atribuindo o modulo diretamente a variavel (http)

----------------------------------------------------------

const port = 3000;
|\_-> Serve somente para atribuir a porta que queremos rodaar o servidor

----------------------------------------------------------

const server = http.createServer((req, res)=> {
    res.write("Oi HTTP");
    res.end();
})

|\_-> O metodo que cria o servidor é o createServer onde por sua vez recebe uma função anonima que tem dois parametros, o req e o res

|\_-> Outro metodo do create server e o res.end(); -> basicamente encerra o servidor

----------------------------------------------------------

server.listen(port, () => {
    console.log(`Servidor rodando na porta ${port}`);
})

|\_-> Este metodo fica responsavel por receber a requisição externa



----> para rodar este script basta utilizar o comando node (nome_do_arquivo.js);

ai o serviço ira rodar na porta escolhida 
----------------------------------------------------------


## Retornando HTML com o modulo http;

const http = require("http");

const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200; //Serve como o status da requisicao indicando sucesso;

  res.setHeader("content-type", "text-html"); // como se fosse o cabeçalho dos headers da requisicao

  res.end("<h1>Ola, estou enviando html atravez do node.js</h1><p style='color: red;'>Testando a atualizacao</p>")

  dentro do metodo end a gente coloca o que queremos passar
});

server.listen(port, () => {
  console.log(`Servidor rodando na porta ${port}`);
});