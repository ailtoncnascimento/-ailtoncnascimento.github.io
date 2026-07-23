---
title: "Um contraexemplo para a conjectura de Goemans sobre fluxos não-divisíveis"
date: 2026-07-23 09:00:00 -0300
categories: [Matemática, Curiosidades]
tags: [inteligência artificial, teoria dos grafos, otimização combinatória, fluxos em redes]
math: true
description: Um grafo com 7 nós e 9 arcos, anunciado em julho de 2026, parece refutar uma conjectura aberta desde os anos 1990. Aqui verificamos o exemplo por enumeração exaustiva.
---

Menos de uma semana depois do episódio envolvendo a [Conjectura Jacobiana]({% post_url 2026-07-22-conjectura-jacobiana-contraexemplo-ia %}), um segundo anúncio do mesmo gênero circulou nas redes sociais. Em 22 de julho de 2026, o pesquisador **Dmitry Rybin** divulgou um grafo com **sete nós e nove arcos** que parece refutar uma conjectura de otimização combinatória em aberto desde os anos 1990 — encontrado, segundo ele, com o auxílio de um modelo de inteligência artificial.

Diferentemente do caso anterior, aqui não é preciso confiar em ninguém. O contraexemplo é **finito e pequeno**: há exatamente oito maneiras de rotear a demanda, e podemos simplesmente examinar todas. Foi o que fiz, com ajuda de LLM,  e o relato desta verificação é o conteúdo principal deste texto.

## O problema do fluxo não-divisível

Imagine um centro de distribuição $s$ que precisa atender três clientes $t_1$, $t_2$, $t_3$, com demandas $d_{t_1}, d_{t_2}, d_{t_3}$. A mercadoria trafega por uma rede de estradas — um grafo dirigido $G=(V,A)$ — em que cada arco $e$ possui uma **capacidade** $u_e$ e um **custo** unitário $c_e$.

Há duas modalidades de transporte:

- No **fluxo fracionário** (ou divisível), a carga de um cliente pode ser repartida entre vários caminhos: metade pela rodovia, metade pela estrada vicinal.
- No **fluxo não-divisível** (*unsplittable*), a demanda de cada cliente deve percorrer **um único caminho**, do início ao fim.

A segunda modalidade é mais realista em muitas aplicações — não se corta um contêiner ao meio — e é também combinatorialmente muito mais rígida. A pergunta natural é: quanto se perde ao exigir a indivisibilidade?

Formalmente, dado um fluxo fracionário viável $x=(x_e)_{e\in A}$, procura-se um fluxo não-divisível $y=(y_e)_{e\in A}$ que se pareça o máximo possível com $x$.

## O teorema de Dinitz, Garg e Goemans

A resposta clássica é um resultado notável de **Yefim Dinitz, Naveen Garg e Michel Goemans**, publicado na *Combinatorica* em 1999.

> **Teorema (DGG, 1999).** Se existe um fluxo fracionário viável, então existe um fluxo não-divisível que viola cada capacidade em no máximo $d_{\max}$, a maior das demandas.

Ou seja: a passagem para a indivisibilidade custa, em termos de congestionamento, **no máximo uma remessa a mais** por estrada. O que impressiona é a universalidade — o limite não depende do tamanho do grafo, do número de clientes nem da estrutura da rede.

## A conjectura de Goemans

Resolvido o congestionamento, resta a pergunta econômica: e o **custo**? Goemans propôs, por volta de 1997, a versão natural do teorema anterior:

> **Conjectura (Goemans).** Existe um fluxo não-divisível que, simultaneamente,
> 1. viola cada capacidade em no máximo $d_{\max}$, e
> 2. tem custo **não superior** ao custo do fluxo fracionário.

A palavra decisiva é *simultaneamente*. Separadamente, cada exigência é fácil de satisfazer: o teorema DGG entrega a primeira, e a segunda se obtém trivialmente roteando tudo pelos caminhos mais baratos (ao preço de congestionar a rede). A conjectura afirmava que as duas metas são compatíveis.

