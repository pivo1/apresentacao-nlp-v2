# Apresentação de PLN — versão 2 (revisão didática)

Projeto separado da apresentação original (`Apresentacao NLP`), para revisar os
slides sem conflito com a versão que já está pronta.

- Mesmo tema (DEXPI), mesmas cores, mesmos blocos e mesmos *cards* do slide 12.
- A revisão mexe em 6 slides da seção 01; o slide 19 ("Resumo") foi removido
  durante a revisão, para o bloco caber no tempo.

## O que mudou, slide por slide

| Slide | Antes | Agora |
|---|---|---|
| 13 | Título "Otimizando com SGD", três *bullets* e uma fórmula solta no meio | Três *cards* numerados (um trecho / um par / um passo), a fórmula do log com os dois termos comentados e a caixa "uma metade premia, a outra pune" |
| 14 | Derivação em três linhas de `align`, sem figura | Duas regras de derivada, o resultado "observado − esperado" e a figura da seta do *esperado* até o *observado* |
| 16 | Só a fórmula e dois blocos de leitura | O bloco da direita virou "mesma fórmula, notação trocada", com o aviso de que no CBOW `v` é contexto |
| 17 | Produtória → `-\log` em um `align` grande, repetindo o slide 12 | Comparação lado a lado "skip-gram: `2m` termos" × "CBOW: 1 termo", com o que se ganha e o que se perde |
| 18 | Log do CBOW + outra fórmula (repetia o slide 14) | Um só gradiente com o fator `1/(2m)` e a corrente "média → derivada → ajuste repartido" |
| 19 | 24 linhas de código em 6,5 pt | 14 linhas em 7 pt, ao lado dos 4 passos do slide 10 e do aviso do custo `N` |

Na seção de pré-treino (15.3–15.4), o bloco deixou de ter 9 slides:

- o dataset (PTB) virou uma linha dentro do **mapa do caminho**;
- o **minibatch** (quatro tensores) e o **laço de treino** foram para o *Backup*,
  que fica depois do "obrigado";
- o **modelo** perdeu os formatos dos tensores e ficou com o argumento que importa:
  "não há softmax, o custo não depende de |V|";
- a **subamostragem** ganhou a régua numérica (f = 10⁻² ⇒ 90% de descarte) e os
  **exemplos** ganharam a escala (≈ 9 milhões de exemplos por época).

O total caiu de 77 para **73 slides de conteúdo** (+2 no *backup*). Depois da
revisão, foi acrescentada a seção 16.3 (ver abaixo) e o slide do GloVe 2/2 foi
cortado no Overleaf, o que deixa **76 slides de conteúdo** (+2 no *backup*).
Depois, a seção 16.3 foi enxugada no Overleaf (saíram o slide de camadas e
formatos, o do código e o de resultados) e recebeu o pooling, a arquitetura
completa e o fluxo de dados, o que deixa **75 slides de conteúdo** (+2 no *backup*).

## Seção 16.3: análise de sentimento com CNN

Bloco de 5 slides, colocado depois de 16.2 e antes das referências.
O fio condutor é um só: **a pergunta muda** — a RNN quer o resumo da frase, a
CNN quer saber quais padrões locais aparecem e qual é o mais forte.

| Slide | O que mostra |
|---|---|
| 1 | A matemática da convolução 1D: a lupa que desliza, input/kernel/output e a conta $0\cdot1+1\cdot2=2$ |
| 2 | A arquitetura textCNN na prática: RNN $\times$ CNN, paralelismo e o fluxo GloVe $\to$ CNN $\to$ classificação |
| 3 | Max-over-time: muitos números, um resumo (o pico como "filtro de importância") |
| 4 | A arquitetura completa do textCNN (Fig. 16.3.5), com as convoluções de largura 2 e 4 em destaque |
| 5 | O fluxo de dados: $T-k+1$, a concatenação, o MLP e o Dropout, sobre o topo da Fig. 16.3.5 |

