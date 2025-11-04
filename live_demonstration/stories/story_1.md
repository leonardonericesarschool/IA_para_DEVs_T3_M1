# User Story: Busca Inteligente de Livros

**Prioridade:** High

**Como** uma ONG/biblioteca
**Eu quero** buscar livros usando filtros avançados
**Para que** eu possa encontrar facilmente os livros que melhor atendam às necessidades do meu público

### Critérios de Aceitação

```gherkin
Cenário: Filtrar livros por múltiplos critérios
Dado que estou na página de busca de livros
Quando seleciono filtros como categoria, faixa etária e estado de conservação
E clico em "Aplicar Filtros"
Então devo ver uma lista de livros que correspondem a todos os critérios selecionados
E os resultados devem ser ordenados por relevância

Cenário: Busca por localização geográfica
Dado que permiti o acesso à minha localização
Quando realizo uma busca por livros
Então os resultados devem mostrar primeiro os livros disponíveis mais próximos de mim
E devo ver a distância aproximada até cada doador

Cenário: Salvar preferências de busca
Dado que realizei uma busca com filtros específicos
Quando clico em "Salvar Esta Busca"
E dou um nome para a busca salva
Então devo poder acessar essa configuração de filtros posteriormente
E devo receber notificações quando novos livros corresponderem aos meus critérios salvos
```