A conjectura permaneceu aberta por quase três décadas. Como observam Traub, Vargas Koch e Zenklusen em trabalho de 2023, o estado da arte era ainda mais desconfortável do que a expressão "problema em aberto" sugere: não se conhecia sequer uma classe não-trivial de grafos para a qual a conjectura fosse sabidamente verdadeira.

**Uma nota de nomenclatura.** O anúncio circulou sob o nome "conjectura de Dinitz–Garg–Goemans", e assim ficou conhecido nas redes. A rigor, o resultado dos três autores é o **teorema** citado acima; a versão com custo é atribuída a **Goemans** individualmente. Neste texto uso a atribuição da literatura.

## O contraexemplo

O grafo proposto tem sete nós — a fonte $s$, três terminais $t_1,t_2,t_3$ e três nós intermediários $u,v,w$ — e nove arcos. As demandas são

$$
d_{t_1}=15, \qquad d_{t_2}=10, \qquad d_{t_3}=15,
\qquad\text{portanto}\qquad d_{\max}=15 .
$$

A capacidade de cada arco é **exatamente** o valor do fluxo fracionário que o percorre (isto é, o fluxo fracionário satura a rede inteira). Apenas três arcos têm custo não nulo.

<div style="overflow-x:auto">
<svg viewBox="0 0 700 470" xmlns="http://www.w3.org/2000/svg" style="max-width:100%;height:auto">
  <defs>
    <marker id="seta" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="currentColor"/>
    </marker>
  </defs>
  <g stroke="currentColor" stroke-width="2" fill="none" marker-end="url(#seta)">
    <path d="M 331,53 Q 160,58 103,175"/>
    <path d="M 350,63 L 350,150"/>
    <path d="M 370,52 Q 600,55 604,285"/>
    <path d="M 577,310 L 380,310"/>
    <path d="M 355,287 L 355,200"/>
    <path d="M 332,310 L 210,310"/>
    <path d="M 172,290 L 112,220"/>
    <path d="M 185,333 L 185,395"/>
    <path d="M 588,332 Q 450,468 211,424"/>
  </g>
  <g fill="none" stroke="currentColor" stroke-width="2">
    <circle cx="350" cy="40" r="23"/>
    <circle cx="350" cy="175" r="23"/>
    <circle cx="95" cy="195" r="23"/>
    <circle cx="185" cy="310" r="23"/>
    <circle cx="355" cy="310" r="23"/>
    <circle cx="600" cy="310" r="23"/>
    <circle cx="185" cy="418" r="23"/>
  </g>
  <g fill="currentColor" font-family="serif" font-style="italic" font-size="19" text-anchor="middle">
    <text x="350" y="47">s</text>
    <text x="350" y="182">t₁</text>
    <text x="95" y="202">t₂</text>
    <text x="185" y="317">w</text>
    <text x="355" y="317">v</text>
    <text x="600" y="317">u</text>
    <text x="185" y="425">t₃</text>
  </g>
  <g font-family="sans-serif" font-size="14" text-anchor="middle">
    <g fill="#2563eb">
      <text x="205" y="52">6</text>
      <text x="333" y="112">10</text>
      <text x="512" y="52">24</text>
      <text x="478" y="300">14</text>
      <text x="371" y="248">5</text>
      <text x="270" y="300">9</text>
      <text x="152" y="248">4</text>
      <text x="200" y="368">5</text>
      <text x="410" y="415">10</text>
    </g>
    <g fill="#dc2626">
      <text x="205" y="72">3</text>
      <text x="368" y="132">2</text>
      <text x="410" y="435">2</text>
    </g>
  </g>
  <g font-family="sans-serif" font-size="12" fill="currentColor">
    <text x="378" y="160">d = 15</text>
    <text x="20" y="230">d = 10</text>
    <text x="110" y="450">d = 15</text>
  </g>
  <g font-family="sans-serif" font-size="13" text-anchor="start">
    <text x="540" y="425" fill="#2563eb">capacidade</text>
    <text x="540" y="445" fill="#dc2626">custo</text>
  </g>
