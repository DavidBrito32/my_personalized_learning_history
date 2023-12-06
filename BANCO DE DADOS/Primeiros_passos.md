**DEPOIS PRECISAMOS LOGAR NO MYSQL**

## |\_-> sudo mysql -u root -p

## CASO ENTRE DIRETO SEM PEDIR SENHA NO ROOT VOCÊ PRECISA DEFINIR UMA NOVA SENHA PARA O ROOT (SENHA MUITO SEGURA PARA EVITAR INVASÕES AO SEU BANCO DE DADOS COM OS PODERES DO ROOT)

## |\_-> use mysql

## |\_-> UPDATE USER SET PLUGIN='' WHERE USER='root';

## |\_-> FLUSH PRIVILEGES;

## |\_-> (QUIT) PARA SAIR;

# - - - - - - - - - - - - - - - - - - - - - - - - - - - - #

# CASO TENHA ACABADO DE INSTALAR PELA PRIMEIRA VEZ: USE ESSE PASSO A PASSO;

## |\_-> SUDO mysql secure_installation

### APOS O COMANDO DE CIMA O TERMINAL VAI LHE FAZER ALGUMAS PERGUNTAS SO RESPONDER;

# - - - - - - - - - - - - - - - - - - - - - - - - - - - -

# PARA CRIAR UM USUARIO:

|\_-> CREATE USER IF NOT EXISTS '<user>'@'localhost' IDENTIFIED BY '<SUA SENHA DE NOVO USUARIO>'

# PARA FORNECER AS PERMIÇÕES DO USUARIO CRIADO USE:

|\_-> GRANT ALL PRIVILEGES ON <nome do banco.\*> TO <USER>@localhost;

## |\_-> OU PARA DEFINIR PERMISSAO A TODOS OS BANCOS DE DADOS USE:

 |\_-> GRANT ALL PRIVILEGES ON _._ TO '<USER>'@'localhost' IDENTIFIED BY 'SENHA DO USER' WITH GRANT OPTION;

|\_-> FLUSH PRIVILEGES; (ATUALIZAR AS PERMISSOES);

### PARA ACESSAR USANDO O NOVO USUARIO CRIADO USE:

#### |\_-> mysql -u <user> -p;

#### |\_-> FORNECER A SENHA DEFINIDA DO REFERIDO USUARIO:

# PARA LISTAR OS BANCOS DE DADOS ESTANDO NA RAIZ DO DB USE:

## |\_-> SHOW DATABASES;

# PARA CRIAR UM BANCO DE DADOS:

## |\_-> **CREATE DATABASE <NOME DO BANCO>**

    |_->PARA TER CERTEZA QUE O BANCO FOI CRIADO USE:
        |_-> SHOW DATABASE;
            |_-> UMA TELA IGUAL A DE BAIXO DEVE APARECER:
                    +--------------------+
                    | Database           |
                    +--------------------+
                    | <NOME DO BANCO>    |
                    | <NOME DO BANCO>    |
                    | <NOME DO BANCO>    |
                    | <NOME DO BANCO>    |
                    | <NOME DO BANCO>    |
                    +--------------------+

# PARA ENTRAR EM UM BANCO DE DADOS USE:

## |\_-> **USE <NOME-DO-BANCO>**

![Alt text](image.png); |_-> NOTE QUE NO FINAL DA LINHA TEM: |_-> MariaDB
[(none)]> O (none) -> é por que nao tem nenhum banco selecionado |\_-> Quando
Selecionamos algum banco o none vira o nome do banco

# PARA VER AS TABELAS DENTRO DE UM BANCO DE DADOS:

## |\_-> USE O SEGUINTE COMANDO:

|_-> **SHOW TABLES** |_-> UMA TELA IGUAL A ESSA DEVERÁ APARECER:
![Alt text](image-1.png); |\_-> SE VOCÊ TIVER CRIADO O BANCO AGORA O NOME EMPTY
DEVERA APARECER ASSIM: Empty set (0,000 sec) - - - > INDICANDO QUE O BANCO NÃO
POSSUI NENHUMA TABELA CRIADA

#PARA CRIAR TABELAS NO SEU BANCO DE DADOS USE:

## |\_-> **CREATE TABLE IF NOT EXISTIS <NOME-DA-TABELA>** - - -> **(IF NOT EXISTIS)** SIGNIFICA QUE SE NÃO EXISTIR ELE CRIE UMA TABELA COM O NOME INDICADO

## |\_-> **CREATE TABLE IF NOT EXISTIS <NOME-DA-TABELA>(
    id (TIPO DE DADO) NOT NULL AUTO_INCREMENT,
    campo2 DATE,
    qualquer VARCHAR(10) NOT NULL,
    CONSTRAINT id_pk PRIMARY KEY (id)
    DEFINIÇÃO DA CHAVE PRIMARIA
    CONTRAINT SIGNIFICA AS RESTRIÇÕES DE INTEGRIDADE DO BANCO DE DADOS;

);


## PARA VISUALIZAR OS CAMPOS CRIADOS DENTRO DA TABELA USE:
## |_-> SHOW COLUMNS FROM <table_name>



### PARA EXCLUIR ALGUMA TABELA USE:

#### |\_-> DROP TABLE <nome-da-tabela>;

# - - - - - - - - - - - - - - - - - - - - - - - - - - - - #

# **mysql / mariaDB** Primeiros Passos -

### INSTALAÇÃO DO MARIADB (MYSQL) (LINUX DEBIAN);

**Passo A passo Terminal**

## |\_-> **sudo apt install mariadb-server -y**

# - - - - - - - - - - - - - - - - - - - - - - - - - - - - #

# SEMPRE UTILIZAR PONTO E VIRGULA NO FINAL DAS EXPRESSÕES






## AULA 

### 1º -> SHOW DATABASES; (SERVE PARA VER OS BANCOS DE DADOS JA EXISTENTES NO CLIENT)

### 2º -> CREATE DATABASE IF NOT EXISTIS <Nome-do-Banco>; 
                      |_-> SERVE PARA CASO NÃO EXISTA, CRIE O BANCO COM O    NOME REFERIDO;

### 3º -> DROP DATABASE <Nome-do-Banco>; (SERVE PARA DELETAR UM DATABASE)

### 4º -> USE <Nome-Do-Banco>; (Serve para usar o banco);

### 5º -> CREATE TABLE IF NOT EXISTIS <Nome-Da-Tabela>(
    user_id <TIPO> NOT NULL AUTO_INCREMENT,
    user_NAME <TIPO<VARCHAR(50)>> NOT NULL,
    user_email <TIPO<VARCHAR(50)>> NOT NULL,
    PRIMARY KEY (user_id)
);


### 6º -> SELECT * FROM user;


### 6º (a) -> SELECT user_id, user_name FROM <tabela>;

### 7º -> INSERT INTO user (COLUNAS) VALUES (VALORES)
                         |_-> COLOCAR TODAS AS COLUNAS OBRIGATORIAS, PARA CADA COLUNA COLOCAR A MESMA QUANTIDADE RESPECTIVA DE VALORES A SEREM INSERIDOS;

### 8º -> SELECT * FROM user WHERE name LIKE '%<PARAMETRO>%';

### 9º -> ALTER TABLE <user> MODIFY email varchar(50) UNIQUE <pode colocar dentro da tabela na hora da criação> DEFINE QUE ESTE CAMPO NÃO PODERÁ SE REPETIR;