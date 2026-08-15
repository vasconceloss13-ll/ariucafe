# BRIEFING.md — Cafeteria Selo

> Material bruto entregue pela pessoa para este projeto, preservado literalmente.
> Ela respondeu ao questionário do `/project` não item a item, mas entregando
> diretamente a ficha já escrita no formato de `CLAUDE.md` — porque este projeto
> é, ao mesmo tempo, um sandbox de treino a construir e um exemplar do formato
> de ficha que ela está aprendendo a ler. O texto abaixo é exatamente o que ela
> colou na conversa; o `CLAUDE.md` deste projeto é a mesma informação
> reformatada no schema fixo de 10 seções.

---

# CLAUDE.md — Cafeteria Selo (sandbox de treino)

> **O que é este arquivo:** a ficha do miniprojeto de treino, escrita no formato real de `CLAUDE.md`. Serve pra duas coisas: (1) é o handoff pra o Claude Code **construir** o sandbox; (2) é um **exemplar** do formato de ficha que a pessoa vai aprender a ler na prática.
>
> **Construir o sandbox = tarefa de Claude Code.** Aqui está a especificação; o código é lá.

---

## 1. Identidade

Cartão de fidelidade digital de uma cafeteria — **de mentira**. Cliente compra café e ganha um selo; a cada 10 selos, resgata um café grátis.

Existe só como **campo de treino**: não é produto, não tem cliente real, não sobe pra lugar nenhum. Público: uma pessoa treinando julgamento de builder. O domínio é propositalmente óbvio — a *única* surpresa do projeto é a regra plantada (seção 9).

## 2. Stack

- Roda **100% local**, na máquina da pessoa. Um comando abre no navegador.
- **Uma página só** (a parte que aparece na tela). Sem servidor, sem back.
- **Sem banco de dados.** Os dados são mockados (de mentira), num arquivo de fixtures — o "faz-de-conta de banco". Recarregou a página, volta ao estado inicial.
- Linguagem: o mais simples que rodar local com um comando (HTML + JavaScript num arquivo, ou um React de arquivo único — *decisão de construção, do Claude Code*). Requisito inegociável: **simples, local, um comando pra rodar.**

## 3. Comandos

- Rodar local: *a definir na construção* (ex.: abrir o `index.html`, ou `npm run dev`).
- **Não existe** comando de deploy. De propósito (ver seção 4).

## 4. Deploy

**Não existe.** Este projeto não sobe pra lugar nenhum — nem produção, nem ambiente de teste remoto. Vive na máquina da pessoa e só.

Consequência de treino: o fluxo `/task` roda até *"construiu, revisou, funciona local"* — não há produção pra subir, então ele termina aí, e está correto. O portão de deploy do mundo real (backup + QA antes de subir) fica na teoria (Episódio 6) e é treinado **ao vivo, supervisionado, na primeira tarefa de verdade**.

## 5. Banco

**Não existe** banco de verdade. Os dados são mockados num arquivo de fixtures (o papel de "banco = planilha organizada", pra reforçar o Episódio 4).

Entidades de mentira:

- **Cliente** — `nome`, `id`, `selos` (número de 0 a 9; ao chegar em 10, vira resgate e zera).
- **Transação** — `tipo` (`"compra"` ou `"resgate"`), `cliente`, `data`.

Fixture inicial sugerido (concreto, pra construção e pros exercícios citarem):

- **Ana** — 8 selos. Histórico: 8 compras.
- **Bruno** — 3 selos. Histórico: 3 compras.
- **Carla** — 0 selos, acabou de resgatar. Histórico: 10 compras + 1 resgate.

A contagem de selos deve ser **derivada das transações de compra** (não um número solto que se incrementa às cegas) — isso é o que deixa a regra plantada visível quando alguém erra.

## 6. Versionamento

**Git local, sem nuvem.** Sem Bitbucket, sem repositório remoto. Serve só pra pessoa treinar `commit` e `branch` num ambiente onde nada vaza pra fora. *(Se for atrapalhar a simplicidade, pode cair — decisão de construção.)*

## 7. Handoff

As demandas de treino não moram aqui — moram no material de exercícios (as 4 provas, documento à parte). Esta ficha é só o terreno onde elas acontecem.

## 8. Pontos quentes de segurança

Num sandbox local, mockado, sem login e sem dado real, a superfície de risco de segurança é **~zero — de propósito**. Aqui o foco é treinar julgamento de **regra de negócio**, não segurança. (Segurança de verdade a pessoa treina lendo as fichas dos projetos reais, onde há login, dado pessoal e produção.)

O ponto quente **real** deste projeto não é segurança — é a regra de negócio da seção 9. É ali que mora o perigo.

## 9. O que NÃO fazer — a regra plantada (o coração do treino)

> Esta seção é o segredo do sandbox. Está escrita aqui, na ficha, de propósito. Mas nos exercícios a IA vai **"esquecer" dela** — e é exatamente isso que a pessoa tem que pegar.

**Resgate NÃO gera selo.** Um café grátis é uma *recompensa*, não uma *compra*. Só compra gera selo.

**Por que importa:** se um resgate gerasse selo, resgatar o 10º café grátis daria um selo pro próximo, que geraria outro grátis, que daria mais um selo, que geraria outro grátis… **café grátis infinito — a loja quebra.**

**Como isso vira a prova de nível 4:** quando pedirem à IA algo como *"faz toda transação virar um selo"*, ela vai obedecer ao pé da letra — e violar esta regra sem perceber, porque a regra estava na cabeça de quem pediu, não no pedido. O código vai rodar, o teste vai passar, vai parecer perfeito. A pessoa tem que farejar o café infinito.

## 10. Pendências abertas

- Escolha final da linguagem (HTML+JS ou React de arquivo único) — decide na construção.
- Manter ou não o git local (seção 6).
- Formato de fixture (arquivo `.js`, `.json`) — decide na construção.

---

### Nota de fronteira

Isto é a **especificação**. Construir o sandbox (escrever o código, montar as fixtures, deixar rodável com um comando) é **tarefa de Claude Code** — é só passar esta ficha pra lá. As 4 provas de treino são o **próximo documento**, escritas em cima deste terreno.
