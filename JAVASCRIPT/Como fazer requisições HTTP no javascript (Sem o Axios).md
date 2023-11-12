
REQUISIÇÕES HTTP JAVASCRIPT ( <strong> SEM O AXIOS</strong>).

No javascript a gente tem um metodo nativo que possibilita a integração com as API'S.

o metodo é o fetch(). (Como Usar)?

        ==> O Fetch sozinho:
            ==> fetch('LINK-DA-API')
                .then(resoponse => resoponse.json()) -> Aqui a gente recebe a resoponse(resposta) e o transforma em objeto novamente
                .then(resoponse => {
                    //Função
                }) -> Aqui você desenvolve sua função com os dados
                .catch((erro) => {
                    console.log(erro.response)
                })
            
            
            ==> fetch('LINK-DA-API',{
                headers: {
                    "content-type": "application/json",
                    "Authorization": "CHAVE" - - - - - - - - - - > (Não é toda api que pede esta chave, porem se pedir, é dentro do header que vai)
                },
                body{
                    //PODE SER UM OBJETO ou string Enfim.....
                }
            })