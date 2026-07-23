---
title: "O milagre desmontado: Terence Tao, um blog e a arte de não aceitar coincidências"
date: 2026-07-23 16:00:00 -0300
categories: [Matemática, Miscelânea]
tags: [inteligência artificial, terence tao, álgebra, divulgação, blogs matemáticos]
math: true
description: Por que o contraexemplo da Conjectura Jacobiana parecia um milagre, e como ele se dissolve quando descobrimos que era apenas uma multiplicação disfarçada.
---

Há uma pergunta que separa o matemático do resto do mundo, e ela apareceu esta semana numa conversa pública entre Terence Tao e um *chatbot*. Diante do contraexemplo da Conjectura Jacobiana — aquele que [comentei aqui há dois dias]({% post_url 2026-07-22-conjectura-jacobiana-contraexemplo-ia %}) — Tao não perguntou "está certo?". Ele perguntou, em essência:

> *É notável que o jacobiano seja constante; isso é uma quantidade excepcional de cancelamento. Essa aplicação polinomial tem alguma simetria ou outra estrutura que torne o cancelamento menos milagroso?*

O leigo, diante de um resultado verificado, para. O matemático se incomoda. **Coincidências são suspeitas.** Se 1299 coeficientes se anulam ao mesmo tempo, alguma coisa está escondida ali — e essa coisa é mais interessante que o próprio resultado.

Este texto conta como o milagre foi desmontado. E o final é bonito: o contraexemplo que parecia caído do céu é, na verdade, uma operação que qualquer estudante do primeiro período conhece.

## Quem é Terence Tao

Nascido em Adelaide, Austrália, em 1975, Tao é provavelmente o matemático vivo mais conhecido fora da matemática. Aos dez anos participava de Olimpíadas Internacionais; aos vinte e um tinha doutorado em Princeton; aos vinte e quatro era professor titular na UCLA. Recebeu a Medalha Fields em 2006.

O que o distingue não é apenas a potência, mas a **amplitude**. Tao publica em análise harmônica, teoria dos números, combinatória aditiva, equações dispersivas, teoria ergódica, matrizes aleatórias, compressed sensing. Para nós que trabalhamos com EDPs dispersivas, ele é presença constante: quem estuda boa colocação para KdV, Schrödinger ou ondas encontra o nome dele em metade da bibliografia essencial.

## O blog