</svg>
</div>

Em forma de tabela:

| Arco | Capacidade $u_e$ | Custo $c_e$ |
| :-- | :-: | :-: |
| $s\to t_1$ | 10 | 2 |
| $s\to t_2$ | 6 | 3 |
| $s\to u$ | 24 | 0 |
| $u\to v$ | 14 | 0 |
| $u\to t_3$ | 10 | 2 |
| $v\to t_1$ | 5 | 0 |
| $v\to w$ | 9 | 0 |
| $w\to t_2$ | 4 | 0 |
| $w\to t_3$ | 5 | 0 |

A conservação do fluxo se verifica de imediato: a fonte despacha $6+10+24=40$, que é a demanda total; em $u$ entram $24$ e saem $14+10=24$; em $v$ entram $14$ e saem $5+9=14$; em $w$ entram $9$ e saem $4+5=9$. Os terminais recebem $10+5=15$, $6+4=10$ e $5+10=15$, exatamente suas demandas.

O custo do fluxo fracionário é

$$
10\cdot 2 \;+\; 6\cdot 3 \;+\; 10\cdot 2 \;=\; 20+18+20 \;=\; \boxed{58}.
$$

## Só existem oito fluxos não-divisíveis

Aqui está a beleza do exemplo. Cada terminal é alcançável por **exatamente dois** caminhos a partir de $s$:

$$
\begin{aligned}
t_1 &: \quad s\to t_1 \quad\text{ou}\quad s\to u\to v\to t_1,\\
t_2 &: \quad s\to t_2 \quad\text{ou}\quad s\to u\to v\to w\to t_2,\\
t_3 &: \quad s\to u\to t_3 \quad\text{ou}\quad s\to u\to v\to w\to t_3.
\end{aligned}
$$

Um fluxo não-divisível é precisamente uma escolha de um caminho por terminal. Logo há $2\times 2\times 2 = 8$ fluxos não-divisíveis, e **podemos examinar todos**.

Note ainda que o primeiro caminho de cada par é o "caro" (custo total $15\cdot 2=30$, $10\cdot 3=30$ e $15\cdot 2=30$, respectivamente) e o segundo é gratuito. O custo de qualquer fluxo não-divisível é, portanto, $30$ vezes o número de rotas caras escolhidas: só pode valer $0$, $30$, $60$ ou $90$.

Eis a enumeração completa, com a violação máxima de capacidade de cada opção:

| $t_1$ | $t_2$ | $t_3$ | Custo | Violação | Gargalo |
| :-: | :-: | :-: | :-: | :-: | :-- |
| longo | longo | longo | 0 | **26** | $u\to v$ recebe 40 (cap. 14) |
| direto | longo | longo | 30 | **16** | $v\to w$ recebe 25 (cap. 9) |
| longo | direto | longo | 30 | **16** | $u\to v$ recebe 30 (cap. 14) |
| longo | longo | curto | 30 | **16** | $s\to u$ recebe 40 (cap. 24) |
| direto | longo | curto | 60 | 6 | $w\to t_2$ recebe 10 (cap. 4) |
| longo | direto | curto | 60 | 10 | $v\to t_1$ recebe 15 (cap. 5) |
| direto | direto | longo | 60 | 10 | $w\to t_3$ recebe 15 (cap. 5) |
| direto | direto | curto | 90 | 5 | $s\to t_1$ recebe 15 (cap. 10) |

A leitura é imediata. Os quatro roteamentos baratos (custo $0$ ou $30$) violam alguma capacidade em $16$ ou mais — acima de $d_{\max}=15$. Entre os que respeitam o limite de $15$, o custo mínimo é $60$. Portanto:

$$
\boxed{\ \text{custo fracionário} = 58 \qquad\text{mas}\qquad \min\{\text{custo}: \text{violação}\le d_{\max}\} = 60. \ }
$$

