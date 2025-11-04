# User Story: Sistema de Reputação

**Prioridade:** Medium

**Como** um usuário do sistema (doador/receptor)
**Eu quero** poder avaliar e ver avaliações de outros usuários
**Para que** eu possa tomar decisões informadas sobre doações e construir confiança na plataforma

### Critérios de Aceitação

```gherkin
Cenário: Avaliação após doação concluída
Dado que uma doação foi marcada como concluída
Quando acesso a opção de avaliar a transação
E atribuo uma nota de 1 a 5 estrelas
E adiciono um comentário sobre a experiência
Então a avaliação deve ser registrada e vinculada ao perfil do outro usuário
E a média de avaliações do usuário deve ser atualizada

Cenário: Visualização do histórico de reputação
Dado que estou visualizando o perfil de um usuário
Quando acesso a seção de reputação
Então devo ver a média geral das avaliações
E devo ver os últimos 5 comentários recebidos
E devo ver estatísticas como "Total de doações realizadas/recebidas"

Cenário: Denúncia de avaliação inadequada
Dado que estou visualizando uma avaliação
Quando identifico conteúdo inadequado ou ofensivo
E clico no botão "Denunciar Avaliação"
E seleciono o motivo da denúncia
Então a denúncia deve ser enviada para análise dos moderadores
E devo receber uma confirmação do registro da denúncia
```