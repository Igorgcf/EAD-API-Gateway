# API-Gateway – Microservice

### Gateway de entrada da plataforma EAD, responsável por receber, filtrar e encaminhar solicitações para os microserviços internos.
### Este projeto foi desenvolvido em Java utilizando o ecossistema Spring, especialmente Spring Cloud Gateway e Eureka Client.

#### 🚀 Descrição do Projeto

O API-Gateway atua como a porta de entrada central para todos os serviços da aplicação.
Ele funciona como um roteador inteligente, delegando chamadas aos microserviços corretos, além de oferecer pontos de extensão para aplicar filtros, autenticação, autorização e monitoramento.

* #### Atualmente, ele:

Conecta-se ao Eureka Server como cliente.

Descobre automaticamente os microserviços registrados.

Redireciona requisições para:

ead-authuser — Gestão de usuários/autenticação.

ead-course — Gestão de cursos, matrículas e conteúdos.

Mantém arquitetura limpa e desacoplada entre os componentes.

* #### Tecnologias Utilizadas

Java 17+

Spring Boot

Spring Cloud Gateway

Spring Cloud Netflix Eureka Client

Maven

* #### Funcionalidades
Serviço registrado no Eureka

O Gateway se registra automaticamente no Eureka Server para poder descobrir e rotear requisições para os microserviços disponíveis.

Roteamento dinâmico para microserviços

Utiliza o service discovery do Eureka, permitindo rotas como:

/ead-authuser/** → ead-authuser

/ead-course/** → ead-course

Balanceamento de carga (quando configurado)

Caso existam múltiplas instâncias de um mesmo serviço, o Gateway faz load balance via Spring Cloud LoadBalancer.

* #### Estrutura extensível

Pronto para inclusão de:

Filtros globais

Autenticação JWT

Monitoramento e logging

Resiliência (circuit breaker e retry)

* #### Como Executar o Projeto

Certifique-se de que o Eureka Server está rodando.

Clone este repositório:

git clone https://github.com/Igorgcf/EAD-API-Gateway.git

Compile e execute:

```markdown 
mvn clean install
```
ou 
```markdown 
mvn spring-boot:run
```

O serviço estará acessível em:

http://localhost:8080

---

## Microservices da Arquitetura

Para o funcionamento completo da arquitetura em ambiente local, todos os microservices do ecossistema devem estar em execução utilizando o profile ativo `dev`.

Os microservices que compõem a arquitetura são:

- [Authuser Microservice](https://github.com/Igorgcf/EAD-Authuser)
- [Course Microservice](https://github.com/Igorgcf/EAD-Course)
- [API Gateway](https://github.com/Igorgcf/EAD-API-Gateway)
- [Service Discovery (Eureka Server)](https://github.com/Igorgcf/EAD-Service-Registry)
- [Config Server](https://github.com/Igorgcf/EAD-Config-Server)
- Execute [Notification Microservice](https://github.com/Igorgcf/EAD-Notification)
  ou
  [Notification-Hex Microservice](https://github.com/Igorgcf/EAD-Notification-Hexagonal)

> ℹ️ Certifique-se de executar todos os serviços com o profile `dev` ativo para garantir a comunicação correta entre os microservices durante o desenvolvimento local.

---

![image](https://portswigger.net/cms/images/82/40/cc98-article-220330-spring-cloud-main.png)
  
