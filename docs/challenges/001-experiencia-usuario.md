# Desafio 001 — Experiência do usuário

Referência de negócio: [enunciado do desafio](001-reserva-de-salas.md), seção **Requisitos confirmados pelo representante do negócio**. As jornadas e os estados abaixo interpretam essas regras; não constituem validação de uma interface pelo stakeholder.

Referência de interação: [rascunho do participante](001-proposta-arquitetural.md#24-experiência-do-usuário-e-frontend), seção 2.4, linhas 60–118 na consolidação inicial. Seus detalhes são identificados como **proposta não validada**. Em divergências ou omissões do rascunho, prevalecem os requisitos do enunciado.

## Jornadas

### Consultar disponibilidade e escolher uma sala

**Base confirmada:** o funcionário consulta salas livres para um intervalo e escolhe conforme capacidade e recursos necessários. Há salas de 4, 6, 8 e 12 lugares; somente a de 12 tem videoconferência. Todas têm acesso sem degraus.

**Esclarecimento confirmado em 2026-11-21:** ao escolher a sala, o funcionário consegue consultar dentro do sistema a capacidade de participantes e os recursos de cada sala, incluindo se possui videoconferência. O formato da apresentação não foi definido. Fonte: [Esclarecimentos com stakeholders](001-reserva-de-salas.md#esclarecimentos-com-stakeholders).

O funcionário informa o intervalo, consulta a disponibilidade e escolhe uma sala adequada. Os horários seguem `America/Sao_Paulo`, de segunda a sexta entre 8h e 18h, com início e fim em múltiplos de 15 minutos e duração de 15 minutos a 2 horas. O resultado permite identificar quais salas estão livres naquele intervalo. A consulta não garante a reserva: a disponibilidade pode mudar antes do pedido.

**Hipótese do participante, não validada:** informar quantidade de participantes e recursos para filtrar as salas, conforme a seção 1.3 da [proposta](001-proposta-arquitetural.md#13-premissas-adotadas). A filtragem automática não é requisito confirmado.

### Solicitar uma reserva e consultar seu resultado

**Base confirmada:** o funcionário solicita a sala para o intervalo e consulta se o pedido foi confirmado ou recusado por conflito. Para pedidos válidos, a decisão é automática, sem aprovação humana. A reserva fica em nome do solicitante.

O funcionário envia o pedido e consulta o resultado correspondente. Uma consulta anterior de disponibilidade não equivale a confirmação. Pedidos quase simultâneos com sobreposição na mesma sala não podem gerar reservas confirmadas sobrepostas. Reservas consecutivas são permitidas. O canal e a forma de apresentar ou recuperar o resultado ainda dependem do desenho da interação.

**Esclarecimento confirmado em 2026-11-21:** se a tentativa for recusada por conflito antes do registro, basta comunicar claramente o conflito naquele momento. Não é obrigatório criar um item recusado para consulta posterior nem manter histórico dessas recusas imediatas. A consulta das reservas efetivadas permanece no escopo. Fonte: [Esclarecimentos com stakeholders](001-reserva-de-salas.md#esclarecimentos-com-stakeholders). Esse esclarecimento não resolve os casos de falha de comunicação com resultado desconhecido.

### Cancelar uma reserva própria

**Base confirmada:** o titular solicita o cancelamento de uma reserva sua que ainda não começou. O resultado esperado é o cancelamento e a liberação do intervalo para consulta de disponibilidade e novas reservas. Pertencer à mesma equipe não concede permissão para cancelar reservas de terceiros.

Uma mudança de horário é feita por cancelamento e novo pedido; trocas e negociações estão fora do incremento. O novo pedido continua sujeito à disponibilidade, sem garantia de sucesso por ter havido cancelamento.

### Acessar e navegar — proposta não validada

No [rascunho, seções 2.4.1 a 2.4.3](001-proposta-arquitetural.md#24-experiência-do-usuário-e-frontend), o funcionário informa usuário de teste e senha e, após autenticação, acessa uma página inicial com **Minhas reservas** e **Consultar disponibilidade das salas**.

Em **Minhas reservas**, a proposta apresenta sala, data e horário e status (confirmada ou cancelada), com ordenação por horário crescente e depois por status, além de acesso aos detalhes. O trecho sobre o final da listagem está incompleto; não há definição registrada de paginação ou carregamento adicional.

**Limite confirmado:** identidades de teste são aceitas no laboratório, desde que seja verificável que somente o titular cancela sua reserva. Usuário e senha, navegação, listagem e ordenação são escolhas do rascunho, não exigências do negócio. Login corporativo está fora do primeiro incremento.

## Estados da interface

### Comportamentos derivados dos requisitos confirmados

| Situação | Informação ou comportamento observável |
|---|---|
| Consulta de disponibilidade | Identifica as salas livres para o intervalo consultado, inclusive quando nenhuma estiver livre; não representa reserva confirmada. |
| Escolha da sala | Permite consultar no próprio sistema a capacidade de participantes e os recursos de cada sala, incluindo a presença ou ausência de videoconferência. |
| Pedido confirmado | Permite ao solicitante identificar que a sala foi reservada para o intervalo solicitado. |
| Pedido recusado por conflito | Permite distinguir a recusa da confirmação, inclusive quando a sala aparecia livre na consulta anterior. Quando a recusa ocorre antes do registro, basta informar o conflito na tentativa, sem exigir um item recusado para consulta posterior. |
| Reserva própria ainda não iniciada | Pode ser cancelada pelo titular. |
| Reserva cancelada | O intervalo fica liberado e isso se reflete na consulta de disponibilidade. |
| Reserva de terceiro ou já iniciada | Não pode ser cancelada pelo solicitante nessa condição; ocultação de ações, desabilitação e mensagens não estão definidas. |
| Intervalo fora das restrições | Não atende às regras confirmadas; a forma de orientar e apresentar a validação ainda não está definida. |

### Estados propostos pelo participante, ainda não validados

Fonte: [rascunho, seções 2.4.1 a 2.4.3](001-proposta-arquitetural.md#24-experiência-do-usuário-e-frontend).

| Situação | Comportamento proposto |
|---|---|
| Usuário ou senha sem preenchimento | Confirmação de acesso desabilitada. |
| Usuário inexistente ou senha incorreta | Mensagem específica para cada caso. |
| Falha interna no acesso | Mensagem genérica de erro interno. |
| Falha de autenticação em chamadas posteriores | Redirecionamento para o acesso ao sistema. |
| Carregamento de Minhas reservas concluído | Apresentação da listagem após receber as informações. |
| Falha ao carregar Minhas reservas, exceto autenticação | Mensagem genérica de erro interno e permanência na página inicial. |

O rascunho não define o feedback durante operações em andamento nem o tratamento de uma falha em que o resultado de uma reserva ou cancelamento seja desconhecido. Esses comportamentos permanecem em aberto, sem prescrever mensagens ou políticas de repetição.

## Alternativas consideradas

- **Preferência confirmada de operações:** uso sem instalar outro aplicativo. Uma página interna no navegador, divulgada por link no Teams, seria bem aceita; o próprio Teams também é opção. Fonte: [Preferência de operações para o canal de atendimento](001-reserva-de-salas.md#preferência-de-operações-para-o-canal-de-atendimento). A escolha do canal cabe ao participante e a integração com Teams é opcional.
- **Proposta do participante:** interface web com acesso por usuário e senha e navegação pela página inicial. Está alinhada à opção de navegador aceita por operações, mas não há validação específica desse fluxo nem comparação de benefícios e limitações registrada no trecho consultado.

## Questões em aberto

As pendências abaixo decorrem do desenho proposto; não substituem a indicação do enunciado de que não havia questão de negócio pendente na rodada registrada.

| Questão ou hipótese | Como esclarecer ou validar |
|---|---|
| Login por usuário e senha, mensagens distintas de credenciais e retorno ao acesso | Validar a experiência com o stakeholder se esse fluxo for mantido; o participante decide o mecanismo de identidade de teste e sessão. |
| Navegação por Minhas reservas, campos, ordenação, detalhes e fim da listagem incompleto | Completar a intenção do participante e validar os detalhes relevantes com o stakeholder; não presumir paginação. |
| Filtragem por quantidade de participantes e recursos | Confirmar com o stakeholder se a hipótese da seção 1.3 corresponde ao comportamento desejado. |
| Operação em andamento ou falha sem resultado conhecido na reserva ou cancelamento | Discutir o feedback esperado com o stakeholder e as garantias possíveis com o participante, sem equiparar falha de comunicação a recusa ou cancelamento. |

**Recomendações dependentes de decisão arquitetural:** ao detalhar a [proposta, seção 2.4](001-proposta-arquitetural.md#24-experiência-do-usuário-e-frontend), considerar os efeitos da identidade de teste sobre a autorização de cancelamento, da mudança de disponibilidade sobre a distinção entre consulta e confirmação e das falhas de comunicação sobre a consulta do resultado. A emissão e renovação de tokens descritas no rascunho continuam sendo proposta técnica; este documento não as aprova nem altera a divisão de responsabilidades entre frontend e backend.

**Impacto do esclarecimento sobre recusas imediatas:** a seção 2.4.3 da proposta pode ser reavaliada pelo participante quanto à inclusão de itens recusados em Minhas reservas. A decisão de persistir tentativas por razões técnicas não é determinada pela necessidade de exibir um histórico ao usuário.

**Impacto da exibição de capacidade e recursos:** ao detalhar a consulta e escolha de salas na proposta, considerar a disponibilização dessas informações para a interface. A hipótese de filtragem da seção 1.3 continua não validada; este esclarecimento não determina como obter ou armazenar os dados.

## Validações com stakeholders

- **Base disponível:** o enunciado registra requisitos confirmados pelo representante do negócio e a preferência de operações pelo canal. Não há transcrição separada nem data dessas interações nos documentos consultados. Não foi localizada validação específica das telas propostas.
- **2026-11-21 — consolidação documental, sem nova validação de stakeholder:** preenchidas Jornadas, Estados da interface, Alternativas consideradas, Questões em aberto e esta seção, a partir do enunciado e do rascunho indicado pelo participante. Nenhum novo requisito ou mudança de escopo foi confirmado nesta operação. Próximo passo: esclarecer as pendências relevantes conforme o desenho evoluir, sem tornar a aprovação integral de UX uma condição para avançar.
- **2026-11-21 — representante de operações simulado:** o participante perguntou se uma recusa por conflito anterior ao registro exigia item consultável posteriormente. Confirmado que a mensagem de conflito na tentativa é suficiente e que o histórico dessas recusas não é obrigatório. Fonte: [Esclarecimentos com stakeholders](001-reserva-de-salas.md#esclarecimentos-com-stakeholders). Atualizadas Jornadas, Estados da interface, Questões em aberto (impacto sobre a proposta) e este registro. A persistência técnica permanece com o participante; falhas com resultado desconhecido continuam em aberto.
- **2026-11-21 — representante de operações simulado:** confirmada a consulta de capacidade e recursos de cada sala dentro do sistema durante a escolha. Fonte: [Esclarecimentos com stakeholders](001-reserva-de-salas.md#esclarecimentos-com-stakeholders). Atualizadas a jornada de consulta e escolha, os estados da interface, o impacto sobre a proposta e este registro. Filtragem automática continua não validada; formato de apresentação e solução técnica não foram decididos.
