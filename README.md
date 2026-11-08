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

O total caiu de 77 para **73 slides de conteúdo** (+2 no *backup*).

## Compilar no Overleaf

1. **New Project → Upload Project** e envie `Apresentacao-NLP-v2.zip`
   (ou a pasta `Apresentacao NLP v2` inteira).
2. Confirme que o *main document* é `main.tex` e o compilador é **pdfLaTeX**.
3. Compile. Na primeira vez o Overleaf baixa os pacotes.

> Sem compilador local, a revisão foi validada por checagem estática
> (ambientes, chaves, `$`, `\left`/`\right` e citações).

## Como esta pasta se liga ao GitHub e ao Overleaf

Esta pasta **é um clone** do repositório
[`apresentacao-nlp-v2`](https://github.com/pivo1/apresentacao-nlp-v2). O
repositório `Mestrado_` **ignora** esta pasta (está no `.gitignore` dele), então
não existe mais `git subtree`: o versionamento é git normal, dentro da pasta.

| Quero… | O que faço |
|---|---|
| Trazer o que mudou no Overleaf | No Overleaf: *Integrations → GitHub → Push Overleaf changes to GitHub*. Aqui: `git pull` **dentro desta pasta** |
| Mandar o que mudei aqui | `git add`, `git commit` e `git push` **dentro desta pasta**; depois, no Overleaf: *Pull GitHub changes into Overleaf* |
| Ver o histórico | `git log --oneline` dentro desta pasta |

O Overleaf continua ligado ao repositório do GitHub, como antes — só não há mais
o passo intermediário de `git subtree pull/push` no `Mestrado_`.

## Plano para 60 minutos

São **73 slides de conteúdo**, mais 2 de *backup* (depois do "obrigado"). Roteiro
sugerido (numeração do PDF):

| Slides | Bloco | Tempo |
|---|---|---|
| 1–2 | Abertura e roteiro | 1,5 min |
| 3–19 | Motivação, skip-gram e CBOW | 14 min |
| 20–28 | Treinamento aproximado (15.2) | 7 min |
| 29–34 | Pré-treino na prática (15.3–15.4) | 5 min |
| 35–45 | GloVe (15.5) | 8 min |
| 46–51 | Subword: fastText e BPE (15.6) | 4,5 min |
| 52–53 | Similaridade e analogia (15.7) | 2,5 min |
| 54–66 | BERT (15.8) | 10 min |
| 67–73 | Análise de sentimento (16.2) | 5 min |
| | **Total** | **~57,5 min** |

Se o tempo apertar, os candidatos naturais a "passar rápido" são o slide 19
(código), o 44 (o passo do GloVe com números) e o 62 (MLM no código): os três são
de apoio, e a mensagem de cada um já aparece no slide vizinho.

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