Uma diferença de duas unidades basta para refutar a conjectura. É digno de nota que as três violações fatais valem exatamente $16 = d_{\max}+1$: o exemplo é apertado, construído para falhar pela menor margem possível.

## Verificação por computador

O leitor pode reproduzir a enumeração em poucas linhas:

```python
from itertools import product

arcs = {('s','t1'): (10, 2), ('s','t2'): ( 6, 3), ('s','u') : (24, 0),
        ('u','v') : (14, 0), ('u','t3'): (10, 2), ('v','t1'): ( 5, 0),
        ('v','w') : ( 9, 0), ('w','t2'): ( 4, 0), ('w','t3'): ( 5, 0)}
dem  = {'t1': 15, 't2': 10, 't3': 15}
dmax = max(dem.values())

adj = {}
for (a, b) in arcs:
    adj.setdefault(a, []).append(b)

def caminhos(u, alvo, vis=()):
    if u == alvo:
        yield (u,); return
    for v in adj.get(u, []):
        if v not in vis:
            for p in caminhos(v, alvo, vis + (u,)):
                yield (u,) + p

P = {t: list(caminhos('s', t)) for t in dem}
custo_frac = sum(cap * c for cap, c in arcs.values())

viaveis = []
for comb in product(P['t1'], P['t2'], P['t3']):
    carga = {}
    for t, p in zip(['t1', 't2', 't3'], comb):
        for e in zip(p, p[1:]):
            carga[e] = carga.get(e, 0) + dem[t]
    custo = sum(f * arcs[e][1] for e, f in carga.items())
    viol  = max(f - arcs[e][0] for e, f in carga.items())
    if viol <= dmax:
        viaveis.append(custo)

print("custo fracionario:", custo_frac)
print("menor custo com violacao <= d_max:", min(viaveis))
```

A saída é `custo fracionario: 58` e `menor custo com violacao <= d_max: 60`.

## O exemplo pertence a uma família infinita

Poucas horas após o anúncio, foi observado nas redes que o grafo não é um acidente isolado, mas um ponto de uma família a três parâmetros sobre os mesmos sete nós. Tome inteiros $b,m,g\ge 1$ com

$$
m \le b-g \qquad\text{e}\qquad m(b-m) > (b+m)\,g,
$$

e defina $d_{t_1}=d_{t_3}=b+m$, $d_{t_2}=b$, com capacidades

$$
\begin{array}{lll}
u_{s t_1}=b, & u_{s t_2}=m+g, & u_{s u}=2b+m-g,\\
u_{uv}=b+m-g, & u_{u t_3}=b, & u_{v t_1}=m,\\
u_{vw}=b-g, & u_{w t_2}=b-m-g, & u_{w t_3}=m,
\end{array}
$$

e custos $b$, $b+m$ e $b$ nos arcos $s\to t_1$, $s\to t_2$ e $u\to t_3$, nulos nos demais. O custo fracionário é então $2b^2+(b+m)(m+g)$.

Verifiquei essa família por enumeração para todos os parâmetros com $b\le 15$: encontrei **79** contraexemplos, o menor deles em $(b,m,g)=(7,2,1)$, com custo fracionário $125$ contra custo não-divisível mínimo $126$. O exemplo divulgado corresponde a $(b,m,g)=(10,5,1)$ — suas capacidades coincidem arco a arco, e o custo fracionário $2\cdot 100+15\cdot 6=290$ é exatamente cinco vezes $58$, pois multiplicar todos os custos por uma constante positiva não altera o problema.

Isso é reconfortante do ponto de vista epistêmico: um contraexemplo isolado poderia esconder um erro de transcrição; uma família paramétrica com estrutura algébrica clara, cujos membros foram verificados independentemente, é bem mais robusta.

## Não há conflito com os resultados conhecidos

Uma verificação que me pareceu obrigatória: o grafo do contraexemplo é **acíclico e planar**. Ora, Traub, Vargas Koch e Zenklusen provaram em 2024 resultados justamente para grafos planares acíclicos. Haveria contradição?

