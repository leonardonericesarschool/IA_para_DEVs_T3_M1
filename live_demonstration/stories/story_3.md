# User Story: Logística de Entrega

**Prioridade:** Low

**Como** um doador
**Eu quero** ter opções flexíveis para a entrega dos livros
**Para que** eu possa realizar as doações de forma conveniente e segura

### Critérios de Aceitação

```gherkin
Cenário: Agendamento de coleta em domicílio
Dado que uma doação foi aceita
Quando seleciono a opção "Solicitar Coleta"
E escolho uma data e período disponível
E confirmo meu endereço de coleta
Então deve ser gerado um código de agendamento
E ambas as partes devem receber confirmação com os detalhes da coleta

Cenário: Pontos de entrega parceiros
Dado que uma doação foi aceita
Quando seleciono a opção "Entregar em Ponto Parceiro"
Então devo ver uma lista de pontos de entrega próximos
E para cada ponto devo ver: endereço, horário de funcionamento e instruções
E devo poder gerar um QR code para validar a entrega no local

Cenário: Rastreamento de entrega
Dado que uma entrega está em andamento
Quando acesso a página de rastreamento da doação
Então devo ver o status atual da entrega
E devo ver o histórico de atualizações
E devo poder compartilhar o código de rastreamento com o receptor
```