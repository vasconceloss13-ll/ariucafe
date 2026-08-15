# CLAUDE.md — Ariú Café (sandbox de treino)

> **O que é este arquivo:** a ficha do miniprojeto de treino, no formato real de `CLAUDE.md`. Serve pra duas coisas: (1) é a bíblia que os comandos leem primeiro neste projeto; (2) é um **exemplar** do formato de ficha que a pessoa vai aprender a ler na prática.
>
> **Estado:** a tela já está **construída e validada** (`index.html`). O que falta é o Claude Code **montar o projeto** em volta dela (git + esta ficha na raiz) — ver o documento de entrega.

---

## 1. Identidade

Cartão de fidelidade digital de uma cafeteria **de mentira**, a "Ariú Café". Cliente compra café e ganha um selo; a cada 10 selos, resgata um café grátis.

Existe só como **campo de treino**: não é produto, não tem cliente real, não sobe pra lugar nenhum. Público: uma pessoa treinando julgamento de builder. O domínio é propositalmente óbvio — a *única* surpresa do projeto é a regra plantada (seção 9).

## 2. Stack

- Roda **100% local**, na máquina da pessoa. Um comando (ou dois cliques) abre no navegador.
- **Uma página só.** Sem servidor, sem back.
- **Sem banco de dados.** Os dados são mockados em memória (o "faz-de-conta de banco"). Recarregou a página, volta ao estado inicial.
- **Implementação (decidida):** um único `index.html` com JavaScript simples (vanilla) e fixtures em memória. Sem build, sem framework.

**A tela (construída):** cartão de fidelidade com a lista de clientes e os selos de cada um visíveis (cartão de carimbos), botão *registrar compra* e botão *resgatar café*. O estado dos selos é a coisa mais gritante da tela — de propósito: é isso que faz a prova de nível 4 aparecer (café infinito visível na contagem).

## 3. Comandos

- Rodar local: abrir o `index.html` no navegador (ou servir com um servidor local simples, ex.: `npx serve`).
- **Não existe** comando de deploy. De propósito (ver seção 4).

## 4. Deploy

**Não existe.** Este projeto não sobe pra lugar nenhum — nem produção, nem ambiente de teste remoto. Vive na máquina da pessoa e só.

Consequência de treino: o fluxo `/task` roda até *"construiu, revisou, funciona local"* — não há produção pra subir, então ele termina aí, e está correto. O portão de deploy do mundo real (backup + QA antes de subir) fica na teoria (Episódio 6) e é treinado **ao vivo, supervisionado, na primeira tarefa de verdade**.

## 5. Banco

**Não existe** banco de verdade. Os dados são mockados em memória (o papel de "banco = planilha organizada", pra reforçar o Episódio 4).

Entidades de mentira:

- **Cliente** — `nome`, `id`, `transacoes` (lista). O número de **selos é derivado** das transações, não um campo solto.
- **Transação** — `tipo` (`"compra"` ou `"resgate"`) e ordem.

Fixture inicial (já na tela):

- **Ana** — 8 selos (8 compras).
- **Bruno** — 3 selos (3 compras).
- **Carla** — 0 selos (10 compras + 1 resgate — acabou de resgatar).

A contagem de selos é **derivada das compras** — é o que deixa a regra plantada visível quando alguém erra.

## 6. Versionamento

**Git local, sem nuvem.** Sem repositório remoto. Serve pra pessoa treinar `commit` e `branch` num ambiente onde nada vaza pra fora.

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

- Nenhuma pendente de construção. A tela está pronta e validada; falta só **montar o projeto em volta** (git + esta ficha na raiz), conforme o documento de entrega.

---

### Nota de fronteira

A tela (`index.html`) já foi **construída e testada**. Montar o projeto em volta dela (git, esta ficha na raiz, deixar rodável) é a tarefa de Claude Code — ver o documento de entrega. As 4 provas de treino são o **próximo documento**, e chegam depois, uma a uma, via `/task`.
