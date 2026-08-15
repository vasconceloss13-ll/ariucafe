# Entrega para o Claude Code — montar o sandbox "Ariú Café"

> **Atenção:** a tela **já está pronta e validada**. Esta tarefa **não é construir do zero nem redesenhar** — é *embrulhar* o que já existe num projeto rodável, pronto pra receber as demandas de treino (que virão depois, uma a uma). *(Este documento substitui qualquer brief de construção anterior.)*

---

## O pacote (anexar estes arquivos)

1. **`cafeteria-selo.html`** — a tela pronta. Baseline já correto e **testado**: compra gera selo, resgate não. **Não reescrever a lógica. Não redesenhar. Não mexer no visual.**
2. **`SANDBOX-FICHA.md`** — a ficha do projeto. Vai na raiz como **`CLAUDE.md`**.

## A tarefa (passos)

1. Criar a pasta do projeto.
2. Colocar a tela como **`index.html`**, exatamente como está no arquivo entregue.
3. Colocar a ficha na raiz como **`CLAUDE.md`**.
4. `git init` **local** — sem remoto, sem nuvem. Primeiro commit com tudo.
5. Deixar rodável do jeito mais simples: abrir o `index.html` no navegador já basta; se preferir, um servidor local de uma linha (ex.: `npx serve`). **Documentar o comando.** Sem build, sem framework, sem deploy.

## Regras críticas (não quebrar)

- **Não alterar a lógica de negócio.** O baseline é correto **de propósito**: compra gera selo, resgate **não**; a contagem de selos vem só das compras. A demanda-armadilha que quebra isso vem **depois**, como exercício.
- **Não adicionar features.** Sem histórico por cliente, sem "faltam X selos", sem nada novo. Essas são demandas de treino que chegam uma a uma.
- **Não embelezar nem mexer no design.** A tela está do jeito que a dona quer.

## Checklist de "pronto" (confirme cada item)

- [ ] Abre no navegador, e o comando pra rodar está documentado.
- [ ] Lista mostra Ana (8), Bruno (3) e Carla (0) selos.
- [ ] *Registrar compra* soma 1 selo; ao chegar em 10, libera o resgate.
- [ ] *Resgatar café* **não** soma selo.
- [ ] `CLAUDE.md` está na raiz do projeto.
- [ ] `git init` local feito, com primeiro commit.
- [ ] Nenhuma feature nova, nenhum estilo mexido.

## Depois disto

O projeto fica parado, montado e rodando, **pronto pra receber as demandas**. As 4 provas de treino são o próximo material e chegam separadamente — uma por vez, cada uma como uma demanda de `/task`.
