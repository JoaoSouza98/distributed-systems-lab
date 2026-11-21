# Desafio 001 — Reserva de salas

**Estado** — em investigação.

## Contexto

Uma empresa coordena as reservas de salas de reunião por um canal interno do Microsoft Teams. Funcionários pedem horários livres, solicitam reservas, consultam o resultado e pedem cancelamentos. Um atendente de operações consulta a agenda compartilhada, registra ou cancela reservas e responde no canal. Às vezes, duas equipes recebem confirmação para a mesma sala no mesmo horário e só descobrem o conflito quando chegam à reunião.

## Requisitos confirmados pelo representante do negócio

- Um funcionário solicita a reserva de uma sala para um intervalo, consulta se o pedido foi confirmado ou recusado por conflito e pode cancelar uma reserva sua que ainda não começou. A reserva fica em nome do funcionário. Pessoas podem fazer parte de mais de uma equipe, sem efeito sobre as permissões de reserva.
- São seis equipes, com quatro a dez pessoas por equipe, em um único escritório. Há quatro salas com 4, 6, 8 e 12 lugares. Todas têm acesso sem degraus. A sala de 12 lugares é a única equipada para videoconferência e é usada em reuniões híbridas. O solicitante escolhe a sala conforme a capacidade e os recursos necessários.
- As reservas podem ocorrer de segunda a sexta, das 8h às 18h no horário do escritório (`America/Sao_Paulo`). Início e fim ficam em múltiplos de 15 minutos. A duração vai de 15 minutos a 2 horas.
- Reservas confirmadas para a mesma sala não podem se sobrepor, inclusive quando os pedidos chegam quase ao mesmo tempo. Reservas consecutivas são permitidas. Cancelar uma reserva libera o intervalo.
- Para pedidos válidos, a confirmação ou a recusa por conflito é automática, sem aprovação humana.
- A empresa já tem contas corporativas, usadas também para acessar o Teams. No uso real, a identidade associada à reserva deve ser a do funcionário autenticado. No laboratório, operações aceita identidades de teste, desde que seja possível verificar que só o titular pode cancelar sua reserva. A integração com o login corporativo fica fora do primeiro incremento.
- O primeiro incremento inclui consultar quais salas estão livres para um intervalo, solicitar uma reserva, consultar seu resultado e cancelar uma reserva própria que ainda não começou. A disponibilidade pode mudar entre a consulta e o pedido. Trocas e negociações ficam fora do escopo. Uma mudança de horário é feita com cancelamento e novo pedido.

## Preferência de operações para o canal de atendimento

Para o primeiro incremento, operações prefere que os funcionários consigam usar o fluxo sem instalar outro aplicativo. Uma página interna acessível pelo navegador, com o link divulgado no canal atual do Teams, seria bem aceita. Usar o Teams como interface também é uma opção. A escolha do canal fica com o participante, e a integração com o Teams é opcional.

## Esclarecimentos com stakeholders

- **2026-11-21 — representante de operações simulado:** o participante perguntou se capacidade e recursos das salas devem ser informados dentro do sistema. Confirmado que, ao escolher uma sala para reservar, o funcionário deve conseguir consultar no próprio sistema sua capacidade de participantes e os recursos oferecidos, incluindo se possui videoconferência. Isso explicita o apoio à escolha já prevista nos requisitos; não confirma a hipótese de filtragem automática por quantidade de participantes ou recursos, nem define o formato da interface. O impacto é disponibilizar essas informações na experiência de escolha, sem alterar as capacidades e os recursos já registrados.
- **2026-11-21 — representante de operações simulado:** ao esclarecer se uma tentativa recusada por conflito antes do registro precisa aparecer posteriormente, operações confirmou que basta comunicar claramente o conflito no momento da tentativa. Não é obrigatório criar um item de reserva recusada nem oferecer histórico dessas recusas imediatas. Isso esclarece a interpretação de “consultar seu resultado”, sem eliminar a consulta das reservas efetivadas ou alterar a regra de não sobreposição. A listagem de recusas no rascunho passa a ser uma opção não exigida pelo negócio; a persistência técnica das tentativas cabe ao participante.

## Hipóteses e questões em aberto

- **Hipóteses do participante** — nenhuma registrada.
- **Questões em aberto** — nenhuma questão de negócio pendente nesta rodada.

## Objetivo de aprendizado e critérios de conclusão

Transformar um relato de negócio em regras verificáveis e justificar uma proposta a partir delas. Para concluir, o participante deve esclarecer as regras que afetam a proposta, justificar a decisão arquitetural e validar os fluxos do incremento, incluindo uma reserva sem conflito, pedidos concorrentes com sobreposição e a liberação do intervalo na consulta de disponibilidade após um cancelamento pelo titular. A conclusão depende da confirmação do participante.
