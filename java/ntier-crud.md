
Todos os dados aqui são em português do Brasil
Contexto:
Sou um programador java, estou utilizando a versão 24, também utilizo o springboot 3.5 nesta solução.
- A aplicação está utilizando o banco de dados POSTGRESS.
- Estou utilizando lombok para diminuir o boilerplait.
- Estou utilizando o spring data para integração com banco de dados.
- Estou utilizando o flyway para versionar meu banco de dados.
- Estou utilizando o swagger e openAPI para documentar minha aplicação (org.springdoc:springdoc-openapi-starter-webmvc-ui:2.8.4)
- Estou utilizando a arquitetura N-Tier (Controller, Service, Repository, Entity, Models de request e response).

Quero que sempre gere uma API que contemple o CRUD e uma busca paginada

peckagePricipal: "src/main/java/com.leokenzley.api"
Nome da entidade: "Customer" 

A estrutura do meu projeto está distribuídas nas sequintes pastas do meu projeto java e quero que gere cada classe respeitando a estrutura:
- src/main/java/com.leokenzley.api/api -> Aqui estão as interfaces que documentão os endpoints do swagger e openAPI, , o sufixo deve sempre conter "Nome da entidade"+API
  - exemplo: interface CustomerAPI
- peckagePricipal/api/controller -> Aqui estão as classes Controllers que implementam as interfaces do pacote src/main/java/com.leokenzley.api/api, o sufixo deve sempre conter "Nome da entidade"+Controller
- peckagePricipal/database/entity -> Aqui ficam as classes que mapeiam as tabelas do banco de dados utilizando JPA, o sufixo deve sempre conter "Nome da entidade"+Entity
- peckagePricipal/database/repository -> Aqui estão as interfaces que extends JpaRepository para cada entity, o sufixo deve sempre conter "Nome da entidade"+Repository 
- peckagePricipal/service -> Aqui estão as interfaces com as regras de negócios, o sufixo deve sempre conter "Nome da entidade"+Service
  - Essa classe deve sempre ter os seguintes métodos do crud: (created, update, deleteById, getPaginated e findById)
- peckagePricipal/service/impl -> Aqui estão as classes que implementam as interfaces src/main/java/com.leokenzley.api/service fazem o import e injeção de dependência das interfazer ligadas a entity, o sufixo deve sempre conter "Nome da entidade"+ServiceImpl
- peckagePricipal/model -> Aqui estão a classes recorder de request "/resquest" e response "/response", o sufixo deve sempre conter "Nome da entidade"+Request para o request e o sufixo deve sempre conter "Nome da entidade"+Response
- peckagePricipal/mapper -> Aqui neste repositório estão as interfaces que utilizam o mappers que possuem os métodos toEntity que transformam as classes src/main/java/com.leokenzley.api/model/request em uma entity através do método toEntity e um método toResponse que transformam uma classe Entity em uma classe src/main/java/com.leokenzley.api/model, o sufixo deve sempre conter "Nome da entidade"+Mapper
  - Exemplo tenho um request chamado UsuarioRequest, o método toEntity vai receber o UsuarioRequest e mapear os campos para o UsuarioEntity
  - Exemplo tenho uma classe que mapeia o banco UsuarioEntity o método toResponse vai mapear os campos UsuarioEntity para UsuarioResponse
  - Sempre utiizando as anotações na interface    @Mapper(componentModel = "spring") e para cada campo  @Mapping(target = "employeeId", source = "entity.id")
- Crie um script DDL para criar a tabela com o prefixo tb_ + o nome da entidade a partir do json 
  - json:
    {
    "id": 1,
    "name": "THS tecnologia",
    "documentNumber": "00002704738157",
    "dtCreatedAt": "2025-09-06T18:05:00",
    "dtUpdatedAt": "2025-09-06T18:50:00",
    "status": "A",
    "phoneNumber": "61998668535",
    "email": "meuemail@gmail.com",
    "primaryContactName": "Adolf Big Ass",
    "secundaryContactName": "Beatle Juice"
    }
- Toda entitidade que tem um campo com o nome "status", vai ser sempre do tipo enum "StatusEnum" que possui "A" -> ativo e "I" inativo, utilizado para delete lógico
