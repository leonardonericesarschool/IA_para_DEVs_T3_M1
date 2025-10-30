# Diagramas de Sequência - Sistema de Doação de Livros

## 1. Cadastro de Doador

```mermaid
sequenceDiagram
    actor User
    participant Frontend
    participant AuthController
    participant UserService
    participant Database

    User->>Frontend: Acessa página de cadastro
    Frontend->>Frontend: Exibe formulário de cadastro

    User->>Frontend: Preenche dados e submete
    Frontend->>Frontend: Valida campos obrigatórios

    alt Campos válidos
        Frontend->>AuthController: POST /api/register
        AuthController->>UserService: validateEmail(email)
        
        alt Email disponível
            UserService->>Database: createUser(userData)
            Database-->>UserService: userId
            UserService-->>AuthController: success
            AuthController-->>Frontend: 201 Created
            Frontend->>Frontend: Exibe mensagem sucesso
            Frontend->>Frontend: Redireciona para perfil
        else Email já existe
            UserService-->>AuthController: emailExists error
            AuthController-->>Frontend: 400 Bad Request
            Frontend->>Frontend: Exibe erro email existente
        end
    else Campos inválidos
        Frontend->>Frontend: Exibe erros de validação
    end
```

## 2. Cadastro de Livro para Doação

```mermaid
sequenceDiagram
    actor Donor
    participant Frontend
    participant BookController
    participant BookService
    participant StorageService
    participant Database

    Donor->>Frontend: Acessa cadastro de livro
    Frontend->>Frontend: Exibe formulário

    Donor->>Frontend: Preenche dados do livro
    Donor->>Frontend: Upload fotos
    Frontend->>Frontend: Valida dados

    alt Dados válidos
        Frontend->>StorageService: POST /api/upload
        StorageService-->>Frontend: URLs das fotos

        Frontend->>BookController: POST /api/books
        BookController->>BookService: createBook(bookData)
        BookService->>Database: saveBook(bookData)
        Database-->>BookService: bookId

        BookService-->>BookController: success
        BookController-->>Frontend: 201 Created
        Frontend->>Frontend: Exibe sucesso
        Frontend->>Frontend: Atualiza lista de livros
    else Dados inválidos
        Frontend->>Frontend: Exibe erros
    end
```

## 3. Solicitação de Doação

```mermaid
sequenceDiagram
    actor Institution
    participant Frontend
    participant RequestController
    participant DonationService
    participant NotificationService
    participant Database

    Institution->>Frontend: Visualiza livro disponível
    Frontend->>Frontend: Exibe detalhes do livro

    Institution->>Frontend: Clica em "Solicitar Doação"
    Frontend->>Frontend: Exibe confirmação

    alt Confirmado
        Frontend->>RequestController: POST /api/donation-requests
        RequestController->>DonationService: createRequest(requestData)
        DonationService->>Database: saveRequest(requestData)
        Database-->>DonationService: requestId

        DonationService->>NotificationService: notifyDonor(requestData)
        NotificationService-->>DonationService: notificationSent

        DonationService-->>RequestController: success
        RequestController-->>Frontend: 201 Created
        Frontend->>Frontend: Atualiza status
        Frontend->>Frontend: Exibe confirmação
    else Cancelado
        Frontend->>Frontend: Fecha diálogo
    end

    alt Acompanhamento
        Institution->>Frontend: Acessa lista de solicitações
        Frontend->>RequestController: GET /api/donation-requests
        RequestController->>DonationService: getRequests(filters)
        DonationService->>Database: fetchRequests(filters)
        Database-->>DonationService: requests
        DonationService-->>RequestController: requests
        RequestController-->>Frontend: 200 OK
        Frontend->>Frontend: Exibe lista filtrada
    end
```

### Descrição dos Componentes

1. **Frontend**
   - Interface do usuário
   - Validação client-side
   - Gerenciamento de estado
   - Roteamento

2. **Controllers**
   - AuthController: Gerencia autenticação
   - BookController: Gerencia operações de livros
   - RequestController: Gerencia solicitações

3. **Services**
   - UserService: Lógica de usuários
   - BookService: Lógica de livros
   - DonationService: Lógica de doações
   - StorageService: Gerencia upload de arquivos
   - NotificationService: Gerencia notificações

4. **Database**
   - Persistência de dados
   - Transações
   - Consultas

### Observações

- Os diagramas mostram o fluxo feliz e principais casos de erro
- Validações ocorrem tanto no frontend quanto no backend
- Notificações são assíncronas
- Uploads de arquivos são tratados separadamente
- Autenticação é verificada em todas as rotas protegidas