Em 2007, Tao começou o **[What's New](https://terrytao.wordpress.com/)**, e essa talvez seja sua contribuição mais subestimada.

O blog é um híbrido raro: anúncios de artigos próprios, notas de cursos completos, problemas em aberto, obituários, digestões de resultados alheios. E a característica que o torna singular — ele escreve o que a maioria dos matemáticos só diz em conversa de corredor: por que uma técnica funciona, onde está a dificuldade real, qual heurística sugeriu o caminho. É a parte que os artigos costumam apagar.

A seção "Career advice" contém um texto que eu recomendo a todo estudante que orientei, "[There's more to mathematics than rigour and proofs](https://terrytao.wordpress.com/career-advice/theres-more-to-mathematics-than-rigour-and-proofs/)": a tese de que o rigor é uma fase, não o destino, e que depois dela vem algo que só pode ser chamado de intuição educada.

## O milagre, quantificado

Voltemos ao contraexemplo. A aplicação $F:\mathbb{C}^3\to\mathbb{C}^3$ tem grau sete. Tao faz então uma conta que muda tudo:

Se $F$ tem grau $7$, cada entrada da matriz jacobiana tem grau até $6$, e o determinante — soma de produtos de três entradas — tem grau até $3\times 6 = 18$. Um polinômio de grau $18$ em três variáveis tem

$$
\binom{18+3}{3} = 1330
$$

coeficientes, dos quais $1329$ são não constantes. Para que $\det DF$ seja a constante $-2$, **todos** eles precisam se anular simultaneamente. Enquanto isso, uma aplicação genérica de grau sete em três variáveis tem apenas

$$
\binom{7+3}{3}\times 3 = 360
$$

parâmetros livres. Há ordens de grandeza mais equações do que incógnitas.

Conclusão de Tao: encontrar tal polinômio por força bruta é praticamente impossível. Ou o exemplo veio de uma estrutura, ou o universo conspirou. E o universo raramente conspira.

## A estrutura: era uma multiplicação

Aqui está a parte deliciosa. Considere três espaços muito simples:

- os polinômios **lineares** homogêneos $L(z,w) = az+bw$ — dois coeficientes;
- os polinômios **quadráticos** homogêneos $Q(z,w) = cz^2+dzw+ew^2$ — três coeficientes;
- os polinômios **cúbicos** homogêneos $C(z,w)$ — quatro coeficientes.

E considere a operação mais banal que existe entre eles: **multiplicar**.

$$
F(L,Q) := L\cdot Q .
$$

Em coordenadas, essa é uma aplicação polinomial de $\mathbb{C}^2\times\mathbb{C}^3$ em $\mathbb{C}^4$:

$$
F\bigl((a,b),(c,d,e)\bigr) = (ac,\; ad+bc,\; ae+bd,\; be).
$$

Nada mais que a multiplicação de polinômios que se aprende no ensino médio. Agora observe duas coisas.

**Primeira: essa aplicação não é injetiva, e sabemos exatamente por quê.** Uma cúbica genérica se fatora em três lineares, $C = L_1L_2L_3$. Para escrevê-la como (linear) $\times$ (quadrática), basta escolher **qual** dos três fatores fará o papel de $L$:

$$
(L_1,\,L_2L_3), \qquad (L_2,\,L_1L_3), \qquad (L_3,\,L_1L_2).
$$

Três escolhas, mesmo produto. A aplicação é genericamente **três para um** — e a não-injetividade, que parecia acidental, é apenas a liberdade de escolher um fator entre três.

**Segunda: ela é localmente injetiva.** Se $L$ e $Q$ não têm raiz comum, a raiz de $L$ é distinta das de $Q$. Perturbe um pouquinho o produto: as três raízes se mexem um pouquinho, mas nenhuma pula para o lugar da outra. Então, olhando só para o produto perturbado, você sabe dizer qual raiz era a "de $L$". Localmente, a escolha entre os três ramos é rígida; globalmente, ela não é. **Invertibilidade local sem invertibilidade global, em duas frases.**

## Os três pontos misteriosos, revelados

No post anterior, os três pontos que $F$ leva ao mesmo valor apareceram como coelhos tirados da cartola:

$$
P_0=\left(0,0,-\tfrac14\right),\quad
P_+=\left(1,-\tfrac32,\tfrac{13}{2}\right),\quad
P_-=\left(-1,\tfrac32,\tfrac{13}{2}\right).
$$

Refiz a mudança de coordenadas de Tao em álgebra simbólica para ver o que esses pontos são de fato. O resultado:

| Ponto | $L$ | $Q$ |
| :-: | :-: | :-: |
| $P_0$ | $w$ | $\bigl(z-\tfrac{w}{2}\bigr)\bigl(z+\tfrac{w}{2}\bigr)$ |
| $P_+$ | $z-\tfrac{w}{2}$ | $w\bigl(z+\tfrac{w}{2}\bigr)$ |
| $P_-$ | $z+\tfrac{w}{2}$ | $w\bigl(z-\tfrac{w}{2}\bigr)$ |

Os três pontos são as **três maneiras de fatorar a mesma cúbica**

$$
C(z,w) \;=\; w\left(z-\frac{w}{2}\right)\left(z+\frac{w}{2}\right) \;=\; z^2w-\frac{w^3}{4}
$$

como (linear) $\times$ (quadrática). Só isso. Aqueles números de aparência arbitrária — $-1/4$, $-3/2$, $13/2$ — são o que sobra de $w$, $z-w/2$ e $z+w/2$ depois de atravessarem a mudança de variáveis.

E o mais bonito: o primeiro coordenada de cada ponto ($0$, $1$, $-1$) é exatamente o coeficiente líder de $L$. O ponto $P_0$ tem primeira coordenada nula porque seu fator linear é $w$, cuja raiz está no infinito.

O milagre evaporou.

## O que sobra de milagroso

Seria desonesto sugerir que tudo se dissolveu. Restam duas surpresas que o próprio Tao classifica como milagres, e ele é explícito ao dizer que não tem uma explicação geométrica inteiramente satisfatória para a primeira.

O problema é que a construção acima vive numa variedade de dimensão errada, e é preciso cortá-la até dimensão três **sem estragar nada** — em particular, o pedaço restante precisa ser isomorfo a $\mathbb{C}^3$ por mudanças polinomiais de variável, que é a condição realmente difícil. Tao mostra que há essencialmente três maneiras de fazer o corte, e o milagre acontece em exatamente uma delas.

O segundo milagre é mais concreto e dá para apreciar sem álgebra: no corte certo, aparece um sistema de duas equações,

$$
cb^2 = 1, \qquad bc = 1,
$$

uma cúbica e uma quadrática. O teorema de Bézout permitiria até $3\times 2 = 6$ soluções. Este sistema tem **exatamente uma**: $b=c=1$. É essa unicidade inesperada que faz a peça se encaixar.

Há ainda um detalhe de estilo que me encantou. Para tratar o limite delicado da construção, Tao anuncia que, dada sua formação, prefere trocar a maquinaria de ideais da geometria algébrica pela notação $O(\cdot)$ da análise — e conduz o argumento inteiro com estimativas do tipo $bc = 1+O(a)$, como quem faz análise assintótica. Um analista fazendo geometria algébrica com as ferramentas de casa.

## O que a IA fez, exatamente

Vale ler a nota que Tao coloca ao final do post, porque ela contrasta com o entusiasmo das redes sociais. Em tradução livre, ele declara ter usado um *chatbot* para **discutir vários aspectos do problema e confirmar diversos cálculos** feitos ali.

Discutir e confirmar. Não descobrir, não demonstrar. A conversa que viralizou não mostra uma máquina resolvendo um problema; mostra um matemático usando uma ferramenta para acelerar verificações e testar formulações enquanto **ele** persegue uma ideia. A pergunta que abre este texto — "há alguma simetria que torne isso menos milagroso?" — não veio da máquina. Ela é o trabalho.

Talvez seja esse o motivo real pelo qual a transcrição fascinou tanta gente: não é um espetáculo de inteligência artificial, é um raro registro público de **como um grande matemático pensa em tempo real**, com todos os becos sem saída incluídos. Coisa que artigos publicados são projetados para esconder.

## Por que o blog importa: o caso Kakeya

Hoje, 23 de julho de 2026, a União Matemática Internacional anunciou na Filadélfia as Medalhas Fields. Entre os laureados está **Hong Wang**, da NYU e do IHES, pela resolução da conjectura de Kakeya em três dimensões — a terceira mulher a receber a medalha.

O problema, formulado por Sōichi Kakeya em 1917, pergunta quão pequeno pode ser um conjunto que contenha um segmento unitário em **todas** as direções. Tais conjuntos podem ter medida nula; a conjectura afirmava que, ainda assim, sua dimensão de Hausdorff deve ser máxima. Wang e Joshua Zahl provaram o caso tridimensional em fevereiro de 2025, num preprint de 127 páginas.

E aqui entra o blog — não como nota de rodapé, mas como ponto de partida.

Foi no Institute for Advanced Study, durante a pandemia, que Wang decidiu voltar sua atenção para a conjectura de Kakeya em três dimensões. O problema já havia resistido a décadas de tentativas; Larry Guth, seu orientador de doutorado, chegou a contar que por quatro ou cinco vezes achou tê-lo resolvido, descobrindo o erro antes de tornar público. O que mudou o jogo foi uma leitura: Wang leu um **post de 2014 do What's New** em que Tao expunha uma estratégia de demonstração que ele e Nets Katz haviam desenvolvido mas nunca perseguido até o fim. A abordagem pareceu promissora. Ela então procurou Joshua Zahl, que estudara aspectos do problema em sua tese, e os dois decidiram investigar o que Katz e Tao haviam descrito. A estratégia, que acabou exigindo um arsenal enorme de técnicas, levou às 127 páginas de 2025.

Vale deixar isso bem assentado, porque é fácil subestimar: uma ideia parcial, abandonada por seus autores, ficou dez anos disponível num blog — pesquisável, datada, citável — até que alguém com as ferramentas certas a encontrasse. Sem o blog, ela provavelmente teria permanecido num caderno de rascunhos em Los Angeles.

E há o segundo momento, no sentido inverso: no dia seguinte à publicação do preprint, Tao escreveu no blog uma digestão detalhada do argumento de Wang e Zahl. Foi por ali que boa parte da comunidade — inclusive eu — entendeu a arquitetura da prova antes de encarar o artigo completo.

O blog funcionou, portanto, como **infraestrutura** nas duas direções: guardou por uma década a estratégia que deu origem ao programa de pesquisa e, no fim, traduziu o resultado para a comunidade em vinte e quatro horas. Nenhuma dessas duas funções cabe no sistema tradicional de publicação.

## Moral da história

Três lições que levo deste episódio, e que valem para quem faz pesquisa em qualquer área:

**Desconfie das coincidências.** Um cancelamento improvável não é sorte: é uma estrutura ainda não identificada. A pergunta "por que isso funciona?" costuma render mais que o próprio resultado.

**Procure a operação escondida.** O objeto mais assustador deste episódio — um polinômio de grau sete com 1329 coeficientes conspirando — era a multiplicação de uma reta por uma cônica. Objetos complicados são, frequentemente, objetos simples em coordenadas ruins.

**Escreva em público.** Um post de blog de 2014, sobre uma estratégia que seus próprios autores haviam abandonado, foi lido durante uma pandemia e deu origem a uma Medalha Fields em 2026. Não há como saber de antemão qual anotação vai germinar na cabeça de outra pessoa — só há como deixá-la ao alcance.

---

*Este texto foi escrito no dia do anúncio das Medalhas Fields de 2026. As verificações simbólicas das fatorações apresentadas na tabela foram feitas por mim em* `SymPy`*, a partir da mudança de variáveis do post de Tao.*

## Referências

1. T. Tao, *A digestion of the Jacobian conjecture counterexample*, What's new, 21 de julho de 2026. [terrytao.wordpress.com](https://terrytao.wordpress.com/2026/07/21/a-digestion-of-the-jacobian-conjecture-counterexample/)
2. T. Tao, *The three-dimensional Kakeya conjecture, after Wang and Zahl*, What's new, 25 de fevereiro de 2025.
3. H. Wang e J. Zahl, *Volume estimates for unions of convex sets, and the Kakeya set conjecture in three dimensions*, preprint, fevereiro de 2025.
4. J. Howlett, *Hong Wang Wins 2026 Fields Medal, the Third Woman Ever*, Quanta Magazine, 23 de julho de 2026.
5. *Hong Wang: On Solving Kakeya and Rethinking Restriction*, entrevista, Centre de Recerca Matemàtica, 2025.
6. União Matemática Internacional, anúncio das Medalhas Fields, Filadélfia, 23 de julho de 2026.
