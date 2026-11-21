---
name: ux-documentation
description: Criar ou atualizar incrementalmente a documentação de experiência do usuário dos desafios do laboratório. Use ao solicitar jornadas, estados ou consolidação de UX e após esclarecimentos ou mudanças confirmadas com stakeholders que afetem a experiência. Não usar para dúvidas gerais sem efeito documental nem para decidir negócio ou arquitetura.
---

# Documentação de experiência do usuário

Consolide requisitos em jornadas, interações e comportamentos observáveis, com esforço proporcional ao desafio e foco no aprendizado de arquitetura de sistemas distribuídos. Execute no próprio agente, sem criar subagentes.

## Contexto e fontes

Os caminhos abaixo são relativos à raiz do repositório, não à pasta desta skill.

- Leia `AGENTS.md`, `docs/CONTRATO_PEDAGOGICO.md` e `docs/GUIA_DO_LABORATORIO.md`. Identifique o desafio solicitado ou consulte `docs/PROGRESS.md` para localizar o atual; não inicie outro desafio. Se houver ambiguidade material, esclareça o alvo antes de editar.
- Leia o enunciado e os registros de requisitos do desafio em `docs/challenges/`. Eles são a fonte de verdade para regras de negócio confirmadas. Consulte os registros disponíveis de conversas e validações com stakeholders, incluindo o contexto da sessão. Não presuma acesso a outras conversas; explicite registros ausentes quando relevantes.
- Leia a experiência existente e, se houver, a proposta arquitetural e os ADRs relacionados para identificar decisões vigentes e possíveis impactos. Premissas e jornadas em propostas não constituem confirmação de negócio.
- Use a estrutura do template em `docs/challenges/001-experiencia-usuario.md`: Jornadas, Estados da interface, Alternativas consideradas, Questões em aberto e Validações com stakeholders. Esse arquivo também é o destino do Desafio 001; para outros desafios, reutilize sua estrutura, sem copiar conteúdo específico nem modificá-lo.

## Autoridade e classificação

- A experiência interpreta as regras confirmadas; não cria regras nem substitui sua fonte. Nesta skill, edite somente o documento de experiência do desafio. Não altere enunciados, registros de requisitos, propostas arquiteturais, ADRs ou implementação.
- Antes de sincronizar uma nova confirmação de negócio, verifique se o mentor a registrou na fonte de verdade correspondente, com origem e eventual decisão substituída. Se estiver apenas na conversa, sinalize a necessidade desse registro ao mentor; não promova o relato a regra confirmada no documento de UX. Prossiga apenas nas partes independentes já sustentadas pelos registros.
- Distinga explicitamente **confirmado** (com referência à fonte), **proposta ou hipótese não validada**, **questão em aberto** e **recomendação dependente de decisão arquitetural**. A descrição de uma jornada derivada de requisitos não significa que houve validação do stakeholder; registre validação somente quando ela realmente ocorreu.
- Não invente telas, canais, campos, mensagens, permissões, políticas de erro, prazos ou garantias técnicas. Descreva comportamentos sustentados pelas fontes sem escolher detalhes de interação ainda não confirmados. Registre lacunas necessárias como perguntas, identificando se dependem do stakeholder ou do participante.
- Decisões de negócio e experiência pendente cabem ao stakeholder; arquitetura cabe ao participante. Preserve alternativas e escolhas já registradas com seu status. Não transforme sugestões em decisões, nem decisões confirmadas em hipóteses. Em conflito sem substituição explícita, preserve a decisão vigente, exponha a divergência e peça esclarecimento sobre o ponto afetado.

## Criação

Quando solicitada a criação, preencha o template existente ou crie `docs/challenges/NNN-experiencia-usuario.md`, seguindo a convenção do desafio. Se já houver conteúdo, preserve-o e aplique atualização incremental.

Descreva usuários e objetivos, sequência de ações, resultados esperados e estados observáveis sustentados pelos requisitos. Relacione jornadas e estados às fontes por links e títulos de seção ou identificadores existentes, sem criar identificadores nos requisitos. Separe alternativas ainda não decididas, hipóteses, dúvidas e dependências arquiteturais. Mantenha seções sem evidência breves, indicando a ausência de registro, sem preencher artificialmente o template.

## Atualização incremental

Compare as novas informações com os requisitos e a experiência atuais. Identifique o que efetivamente muda em jornadas, estados, alternativas, pendências ou validações. Se não houver mudança pertinente ou a informação já estiver refletida, não edite arquivos nem acrescente histórico; informe que a documentação já está sincronizada.

Atualize somente as seções afetadas. Preserve conteúdo e decisões ainda válidos. Substitua uma decisão apenas com confirmação explícita na fonte e registre concisamente o que foi substituído e por quê, mantendo a rastreabilidade. Resolva hipóteses e questões somente quando houver evidência suficiente.

Em `Validações com stakeholders`, registre apenas alterações ou validações relevantes, sem duplicar entradas: data e papel quando disponíveis, origem, retorno confirmado, seções afetadas e pendências ou impactos. Não invente data, participante, aprovação ou conversa; uma consolidação documental deve ser identificada como tal, sem simular validação.

Quando uma mudança puder afetar uma proposta ou ADR existente, sinalize no documento de experiência a referência e a consequência possível para discussão, sem redesenhar nem alterar a arquitetura ou presumir uma solução técnica.

## Verificação e retorno

Revise o diff: cada afirmação confirmada deve ter apoio nas fontes; hipóteses e conflitos devem permanecer visíveis; somente a experiência pode ter sido editada por esta operação. Uma atualização puramente documental sustentada pelas fontes não exige aprovação do participante. Isso não autoriza decidir questões pendentes nem torna validação de UX uma etapa obrigatória para avançar no laboratório.

Informe brevemente o arquivo e as seções criadas ou alteradas, dúvidas que exigem stakeholder ou participante e possíveis impactos arquiteturais. Se nada mudou, diga isso sem gerar alterações cosméticas.
