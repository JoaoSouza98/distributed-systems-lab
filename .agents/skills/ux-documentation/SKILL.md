---
name: ux-documentation
description: Criar, propor melhorias e atualizar incrementalmente a documentação de experiência do usuário dos desafios do laboratório. Use para elaborar jornadas, interações e feedbacks para validação, consolidar UX ou sincronizá-la após esclarecimentos de stakeholders. Não usar para dúvidas gerais sem efeito documental nem para decidir regras de negócio ou arquitetura.
---

# Documentação de experiência do usuário

Consolide requisitos e proponha experiências concretas para validação, com esforço proporcional ao desafio e foco no aprendizado de arquitetura de sistemas distribuídos. Não espere que todos os detalhes de interação sejam decididos pelo participante ou stakeholder antes de apresentar uma proposta útil. Execute no próprio agente, sem criar subagentes.

## Contexto e fontes

Os caminhos abaixo são relativos à raiz do repositório, não à pasta desta skill.

- Leia `AGENTS.md`, `docs/CONTRATO_PEDAGOGICO.md` e `docs/GUIA_DO_LABORATORIO.md`. Identifique o desafio solicitado ou consulte `docs/PROGRESS.md` para localizar o atual; não inicie outro desafio. Se houver ambiguidade material, esclareça o alvo antes de editar.
- Leia o enunciado e os registros de requisitos do desafio em `docs/challenges/`. Eles são a fonte de verdade para regras de negócio confirmadas. Consulte os registros disponíveis de conversas e validações com stakeholders, incluindo o contexto da sessão. Não presuma acesso a outras conversas; explicite registros ausentes quando relevantes.
- Leia a experiência existente e, se houver, a proposta arquitetural e os ADRs relacionados para identificar decisões vigentes e possíveis impactos. Premissas e jornadas em propostas não constituem confirmação de negócio.
- Use a estrutura do template em `docs/challenges/001-experiencia-usuario.md`: Jornadas, Estados da interface, Alternativas consideradas, Questões em aberto e Validações com stakeholders. Esse arquivo também é o destino do Desafio 001; para outros desafios, reutilize sua estrutura, sem copiar conteúdo específico nem modificá-lo.

## Autoridade e classificação

- A experiência interpreta as regras confirmadas e contém propostas de interação explicitamente identificadas; não estabelece novas regras de negócio nem substitui sua fonte. Nesta skill, edite somente o documento de experiência do desafio. Não altere enunciados, registros de requisitos, propostas arquiteturais, ADRs ou implementação.
- Antes de sincronizar uma nova confirmação de negócio, verifique se o mentor a registrou na fonte de verdade correspondente, com origem e eventual decisão substituída. Se estiver apenas na conversa, sinalize a necessidade desse registro ao mentor; não promova o relato a regra confirmada no documento de UX. Prossiga apenas nas partes independentes já sustentadas pelos registros.
- Distinga explicitamente **confirmado** (com referência à fonte), **proposta ou hipótese não validada**, **questão em aberto** e **recomendação dependente de decisão arquitetural**. A descrição de uma jornada derivada de requisitos não significa que houve validação do stakeholder; registre validação somente quando ela realmente ocorreu.
- Pode propor telas, campos, navegação, apresentação de informações, mensagens e ações de recuperação compatíveis com o escopo, identificando-os como propostas. Não apresente essas sugestões como fatos confirmados. Não invente permissões, regras de elegibilidade, prioridades, prazos de negócio ou garantias técnicas; quando uma interação depender deles, explicite a dependência e a questão a resolver.
- Decisões de negócio e experiência pendente cabem ao stakeholder; arquitetura cabe ao participante. Preserve alternativas e escolhas já registradas com seu status. Não transforme sugestões em decisões, nem decisões confirmadas em hipóteses. Em conflito sem substituição explícita, preserve a decisão vigente, exponha a divergência e peça esclarecimento sobre o ponto afetado.

## Postura propositiva

