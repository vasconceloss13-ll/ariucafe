> Sandbox de treino. Duplo papel: (1) handoff para o Claude Code construir o
> miniprojeto; (2) exemplar do formato de ficha que a pessoa está aprendendo
> a ler — por isso segue o schema fixo de 10 seções igual a qualquer projeto
> real deste laboratório. Texto original da pessoa em `BRIEFING.md`.

## Identidade
- OBJETIVO: cartão de fidelidade digital de uma cafeteria de mentira — cliente
  compra café e ganha um selo; a cada 10 selos, resgata um café grátis. Existe
  só como campo de treino de julgamento de builder: não é produto, não tem
  cliente real, não sobe pra lugar nenhum. O domínio é propositalmente óbvio —
  a única surpresa do projeto é a regra plantada (ver "O que NÃO fazer").
- PRODUTO: Ariú Café (nome usado na tela construída; a ficha original desta
  demanda chamava o projeto de "Cafeteria Selo")
- REQUISITOS_URL: "não existe" — as demandas de treino moram no material de
  exercícios (as 4 provas), documento à parte; esta ficha é só o terreno.

## Stack
- FRAMEWORK: não existe — `index.html` único com JavaScript vanilla e
  fixtures em memória. Sem build, sem framework. (Decidido na construção;
  tela entregue pronta e validada.)
- RUNTIME: navegador — 100% local, sem servidor, sem back, uma página só.
- BANCO: "não existe" — ver seção Banco.
- LINGUAGEM: JavaScript vanilla, num único arquivo.
- TOKENS_FILE: "não existe"

## Comandos
- BUILD_CMD: "não existe"
- LINT_CMD: "não existe"
- TEST_CMD: "não existe"
- TYPECHECK_CMD: "não existe"
- Rodar local: abrir `index.html` direto no navegador (ou, se preferir, um
  servidor local de uma linha como `npx serve`).

## Deploy
- DEPLOY_KIND: "não existe" — o projeto não sobe pra lugar nenhum, nem
  produção nem ambiente de teste remoto. Vive só na máquina da pessoa.
- DEPLOY_CMD: "não existe"
- DEPLOY_DEV_CMD: "não existe"
- TEM_DEV: "não existe"
- PROD_HOST: "não existe"
- DEV_HOST: "não existe"
- SSH_USER: "não existe"
- SSH_PORT: "não existe"
- REMOTE_DIR: "não existe"
- SSH_KEY_FILE: "não existe"
- INFRA_NOTES: resumo — não há infra nenhuma, de propósito. Consequência de
  treino: o fluxo `/task` roda até "construiu, revisou, funciona local" e
  termina aí — não existe produção pra subir. O portão de deploy do mundo real
  (backup + QA antes de subir) fica pra teoria (Episódio 6) e é treinado ao
  vivo, supervisionado, só na primeira tarefa de verdade fora deste sandbox.

## Banco
- TEM_DB: "não existe" — dados mockados num arquivo de fixtures ("faz-de-conta
  de banco"); recarregou a página, volta ao estado inicial.
- DB_CONTAINER: "não existe"
- DB_MIGRATE_USER: "não existe"
- MIGRATE_CMD: "não existe"
- MIGRATION_DIR: "não existe"
- TEM_BASELINE: "não existe"
- CONTAINER_ENGINE: "não existe"
- BACKUP_CMD: "não existe"
- RESTORE_CMD: "não existe"
- Entidades de mentira, como implementadas em `index.html` (ajustado da
  fixture original: `selos` não é campo solto — é derivado):
  - Cliente — `id`, `nome`, `transacoes` (lista).
  - Transação — `tipo` (`"compra"` ou `"resgate"`), `ordem`.
  - Selos disponíveis = nº de compras − (nº de resgates × 10). Função
    `selosDisponiveis()` em `index.html`. É essa derivação que deixa a regra
    plantada visível quando alguém erra.
  - Fixture: Ana (8 selos, 8 compras); Bruno (3 selos, 3 compras); Carla (0
    selos, acabou de resgatar — 10 compras + 1 resgate).

## Versionamento
- TEM_GIT: sim — repositório local iniciado, branch `main`.
- GIT_REMOTE: `https://github.com/vasconceloss13-ll/ariucafe` (GitHub,
  conectado em 2026-08-15). Decisão original desta ficha era "sem nuvem, sem
  repositório remoto" — revista a pedido da pessoa; o sandbox deixou de ser
  100% local nesse sentido, mas segue sem deploy nenhum (ver seção Deploy).

## Handoff
- TEM_HANDOFF: "não existe" — as demandas de treino não moram nesta pasta,
  moram no material de exercícios (as 4 provas), documento à parte. A pasta
  `.handoff/` (oculta, renomeada de `handoff/`) guardou uma entrega pontual
  de montagem inicial (tela pronta + instruções), já processada e arquivada.
- HANDOFF_DONE_DIR: `.handoff/_done/<AAAA-MM-DD>/`

## Pontos quentes de segurança
- Resumo: superfície de risco ~zero, de propósito — sandbox local, mockado,
  sem login e sem dado real. O foco de treino aqui é regra de negócio, não
  segurança (segurança de verdade se treina nas fichas dos projetos reais,
  onde há login, dado pessoal e produção). O ponto quente real deste projeto
  não é segurança — é a regra de negócio descrita em "O que NÃO fazer".

## O que NÃO fazer
- Resumo: **resgate não gera selo** — essa é a regra plantada, o coração do
  treino. Detalhe abaixo.
  - Um café grátis é uma recompensa, não uma compra. Só compra gera selo.
  - Por quê: se resgate gerasse selo, resgatar o 10º café grátis daria um
    selo pro próximo resgate, que geraria outro grátis, que daria mais um
    selo — café grátis infinito, a loja quebra.
  - Como vira armadilha de treino (prova de nível 4): um pedido como "faz
    toda transação virar um selo" soa inocente e a IA tende a obedecer ao pé
    da letra, violando a regra sem perceber — porque a regra estava na
    cabeça de quem pediu, não no pedido. Código roda, teste passa, parece
    perfeito. A pessoa tem que farejar o café infinito.
  - Esta seção fica escrita aqui de propósito; nos exercícios a IA vai
    "esquecer" dela — pegar esse esquecimento é o próprio exercício.

## Pendências abertas
- "não existe" — tela construída e validada (`index.html`), ficha ajustada
  aos fatos reais da implementação, git conectado ao remoto. Falta só
  decidir o que fazer com os arquivos de entrega em `.handoff/` (ver
  observação abaixo) e aguardar as próximas demandas de treino.
