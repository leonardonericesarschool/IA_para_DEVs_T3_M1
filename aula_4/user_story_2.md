# User Story: Cadastro de Livros para Doação

**Prioridade:** High

**Como** um doador cadastrado  
**Eu quero** cadastrar livros para doação  
**Para que** as ONGs e bibliotecas possam visualizar os livros disponíveis

### Critérios de Aceitação

```gherkin
Cenário: Cadastro completo de um livro para doação
Dado que estou logado como doador
Quando acesso a página de cadastro de livros
E preencho todos os dados do livro (título, autor, edição, estado de conservação, foto)
E clico em "Cadastrar Livro"
Então o livro deve aparecer na minha lista de livros disponíveis para doação
E deve ficar visível para ONGs e bibliotecas

Cenário: Upload de múltiplas fotos do livro
Dado que estou cadastrando um livro
Quando seleciono múltiplas fotos do livro (até 5 fotos)
E submeto o cadastro
Então todas as fotos devem ser salvas
E devem ser exibidas na página de detalhes do livro

Cenário: Edição de informações do livro cadastrado
Dado que tenho um livro cadastrado para doação
Quando acesso a página de edição do livro
E modifico qualquer informação
E salvo as alterações
Então as informações atualizadas devem ser exibidas na página do livro
E um histórico de alterações deve ser mantido
```