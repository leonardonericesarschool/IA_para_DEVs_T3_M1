# Diagrama de Classes - Sistema de Doação de Livros

```mermaid
classDiagram
    class User {
        -int id
        -string name
        -string email
        -string password
        -string phone
        -Address address
        -DateTime createdAt
        +register()
        +login()
        +updateProfile()
    }

    class Donor {
        -List~Book~ books
        +registerBook(Book)
        +listBooks()
        +updateBookStatus(Book, Status)
        +respondToDonationRequest(Request)
    }

    class Institution {
        -string type
        -string documentation
        -string responsiblePerson
        +requestDonation(Book)
        +listRequests()
        +confirmBookReceipt(Book)
    }

    class Book {
        -int id
        -string title
        -string author
        -string edition
        -string condition
        -List~string~ photos
        -Status status
        -DateTime registeredAt
        -Donor owner
        +updateStatus()
        +addPhotos()
        +updateInfo()
    }

    class DonationRequest {
        -int id
        -Book book
        -Institution requester
        -Donor donor
        -Status status
        -DateTime requestDate
        -DateTime updateDate
        -List~Message~ messages
        +updateStatus()
        +addMessage()
        +generateReceipt()
    }

    class Address {
        -string street
        -string number
        -string complement
        -string city
        -string state
        -string zipCode
        +validate()
        +format()
    }

    class Status {
        <<enumeration>>
        AVAILABLE
        REQUESTED
        ACCEPTED
        REJECTED
        COMPLETED
        CANCELLED
    }

    class Message {
        -int id
        -User sender
        -string content
        -DateTime sentAt
        +markAsRead()
    }

    User <|-- Donor
    User <|-- Institution
    User "1" -- "1" Address
    Donor "1" -- "*" Book
    Book "1" -- "*" DonationRequest
    Institution "1" -- "*" DonationRequest
    DonationRequest "1" -- "*" Message
    Book -- Status
    DonationRequest -- Status
```

### Descrição das Classes e Relacionamentos

1. **User (Abstrata)**
   - Classe base para todos os usuários do sistema
   - Contém informações comuns como nome, email, senha e endereço
   - Gerencia autenticação e perfil do usuário

2. **Donor**
   - Herda de User
   - Representa o doador de livros
   - Gerencia lista de livros e responde a solicitações
   - Pode ter múltiplos livros cadastrados

3. **Institution**
   - Herda de User
   - Representa ONGs e bibliotecas
   - Possui documentação específica
   - Pode solicitar e confirmar recebimento de doações

4. **Book**
   - Representa o livro para doação
   - Mantém informações detalhadas e fotos
   - Possui status atual
   - Pertence a um Donor

5. **DonationRequest**
   - Gerencia o processo de doação
   - Conecta Donor, Institution e Book
   - Mantém histórico de mensagens
   - Controla status da doação

6. **Address**
   - Componente para endereços
   - Usada por User (composição)
   - Possui validação própria

7. **Status**
   - Enum para estados de Book e DonationRequest
   - Define todos os possíveis estados do processo

8. **Message**
   - Representa mensagens na comunicação
   - Vinculada a DonationRequest
   - Mantém histórico de comunicação

### Cardinalidades

- User-Address: 1:1 (cada usuário tem um endereço)
- Donor-Book: 1:N (um doador pode ter vários livros)
- Book-DonationRequest: 1:N (um livro pode ter várias solicitações)
- Institution-DonationRequest: 1:N (uma instituição pode fazer várias solicitações)
- DonationRequest-Message: 1:N (uma solicitação pode ter várias mensagens)