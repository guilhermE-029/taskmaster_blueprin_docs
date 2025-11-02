# Arquitetura do Sistema

## Visão de Alto Nível  
O sistema segue arquitetura **microserviços leve** com os principais módulos:
- Serviço de Autenticação/Autorização  
- Serviço de Projeto/Equipe  
- Serviço de Tarefa  
- Serviço de Notificação  
- Gateway/API  → único ponto de entrada para o frontend e para clientes externos  

      @startuml
    
      actor Usuário
    
      rectangle "API Gateway" {
    
        rectangle "Serviço Autenticação" --> (Banco Auth)
    
        rectangle "Serviço Projeto" --> (Banco Projeto)
    
        rectangle "Serviço Tarefa" --> (Banco Tarefa)
    
        rectangle "Serviço Notificação" --> (Broker Mensagens)
    
      }
    
      Usuário --> "API Gateway"
    
      @enduml

## Padrões de Comunicação  
- Serviços se comunicam entre si via mensagens assíncronas (ex: Kafka/RabbitMQ) para eventos de “tarefa criada”, “tarefa mudada”.  
- APIs REST‑ful ou GraphQL para entrada externa.  
- Autenticação baseada em JWT + OAuth2.

## Considerações de Escalabilidade  
- Cada serviço implantado em contêiner (ex: Docker/Kubernetes)  
- Base de dados separada por serviço (Database per service)  
- Uso de cache Redis para leitura intensiva (ex: painel Kanban)  

## Segurança  
- TLS para todas comunicações externas/internas  
- Cada serviço com escopo mínimo de privilégios  
- Auditoria de acesso e logs centralizados  

