# VxTel - FaleMais
## _Adquira já seu plano_

FaleMias da VxTel é o produto onde o cliente adquire um plano e pode falar de graça até um determinado tempo, pagando apenas os minutos excedentes.


## Regras de negócio:

- O tempo de cada plano é contado em minutos
- Cada minuto excedente tem um acréscimo de 10% sobre a tarifa normal do minuto
- Planos:
    - FaleMais30 - 30 minutos
    - FaleMais60 - 60 minutos
    - FaleMais30 - 120 minutos
- O custo inicial de aquisição do plano deve ser desconsiderado para este
problema


## Requisitos Funcionais:
- RF01: Dispobibilizar uma plataforma web com a simulação de um plano
- RF02: O cliente pode escolher o código de origem. O código de origem é o DDD.
- RF03: O cliente pode escolher o código de destino. O código de destino é o DDD.
- RF04: O cliente pode escolher o tempo da ligação, em minutos.  
- RF05: O cliente pode escolher o plano FaleMais, de acordo com os planos disponibilizados acima
- RF06: O sistema deve retornar o valor da ligação com o plano
- RF07: O sistema deve retornar o valor da ligação sem o plano

Exemplo de valores:

| Origem  |  Destino  | Tempo   | Plano FaleMais | Com FaleMais | Sem FaleMais |
| ------- | --------- | -----   | -------------- | ------------ | ------------ |
| 011     | 016       | 20      | FaleMais 30    | $ 0,00       |    $ 38,00   |
| 011     | 017       | 80      | FaleMais 60    | $ 37,40      |    $ 136,00  |
| 018     | 011       | 200     | FaleMais 120   | $ 167,20     |    $ 380,00  |
| 018     | 017       | 100     | FaleMais 30    |      -       |       -      |


## Funcionalidades

- Cálculo do valor da ligação usando um plano;
- Cálculo do valor da ligação sem usar um plano;

## Tecnologias

FaleMais usa as seguintes tecnologias:

Backend:
- [C#](https://docs.microsoft.com/pt-br/dotnet/csharp/) - Linguagem de programação utilizada para desenvolvimento do módulo backend
- [DotNet](https://dotnet.microsoft.com/) - Framewwork utilizado para auxiliar no desenvolvimento do módulo backend
- [Docker](https://www.docker.com/) - Tecnologia utilizada para a entrega da aplicação
- [Swagger](https://swagger.io/) - Para documentar e testar a api
- [xUnit](https://xunit.net/) - Para testes unitários


## Instalação

#### package



#### Docker
- Use o arquivo dockerfile na raiz do projeto e gere uma imagem, exemplo de comandos:
        
        docker build . -- tag repositorio/nome-da-imagem
        docker push tag repositorio/nome-da-imagem
        docker pull repositorio/nome-da-imagem
        
        

## Testes
### Testes unitários

#### O que foi usado?


#### Como verificar a cobertura de testes ?


#### Dependências:



#### Plugins:


### Testes de integração

#### O que foi feito?


- Exemplo de teste:



- A quantidade de minutos de cada plano foi utilizada como base para os testes, isso significa que foram feitos testes com valor menor, valor igual e valor maior que a quantidade de minutos de cada plano.

#### Plano de testes

Testes executados automaticamente no build:

- Plano 30 com duração da chamada menor que o plano.
Resultado esperado: Com o plano a ligação custa 0.0 e sem o plano o valor do minuto é multiplicado pela duração da chamada

- Plano 30 com duração da chamada igual ao plano.
Resultado esperado: Com o plano a ligação custa 0.0 e sem o plano o valor do minuto é multiplicado pela duração da chamada

- Plano 30 com duração da chamada maior que o plano.
Resultado esperado: Com o plano a ligação custa o valor dos minutos excedentes * o valor do minuto com acréscimo de 10% e sem o plano o valor do minuto é multiplicado pela duração da chamada

- Plano 60 com duração da chamada menor que o plano.
Resultado esperado: Com o plano a ligação custa 0.0 e sem o plano o valor do minuto é multiplicado pela duração da chamada
 
- Plano 60 com duração da chamada igual ao plano.
Resultado esperado: Com o plano a ligação custa 0.0 e sem o plano o valor do minuto é multiplicado pela duração da chamada

- Plano 60 com duração da chamada maior que o plano.
Resultado esperado: Com o plano a ligação custa o valor dos minutos excedentes * o valor do minuto com acréscimo de 10% e sem o plano o valor do minuto é multiplicado pela duração da chamada

- Plano 120 com duração da chamada menor que o plano.
Resultado esperado: Com o plano a ligação custa 0.0 e sem o plano o valor do minuto é multiplicado pela duração da chamada

- Plano 120 com duração da chamada igual ao plano.
Resultado esperado: Com o plano a ligação custa 0.0 e sem o plano o valor do minuto é multiplicado pela duração da chamada

- Plano 120 com duração da chamada maior que o plano.
Resultado esperado: Com o plano a ligação custa o valor dos minutos excedentes * o valor do minuto com acréscimo de 10% e sem o plano o valor do minuto é multiplicado pela duração da chamada

Testes manuais:

- Validação do campo codigo de origem.
Resultado esperado: HttpStatus 409 e a mensagem: 409 CONFLICT "Codigo de origem nulo ou vazio"

- Validação do campo codigo de destino.
Resultado esperado: HttpStatus 409 e a mensagem: 409 CONFLICT "Codigo de destino nulo ou vazio"

- Validação do campo minutos do plano.
Resultado esperado: HttpStatus 409 e a mensagem: 409 CONFLICT "O campo minutos do plano esta invalido"

- Validação do campo duracao da chamada.
Resultado esperado: HttpStatus 409 e a mensagem: 409 CONFLICT "Duracao da chamada invalida"

- Validação do campo valor do minuto.
Resultado esperado: HttpStatus 409 e a mensagem: 409 CONFLICT "O campo valor do minuto esta invalido"


Foi disponibilizada uma collection para ser importada no postman com esses testes prontos. Arquivo: falemais.postman_collection.json

### Testes de carga

- Os testes de carga podem ser executados com jmeter, os scripts com os testes prontos estão no diretório testes-carga;

## Documentação
- Os métodos estão disponiveis na rota http://localhost:8080/falemais/swagger-ui.html
 
## Health

Rotas disponíveis para verificar a saúde e métricas da aplicação:



Com isso é possível utilizar softwares como o grafana para monitorar esse serviço.

## Docker
### /dockerfile
- Na raiz do projeto existe um arquivo dockerfile, pronto para ser usado e gerar uma imagem docker