- Para cada jornada relevante, ofereça um fluxo recomendado: o que o usuário vê, informa e faz, o resultado esperado e o feedback nos estados pertinentes, como carregamento, ausência de resultados, sucesso, conflito e falha. Cubra somente os estados que fizerem sentido no desafio.
- Use o rascunho do participante como ponto de partida e complete lacunas de interação com sugestões identificadas. Recomende uma opção simples com justificativa breve; apresente alternativas apenas quando houver um trade-off relevante. Não entregue apenas uma lista de perguntas onde já for possível elaborar uma proposta.
- Nas seções do template, identifique blocos como **Proposta de UX — a validar** e indique a regra ou objetivo que os motiva, a recomendação e o ponto específico a validar. Agrupe detalhes relacionados, sem exigir aprovação isolada de cada campo ou mensagem. Separe o que depende de decisão arquitetural.
- Se faltar uma regra de negócio necessária, proponha as partes independentes e descreva a parte afetada de forma condicional, sem escolher a regra. Por exemplo, pode sugerir manter sala e intervalo preenchidos após recusa por conflito e oferecer nova consulta; isso não autoriza prometer disponibilidade nem reenviar automaticamente uma operação de resultado desconhecido.
- A skill pode elaborar e documentar propostas sem aprovação prévia, mas não aprová-las por conta própria, assumir o papel de stakeholder para validá-las nem implementar as interações. Encaminhe ao mentor apenas as decisões relevantes para validação proporcional.

## Criação

Quando solicitada a criação, preencha o template existente ou crie `docs/challenges/NNN-experiencia-usuario.md`, seguindo a convenção do desafio. Se já houver conteúdo, preserve-o e aplique atualização incremental.

Descreva usuários e objetivos, sequência de ações, resultados esperados e estados observáveis sustentados pelos requisitos. Acrescente uma proposta de interação suficiente para ser avaliada, conforme a postura propositiva acima. Relacione a base confirmada às fontes por links e títulos de seção ou identificadores existentes, sem criar identificadores nos requisitos. Separe propostas de UX, hipóteses de negócio, dúvidas e dependências arquiteturais. A ausência de decisão sobre um detalhe de interação permite propor uma solução; a ausência de evidência de confirmação exige manter seu status como proposta.

## Atualização incremental

Compare as novas informações ou o pedido de melhoria com os requisitos e a experiência atuais. Identifique o que efetivamente muda em jornadas, estados, alternativas, pendências ou validações. Um pedido para elaborar ou melhorar propostas de UX pode justificar atualização sem novos requisitos. Em sincronizações rotineiras sem mudança pertinente, ou quando o conteúdo já estiver refletido, não edite arquivos nem acrescente histórico; informe que não há atualização necessária. Não gere alternativas ou reformulações cosméticas a cada acionamento.

Atualize somente as seções afetadas. Preserve conteúdo e decisões ainda válidos. Substitua uma decisão apenas com confirmação explícita na fonte e registre concisamente o que foi substituído e por quê, mantendo a rastreabilidade. Resolva hipóteses e questões somente quando houver evidência suficiente.

Pode completar ou revisar propostas ainda não validadas quando houver motivo concreto, explicando a alteração. Uma proposta para uma questão aberta não encerra a questão nem equivale à sua validação. Se recomendar mudar uma decisão confirmada, apresente a alternativa separadamente, mantendo a decisão vigente.

Em `Validações com stakeholders`, registre apenas alterações ou validações relevantes, sem duplicar entradas: data e papel quando disponíveis, origem, retorno confirmado, seções afetadas e pendências ou impactos. Não invente data, participante, aprovação ou conversa; uma consolidação documental deve ser identificada como tal, sem simular validação.

Quando uma mudança puder afetar uma proposta ou ADR existente, sinalize no documento de experiência a referência e a consequência possível para discussão, sem redesenhar nem alterar a arquitetura ou presumir uma solução técnica.

## Verificação e retorno

Revise o diff: cada afirmação confirmada deve ter apoio nas fontes; hipóteses e conflitos devem permanecer visíveis; somente a experiência pode ter sido editada por esta operação. Uma atualização puramente documental sustentada pelas fontes não exige aprovação do participante. Isso não autoriza decidir questões pendentes nem torna validação de UX uma etapa obrigatória para avançar no laboratório.

Informe brevemente o arquivo e as seções criadas ou alteradas, a principal recomendação de UX e os pontos relevantes para validação ou decisão arquitetural. Se nada mudou, diga isso sem gerar alterações cosméticas.
