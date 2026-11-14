# Como funciona o laboratório

O [contrato pedagógico](CONTRATO_PEDAGOGICO.md) orienta a mentoria. Abra o projeto no Codex e peça para iniciar ou retomar um desafio. O mentor usa o [registro de progresso](PROGRESS.md) para recuperar o contexto.

1. **Apresentação.** A pedido do participante, o mentor registra em [desafios](challenges/README.md) o problema, o estado atual relevante, as restrições conhecidas, os objetivos de aprendizado e os critérios de conclusão disponíveis.
2. **Investigação e proposta.** O participante esclarece requisitos, explicita premissas e propõe alternativas com justificativas. O mentor investiga os pontos que podem mudar a escolha e atualiza o registro à medida que os requisitos são esclarecidos.

   Ao documentar requisitos e restrições, diferencie explicitamente: (a) requisitos confirmados pelo representante do negócio; (b) hipóteses assumidas pelo participante e ainda não validadas; e (c) questões em aberto que podem influenciar decisões arquiteturais. Não apresente hipóteses como fatos confirmados. Essas classificações devem ser atualizadas conforme novas informações forem obtidas.

3. **Discussão e revisão.** Mentor e participante discutem consequências e trade-offs. Quando a proposta estiver pronta para uma avaliação independente, o participante pode pedir: “Use o subagente `architecture-reviewer` para fazer uma revisão crítica desta proposta com os requisitos conhecidos.” O mentor encaminha a proposta, as restrições, as premissas declaradas e os registros relevantes. A revisão apresenta argumentos que o participante pode contestar ou incorporar. Se o revisor não estiver disponível, o mentor informa a limitação.
4. **Decisão e execução.** O participante decide. Registre as escolhas arquiteturais relevantes em [ADRs](adr/README.md), com os argumentos que pesaram na decisão. Se o desafio pedir implementação, inicie o código de negócio após a aprovação explícita do participante.
5. **Validação e conclusão.** Confronte o resultado com os critérios de conclusão. Quando pertinente, registre [experimentos](experiments/README.md) reproduzíveis. Faça uma retrospectiva breve com o que foi aprendido, as hipóteses revistas e as pendências. Com a confirmação do participante, marque o desafio como concluído e atualize o progresso.

Ao encerrar uma sessão de trabalho, mesmo que o desafio não tenha sido concluído, atualize `docs/PROGRESS.md` com um resumo conciso contendo: desafio atual, estado da discussão ou implementação, decisões tomadas, hipóteses relevantes, questões pendentes e próximo passo recomendado. Não marque desafios como concluídos sem confirmação do participante. Ao iniciar uma nova sessão, consulte esse registro para retomar o contexto sem repetir investigações já realizadas.

Combine etapas triviais e ajuste o nível de detalhe ao desafio. Mantenha os registros ligados entre si. Ao mudar uma decisão já tomada, preserve o ADR original e indique qual ADR o substitui. Acompanhe a evolução dos registros no histórico Git quando o versionamento estiver ativo.
