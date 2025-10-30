# User Story: Cadastro de Doador

**Prioridade:** High

**Como** um potencial doador de livros  
**Eu quero** me cadastrar no aplicativo  
**Para que** eu possa começar a doar meus livros usados

### Critérios de Aceitação

```gherkin
Cenário: Cadastro bem-sucedido de doador
Dado que estou na página de cadastro
Quando preencho todos os campos obrigatórios (nome, email, senha, telefone e endereço)
E clico no botão "Cadastrar"
Então devo ver uma mensagem de confirmação
E ser redirecionado para minha página de perfil

Cenário: Tentativa de cadastro com email já existente
Dado que estou na página de cadastro
Quando preencho um email que já está cadastrado no sistema
E tento finalizar o cadastro
Então devo ver uma mensagem de erro informando que o email já está em uso
E os dados não devem ser salvos

Cenário: Validação de campos obrigatórios
Dado que estou na página de cadastro
Quando deixo um ou mais campos obrigatórios em branco
E tento finalizar o cadastro
Então devo ver mensagens de erro indicando quais campos precisam ser preenchidos
E o formulário não deve ser submetido
```