As figuras 16.3.1 e 16.3.2 do livro foram redesenhadas em TikZ, no mesmo traço
das outras figuras do tema. A Figura 16.3.5 é a **original** do D2L, em PNG
(`img/d2l_textcnn.png` e o recorte `img/d2l_textcnn_topo.png`), com os destaques
e os números desenhados por cima em TikZ.

Cada slide tem `\note`, no mesmo tom das seções 02–08. Foram acrescentadas as
referências `kim2014convolutional` e `collobert2011natural`.

## Compilar no Overleaf

1. **New Project → Upload Project** e envie `Apresentacao-NLP-v2.zip`
   (ou a pasta `Apresentacao NLP v2` inteira).
2. Confirme que o *main document* é `main.tex` e o compilador é **pdfLaTeX**.
3. Compile. Na primeira vez o Overleaf baixa os pacotes.

> Sem compilador local, a revisão foi validada por checagem estática
> (ambientes, chaves, `$`, `\left`/`\right` e citações).

## Como esta pasta se liga ao GitHub e ao Overleaf

Esta pasta é uma **git subtree** do repositório `Mestrado_`, ligada ao
repositório [`apresentacao-nlp-v2`](https://github.com/pivo1/apresentacao-nlp-v2)
(remote `apresentacao-nlp-v2`), que por sua vez está ligado ao Overleaf. Os
comandos rodam **na raiz do `Mestrado_`**:

| Quero… | O que faço |
|---|---|
| Trazer o que mudou no Overleaf | `git subtree pull --prefix="CPE727 - APRENDIZADO PROFUNDO/Apresentacao NLP V2" apresentacao-nlp-v2 main` |
| Mandar o que mudei aqui | `git subtree push --prefix="CPE727 - APRENDIZADO PROFUNDO/Apresentacao NLP V2" apresentacao-nlp-v2 main`; depois, no Overleaf: *Pull GitHub changes into Overleaf* |
| Ver o histórico | `git log --oneline -- "CPE727 - APRENDIZADO PROFUNDO/Apresentacao NLP V2"` |

## Plano para 60 minutos

São **75 slides de conteúdo**, mais 2 de *backup* (depois do "obrigado"). Roteiro
sugerido (numeração do PDF):

| Slides | Bloco | Tempo |
|---|---|---|
| 1–2 | Abertura e roteiro | 1,5 min |
| 3–19 | Motivação, skip-gram e CBOW | 14 min |
| 20–28 | Treinamento aproximado (15.2) | 7 min |
| 29–34 | Pré-treino na prática (15.3–15.4) | 5 min |
| 35–44 | GloVe (15.5) | 7 min |
| 45–50 | Subword: fastText e BPE (15.6) | 4,5 min |
| 51–52 | Similaridade e analogia (15.7) | 2,5 min |
| 53–65 | BERT (15.8) | 10 min |
| 66–72 | Análise de sentimento com RNN (16.2) | 5 min |
| 73–77 | Análise de sentimento com CNN (16.3) | 4 min |
| | **Total** | **~60 min** |

O bloco de 16.3 entra com ~4 min, e o roteiro fica em ~60 min. Se o limite for
apertado, os candidatos naturais a "passar rápido" são o slide 19 (código) e o
61 (MLM no código) — os dois são de apoio, e a mensagem de cada um já aparece
no slide vizinho.

Os dois slides de *backup* (minibatch e laço de treino) ficam depois do
"obrigado" e só entram se alguém perguntar de implementação.

## Atenção

- **Notas de apresentação (`Notas_Apresentacao_NLP.docx`)**: o documento tem
  slides a mais que o `.tex` (a "função de perda em três passos" e o "Resumo:
  Skip-gram ou CBOW"), então a numeração dele está adiantada em relação ao PDF.
  As seções dos slides 13, 14, 17 e 18 descrevem os slides **antigos**; a
  revisão dessas seções está em
  `Notas Apresentacao NLP/Notas_revisadas_slides_13_a_20.md`.
- **Imagens**: só as duas usadas (`dexpi_logo.png` e
  `d2l_sentimento_rnn_treino.png`) estão aqui; a foto de fundo que não é usada
  no `.tex` ficou de fora para o projeto subir leve.
