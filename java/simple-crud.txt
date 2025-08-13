Tenho a seguinte estrutura de projeto java 21 e springboot 3.4.x e o banco de dados postgres:
|_src
    |_main
        |_java
           |_api
               |_controller
           |_mapper
           |_repository
           |_model
              |_entity
           |_service
               |_impl

Crie uma tabela tb_tipo_documento a partir do seguinte json:
{
    "id": 1,
    "descricao": "Carteira de identidade",
    "status": "A"
}
- O nome das classe precisam ter o prefixo TipoDocumento
- Crie a classe de Entity que mapeie a tabela criada na pasta model/entity/
- Crie a interface repository 
- Crie uma interface do serviço na pasta service e a implamentação na pasta service/impl e faça o autowired do repositório
- Crie a API documentada pela io.swagger.v3.oas.
- Cria um controller que implemente a API
- Crie uma classe de modelo baseada na entity para ser utilizada como um DTO de request
- Crie uma classe de modelo baseada na entity para ser utilizada como um DTO de response
- Crie um mapper que mapeie a classe de DTO request para uma entidade e a entity em um DTO de response
