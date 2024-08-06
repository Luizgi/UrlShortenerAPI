# URL Shortener API

## Descrição

Esta é uma API encurtadora de URL construída com C# .NET. A API permite encurtar URLs longas e redirecionar para as URLs originais. Inclui recursos como contagem de acessos e expiração de URLs.

## Requisitos

- .NET 6.0 SDK
- SQL Server
- Ferramentas do Entity Framework Core

## Configuração do Projeto

### 1. Clone o Repositório

```bash
git clone <https://github.com/Luizgi/UrlShortener>
cd <UrlShortener>
```

### 2. Configurar o banco de Dados

Certifique-se de que você tem uma instância do SQL Server em execução e crie uma nova base de dados. Atualize a string de conexão no arquivo appsettings.json para refletir a sua configuração:

```json
    {
    "ConnectionStrings": {
        "DefaultConnection": "Server=<NOME_DO_SERVIDOR>;Database=<NOME_DO_BANCO_DE_DADOS>;Trusted_Connection=True;MultipleActiveResultSets=true"
    },
    "Logging": {
        "LogLevel": {
        "Default": "Information",
        "Microsoft.AspNetCore": "Warning"
        }
    },
    "AllowedHosts": "*"
    }
```

### 3. Restaurar Dependências

Navegue até o diretório do projeto e restaure as dependências:

``` bash
dotnet restore
```

### 4. Executar Migrações

Crie e aplique migrações para configurar o banco de dados:


``` bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

### 5. Executar o Projeto

Inicie o projeto:
``` bash
dotnet run
```

### 6. Acessar o Swagger
A API estará disponível em http://localhost:5000 e https://localhost:5001. 
A documentação do Swagger pode ser acessada em https://localhost:5001/swagger.


## Endpoints

### 1. Encurtar URL

**Endpoint:** `POST /api/urls`

**Request Body:**

```json
{
  "originalUrl": "https://example.com",
  "expirationDate": "2024-12-31T23:59:59"  // Opcional
}
```

**Response:**
```json
{
  "id": 1,
  "originalUrl": "https://example.com",
  "shortUrl": "abc123",
  "createdAt": "2023-08-01T12:34:56",
  "expirationDate": "2024-12-31T23:59:59",
  "accessCount": 0
}

```

### 2. Redirecionar para URL Original

**Endpoint:** `GET /api/urls/r/{shortUrl}`

**Response:** `Redireciona para a URL original`

## 3. Obter Informações de uma URL Encurtada

**Endpoint:** `GET /api/urls/{id}`

**Response:** 
```json
{
  "id": 1,
  "originalUrl": "https://example.com",
  "shortUrl": "abc123",
  "createdAt": "2023-08-01T12:34:56",
  "expirationDate": "2024-12-31T23:59:59",
  "accessCount": 10
}

```

# Desenvolvimento

## Estrutura do Projeto
- **Controllers**: Contém os controladores da API.
- **Data**: Contém o contexto do Entity Framework Core.
- **Models**: Contém os modelos de dados.
- **Migrations**: Contém as migrações do Entity Framework Core.
- **Program.cs**: Configuração e inicialização do aplicativo.

## Adicionando Novas Funcionalidades
1. Criar um novo ramo para a funcionalidade:

    ```bash
    git checkout -b nome-da-funcionalidade
    ```

2. Implementar a funcionalidade e testar localmente.

3. Comitar as mudanças:

    ```bash
    git add .
    git commit -m "Implementação da nova funcionalidade"
    ```

4. Fazer o push do ramo para o repositório remoto:

    ```bash
    git push origin nome-da-funcionalidade
    ```

5. Criar um Pull Request para revisão.

## Contribuição
1. Faça um fork do repositório.
2. Crie um novo ramo para sua funcionalidade ou correção.
3. Faça commit das suas alterações.
4. Faça push para o seu ramo.
5. Crie um Pull Request.
