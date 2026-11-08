# Apresentação de PLN — versão 2 (revisão didática)

Cópia da apresentação original (`Apresentacao NLP`), criada para poder revisar os
slides **sem conflito** com a versão que já está pronta e commitada.

- Mesmo tema (DEXPI), mesmas cores, mesmos blocos e mesmos *cards* do slide 12.
- A revisão mexe só no **conteúdo** de 7 slides da seção 01 (word2vec/CBOW).
- Nada foi renomeado, nenhum `\usepackage` novo, nenhuma mudança de tema.

## O que mudou, slide por slide

| Slide | Antes | Agora |
|---|---|---|
| 13 | Título "Otimizando com SGD", três *bullets* e uma fórmula solta no meio | Três *cards* numerados (trecho / par / passo), a fórmula do log com os dois termos comentados e uma caixa "as duas metades puxam em sentidos opostos" |
| 14 | Derivação em três linhas de `align`, sem exemplo e sem figura | Duas regras de derivada, o resultado "observado − esperado", um exemplo numérico (`N=3`, `d=2`) e a figura da seta do *esperado* até o *observado* |
| 16 | Só a fórmula e dois blocos de leitura | Ganhou a caixa "cuidado com a notação do D2L" (no CBOW, `v` é contexto) |
| 17 | Produtória → `-\log` em um `align` grande, repetindo o slide 12 | Comparação lado a lado "skip-gram: `2m` termos" × "CBOW: 1 termo", com o que se ganha e o que se perde |
| 18 | Log do CBOW + outra fórmula (repetia o slide 14) | Um só gradiente com o fator `1/(2m)` e a corrente "média → derivada → ajuste repartido" |
| 19 | Gradiente do CBOW com a fração expandida (terceira repetição) | Tabela-resumo skip-gram × CBOW + a regra de qual vetor usar como embedding |
| 20 | 24 linhas de código em 6,5 pt | 14 linhas em 7 pt, ao lado dos 4 passos do slide 10 e do aviso do custo `N` |

A ordem e a quantidade de slides **não mudaram**: a seção 01 continua com 18
frames, e o total continua 77 slides de conteúdo + referências + slide final.

## Compilar no Overleaf

1. **New Project → Upload Project** e envie `Apresentacao-NLP-v2.zip`
   (ou a pasta `Apresentacao NLP v2` inteira).
2. Confirme que o *main document* é `main.tex` e o compilador é **pdfLaTeX**.
3. Compile. Na primeira vez o Overleaf baixa os pacotes.

> Sem compilador local, a revisão foi validada por checagem estática
> (ambientes, chaves, `$`, `\left`/`\right` e citações). Os três slides com
> TikZ novo (13, 14 e 18) são os que merecem uma olhada na tela para conferir
> se nada passou da margem.

## Ligar com uma subtree nova no GitHub

O repositório novo precisa ser **vazio** (sem README, sem `.gitignore`), senão o
primeiro `git subtree push` é rejeitado por histórico não relacionado.

```bash
# 1) crie no GitHub o repo vazio: pivo1/apresentacao-nlp-v2

# 2) em Mestrado_ (não dentro desta pasta)
git remote add apresentacao-nlp-v2 https://github.com/pivo1/apresentacao-nlp-v2.git

git add "CPE727 - APRENDIZADO PROFUNDO/Apresentacao NLP v2"
git commit -m "Adiciona versao 2 da apresentacao de PLN"

git subtree push --prefix="CPE727 - APRENDIZADO PROFUNDO/Apresentacao NLP v2" apresentacao-nlp-v2 main
```

Depois, no Overleaf: **New Project → Import from GitHub** e escolha
`apresentacao-nlp-v2`. É um projeto **separado** do atual, então nada do que já
está pronto é tocado.

### Sincronização no dia a dia

| Editei onde | O que rodar |
|---|---|
| No Overleaf | Menu → GitHub → *Push Overleaf changes to GitHub*, depois `git subtree pull --prefix="CPE727 - APRENDIZADO PROFUNDO/Apresentacao NLP v2" apresentacao-nlp-v2 main -m "Sincroniza v2"` |
| No computador | commit normal e `git subtree push --prefix="CPE727 - APRENDIZADO PROFUNDO/Apresentacao NLP v2" apresentacao-nlp-v2 main` |

## Plano para 60 minutos

São 77 slides de conteúdo. Roteiro sugerido (a numeração é a do PDF):

| Slides | Bloco | Tempo |
|---|---|---|
| 1–2 | Abertura e roteiro | 1,5 min |
| 3–20 | Motivação, skip-gram e CBOW | 15 min |
| 21–29 | Treinamento aproximado (15.2) | 7 min |
| 30–38 | Pré-treino na prática (15.3–15.4) | 7 min |
| 39–49 | GloVe (15.5) | 8 min |
| 50–55 | Subword: fastText e BPE (15.6) | 4,5 min |
| 56–57 | Similaridade e analogia (15.7) | 2,5 min |
| 58–70 | BERT (15.8) | 9 min |
| 71–77 | Análise de sentimento (16.2) | 5 min |
| | **Total** | **~59,5 min** |

Se o tempo apertar, os candidatos naturais a "passar rápido" são o slide 20
(código), o 49 (passo do GloVe com números) e o 67 (MLM no código): os três são
de apoio, e a mensagem de cada um já aparece no slide vizinho.

## Atenção

- **Notas de apresentação (`Notas_Apresentacao_NLP.docx`)**: o documento tem um
  slide a mais que o `.tex` ("A função de perda em três passos", removido na
  versão atual), então do slide 27 em diante a numeração dele está adiantada em
  1 (nas referências e no slide final a diferença pode ser maior, porque as
  referências ocupam várias páginas). As seções dos slides 13, 14, 17, 18 e 19
  descrevem os slides **antigos**; a revisão dessas seções está em
  `Notas Apresentacao NLP/Notas_revisadas_slides_13_a_20.md`.
- **Imagens**: só as duas usadas (`dexpi_logo.png` e
  `d2l_sentimento_rnn_treino.png`) foram copiadas; a foto de fundo que não é
  usada no `.tex` ficou de fora para o projeto subir leve no Overleaf.
