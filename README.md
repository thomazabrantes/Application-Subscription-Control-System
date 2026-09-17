# Sistema de Controle de Assinaturas de Aplicativos

API REST desenvolvida em Java com Spring Boot para gerenciar clientes, aplicativos, assinaturas e promoções.

## Funcionalidades

- Cadastro, edição e listagem de clientes.
- Cadastro, edição e listagem de aplicativos.
- Atualização do custo mensal de aplicativos.
- Cadastro e gerenciamento de assinaturas entre clientes e aplicativos.
- Suporte a promoções com dias extras e/ou desconto.
- Persistência utilizando JPA e banco de dados H2 em memória.
- Carga automática de dados iniciais para desenvolvimento.

## Tecnologias

- Java 21
- Spring Boot 3.4.0
- Spring Web
- Spring Data JPA
- Spring Data REST
- H2 Database
- Maven
- Lombok

## Estrutura do projeto

O projeto Spring Boot está localizado em:

```text
arquitetura_clean_eu_acho/arq_clean_do_zero/trabfdsfinal/
```

Os principais componentes estão organizados em camadas, incluindo domínio, DTOs, repositórios e controladores da aplicação.

## Pré-requisitos

- JDK 21 ou superior
- Maven 3.9 ou superior
- Git

## Como executar

1. Clone o repositório:

   ```bash
   git clone https://github.com/thomazabrantes/Application-Subscription-Control-System.git
   cd Application-Subscription-Control-System
   ```

2. Entre no diretório da aplicação:

   ```bash
   cd arquitetura_clean_eu_acho/arq_clean_do_zero/trabfdsfinal
   ```

3. Execute a aplicação com o Maven:

   ```bash
   ./mvnw spring-boot:run
   ```

   No Windows, utilize:

   ```bat
   mvnw.cmd spring-boot:run
   ```

   Caso o Maven Wrapper não esteja disponível, execute `mvn spring-boot:run` com o Maven instalado.

A aplicação será iniciada, por padrão, em `http://localhost:8080`.

## API

A API utiliza o prefixo `/servcad`. Alguns endpoints disponíveis são:

| Método | Endpoint | Descrição |
| --- | --- | --- |
| `POST` | `/servcad/clientes` | Cadastra um cliente |
| `GET` | `/servcad/clientes` | Lista os clientes |
| `PUT` | `/servcad/clientes/{codigo}` | Atualiza um cliente |
| `POST` | `/servcad/aplicativos` | Cadastra um aplicativo |
| `GET` | `/servcad/aplicativos` | Lista os aplicativos |
| `PUT` | `/servcad/aplicativos/{codigo}` | Atualiza um aplicativo |
| `POST` | `/servcad/aplicativos/atualizacusto/{codigo}` | Atualiza o custo mensal |
| `POST` | `/servcad/assinaturas` | Cadastra uma assinatura |

### Exemplos de requisições

Cadastrar um cliente:

```bash
curl -X POST http://localhost:8080/servcad/clientes \
  -H "Content-Type: application/json" \
  -d '{"nome":"João Silva","email":"joao.silva@example.com"}'
```

Cadastrar um aplicativo:

```bash
curl -X POST http://localhost:8080/servcad/aplicativos \
  -H "Content-Type: application/json" \
  -d '{"nome":"Aplicativo de Música","custoMensal":9.99}'
```

Cadastrar uma assinatura:

```bash
curl -X POST http://localhost:8080/servcad/assinaturas \
  -H "Content-Type: application/json" \
  -d '{
    "aplicativo": {"codigo": 1},
    "cliente": {"codigo": 1}
  }'
```

Outros exemplos de comandos podem ser encontrados em [`comandos.txt`](arquitetura_clean_eu_acho/arq_clean_do_zero/trabfdsfinal/comandos.txt).

## Banco de dados

A aplicação utiliza o H2 em memória com a seguinte configuração de desenvolvimento:

- URL: `jdbc:h2:mem:testdb`
- Console H2: habilitado
- Console: `http://localhost:8080/h2-console`
- Usuário e senha: conforme a configuração local do Spring Boot

O arquivo `src/main/resources/db/data.sql` insere dados iniciais sempre que a aplicação é iniciada. Como o banco é em memória, os dados são recriados a cada execução.

## Build e testes

Para gerar o build da aplicação:

```bash
cd arquitetura_clean_eu_acho/arq_clean_do_zero/trabfdsfinal
./mvnw clean package
```

Para executar os testes:

```bash
./mvnw test
```

## Observações

Este projeto foi desenvolvido como uma aplicação acadêmica para demonstrar o gerenciamento de assinaturas de aplicativos usando uma API REST e arquitetura baseada em Spring Boot.
