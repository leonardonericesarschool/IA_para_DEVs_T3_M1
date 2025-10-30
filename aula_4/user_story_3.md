# User Story: Solicitação de Doação por ONGs/Bibliotecas

**Prioridade:** Medium

**Como** uma ONG ou biblioteca cadastrada  
**Eu quero** solicitar doações de livros disponíveis  
**Para que** eu possa receber os livros para meu acervo

### Critérios de Aceitação

```gherkin
Cenário: Solicitação bem-sucedida de doação
Dado que estou logado como ONG/biblioteca
Quando encontro um livro disponível para doação
E clico no botão "Solicitar Doação"
E confirmo meu interesse
Então o doador deve receber uma notificação da solicitação
E o status do livro deve mudar para "Solicitado"

Cenário: Acompanhamento do status da solicitação
Dado que fiz uma solicitação de doação
Quando acesso minha página de solicitações
Então devo ver o status atual de cada solicitação
E devo poder filtrar por status (Pendente, Aceita, Recusada)
E devo ver o histórico de comunicações com o doador

Cenário: Confirmação de recebimento do livro
Dado que uma solicitação foi aceita pelo doador
E o livro foi entregue fisicamente
Quando confirmo o recebimento no sistema
Então o status da doação deve mudar para "Concluída"
E um comprovante digital deve ser gerado
E o doador deve receber uma notificação de confirmação
```