Não. O que eles provaram para grafos planares foi um enfraquecimento da conjectura, admitindo violações até duas vezes maiores — isto é, custo não superior ao fracionário com violação até $2d_{\max}$. E, de fato, o roteamento totalmente gratuito do nosso exemplo (custo $0 \le 58$) tem violação $26$, confortavelmente abaixo de $2d_{\max}=30$. O contraexemplo e o teorema convivem em paz.

Mais que isso: o contraexemplo esclarece *por que* aquele fator $2$ estava lá. Uma leitura natural, até ontem, era que a folga extra fosse um artefato técnico da demonstração, a ser removido por um argumento mais fino. O exemplo mostra que alguma folga é genuinamente necessária — o limite $d_{\max}$ da conjectura original é inatingível.

## O papel da inteligência artificial

Como no episódio da Conjectura Jacobiana, convém separar duas afirmações de naturezas bem diferentes.

**A primeira** é matemática: o grafo divulgado tem as propriedades anunciadas. Essa parte está estabelecida — não por autoridade, mas porque a enumeração das oito possibilidades é finita, elementar e reproduzível por qualquer leitor em cinco minutos.

**A segunda** é histórica: o quanto a inteligência artificial contribuiu. Aqui a avaliação é mais delicada. Diferentemente do caso anterior, o registro completo da interação foi tornado público, o que é um avanço metodológico considerável. Ainda assim, permanecem em aberto perguntas como: quantas tentativas incorretas antecederam o exemplo final? Qual o peso da formulação precisa do problema, feita por um especialista que declarou ter passado semanas pensando nele em ambas as direções? A intuição estrutural — de que valia a pena procurar um contraexemplo apertado, com violação $d_{\max}+1$ — veio da máquina ou do humano?

Vale registrar que o resultado **não passou por revisão científica** nem por verificação formal. Nada disso diminui a solidez do cálculo; apenas situa o anúncio no gênero a que pertence, que é o da comunicação em rede social, não o da publicação matemática.

## Uma observação sobre a assimetria

Os dois episódios desta semana ilustram bem uma assimetria antiga da matemática, que a chegada da inteligência artificial apenas tornou mais visível: **refutar pode ser radicalmente mais barato que demonstrar**.

Uma demonstração da conjectura de Goemans teria de contemplar todos os grafos, todas as demandas e todos os custos. Sua refutação coube em sete nós, nove arcos e oito verificações aritméticas. É exatamente o tipo de tarefa em que uma busca automatizada, capaz de percorrer rapidamente um espaço enorme de instâncias pequenas, tem vantagem estrutural sobre a intuição humana — que, por sua vez, tende a procurar o padrão geral, não a exceção minúscula.

Isso sugere uma divisão de trabalho, mais do que uma substituição. A máquina pode vasculhar o espaço das instâncias; cabe ao matemático formular o problema, reconhecer o que conta como contraexemplo e — a parte que continua inteiramente humana — **entender por que ele funciona**.

## Referências

1. Y. Dinitz, N. Garg e M. X. Goemans, *On the single-source unsplittable flow problem*, Combinatorica, vol. 19, n. 1, 1999, pp. 17–41.
2. V. Traub, L. Vargas Koch e R. Zenklusen, *Single-source unsplittable flows in planar graphs*, Proceedings of the 2024 ACM-SIAM Symposium on Discrete Algorithms (SODA), 2024, pp. 639–668. Pré-publicação: arXiv:2308.02651.
3. C. Swamy, V. Traub, L. Vargas Koch e R. Zenklusen, *Unsplittable cost flows from unweighted error-bounded variants*, SIAM Symposium on Simplicity in Algorithms (SOSA), 2026, pp. 512–523.
4. D. Rybin, anúncio público do contraexemplo, 22 de julho de 2026.

*Última verificação das fontes: 23 de julho de 2026.*
