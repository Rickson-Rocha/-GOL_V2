# Diagrama C4 de Contêiner
O diagrama apresentado é um C4 model do tipo Contêiner(nivel 2), que representa a arquitetura de conteiner da aplicação +GOL. O C4 model é uma abordagem para descrever arquiteturas de software, dividindo-as em contexto, contêineres, componentes e código. Esta divisão ajuda a entender e comunicar a estrutura de sistemas complexos de forma clara e eficaz.

Importância do C4 Model
O C4 model é essencial para visualizar a arquitetura de software, proporcionando uma visão abrangente dos contêineres e componentes que compõem o sistema. Ele facilita a comunicação entre equipes técnicas e não técnicas, ajuda na identificação de dependências críticas e suporta decisões de design e evolução do sistema de forma estruturada.

O contêiner é uma abstração de alto nível responsável por uma parte específica da funcionalidade do sistema. Pode ser uma aplicação web, um banco de dados, uma API, um serviço de microserviços, uma aplicação de linha de comando, entre outros.





```mermaid
C4Container
title Diagrama de Containers do Sistema de gestão esportiva +GOL

Person(cliente, Cliente, "Um cliente do sistema", $tags="v1.0")

Container_Boundary(c1, "Sistema Internet +GOL") {
    Container(spa, "Aplicação de Página Única", "JavaScript, React e Next.js", "Fornece todas as funcionalidades do sistema +GOL para clientes via navegador web")
    Container(ma, "Aplicativo Móvel", "JavaScript, React Native", "Fornece um subconjunto das funcionalidades do sistema +GOL para clientes via dispositivo móvel")
    Container(api, "Aplicação API", "Java, Spring Boot", "Fornece funcionalidades do sistema +GOL via API REST")
    ContainerDb(bd, "Banco de Dados", "PostgreSQL", "Armazena informações de registro de usuários, credenciais de autenticação hash, logs de acesso, etc.")
}

Rel(cliente, spa, "Usa", "HTTPS")
UpdateRelStyle(cliente, spa, $offsetY="-40")
Rel(cliente, ma, "Usa")
UpdateRelStyle(cliente, ma, $offsetY="-30")

Rel(spa, api, "Usa", "async, JSON/HTTPS")
Rel(ma, api, "Usa", "async, JSON/HTTPS")
Rel(api, bd, "Usa", "JPA e Spring Data")


```