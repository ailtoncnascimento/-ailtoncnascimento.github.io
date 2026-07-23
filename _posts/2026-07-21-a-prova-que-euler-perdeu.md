---
title: A prova que Euler perdeu
date: 2026-07-21 10:00:00 -0300
categories: [Matemática, Curiosidades]
tags: [euler, apéry, teoria dos números, função zeta, história]
math: true
description: Em 1979, uma demonstração da irracionalidade de ζ(3) apareceu usando ferramentas que Euler dominava dois séculos antes. E o caso geral segue aberto.
---

Em junho de 1978, numa conferência em Marselha, um matemático francês de sessenta e um anos chamado Roger Apéry subiu ao palco para anunciar que havia demonstrado a irracionalidade de

$$
\zeta(3) \;=\; \sum_{n=1}^{\infty}\frac{1}{n^{3}} \;=\; 1{,}20205690\ldots
$$

A plateia reagiu com ceticismo aberto. Apéry apresentou identidades sem justificativas, em francês, diante de um auditório impaciente; a certa altura, perguntado de onde vinha uma de suas fórmulas, respondeu apenas que ela "crescia no seu jardim". Vários presentes saíram convencidos de que assistiam a um constrangimento. Dois meses depois, quando as identidades foram verificadas numericamente e a demonstração reconstruída, ficou claro que Apéry estava certo — e que havia resolvido um problema aberto desde Euler.

Alfred van der Poorten registrou o episódio num artigo célebre, com o título que dá nome a este texto: *A proof that Euler missed*. Uma prova que Euler perdeu.

O adjetivo não é retórico. O que este texto quer mostrar é por que, com poucas exceções bem localizadas, **Euler tinha em mãos tudo de que precisava** — e ainda assim o resultado esperou duzentos anos. E por que, quase cinquenta anos depois de Apéry, a pergunta geral continua sem resposta.

*(Este texto é uma versão escrita da palestra que apresentei no ciclo THEoremas e THEorias do Departamento de Matemática da UFPI, em julho de 2024.)*

## Os números de Bernoulli

Precisamos primeiro de um elenco de números que aparecerá em toda parte.

Eles foram descobertos de forma independente por duas pessoas em lados opostos do mundo: o suíço **Jacob Bernoulli** (1655–1705), de quem receberam o nome, e o japonês **Seki Takakazu** (1642–1708). Curiosamente, ambas as descobertas foram publicadas postumamente e quase simultaneamente: Seki em 1712, na obra *Katsuyo Sanpo*; Bernoulli em 1713, no *Ars Conjectandi*.

A definição moderna é analítica e elegante. A função

$$
\frac{z}{e^{z}-1}
$$

tem singularidades mais próximas em $z=\pm 2\pi i$ e é, portanto, analítica no disco $\lvert z\rvert < 2\pi$. Podemos então expandi-la em série:

$$
\frac{z}{e^{z}-1}\;=\;\sum_{n=0}^{\infty} B_{n}\,\frac{z^{n}}{n!}.
$$

Os coeficientes $B_n$ são os **números de Bernoulli**. Os primeiros:

$$
B_0=1,\quad B_1=-\tfrac12,\quad B_2=\tfrac16,\quad B_3=0,\quad B_4=-\tfrac1{30},\quad B_5=0,\quad B_6=\tfrac1{42},\quad B_8=-\tfrac1{30},\quad B_{10}=\tfrac5{66}.
$$

Um padrão salta aos olhos: os de índice ímpar somem.

> **Proposição.** $B_{2k+1}=0$ para todo $k\ge 1$.

A demonstração cabe em três linhas e é bonita. Observe que

$$
\frac{t}{e^{t}-1}+\frac{t}{2}\;=\;\frac{t}{2}\coth\!\left(\frac{t}{2}\right)
$$

é uma função **par**. Mas o lado esquerdo é exatamente $\sum_{n\ne 1} B_n t^n/n!$, isto é, a série de Bernoulli com o único termo ímpar conhecido removido. Trocando $t$ por $-t$ e comparando coeficientes, obtemos $(-1)^n B_n = B_n$ para todo $n\ne 1$, o que força $B_n=0$ quando $n$ é ímpar maior que $1$. $\blacksquare$

Guarde essa paridade. Ela vai reaparecer, e a assimetria entre pares e ímpares que ela introduz não é acidente: é o coração de toda esta história.

## A função zeta

A **função zeta de Riemann** é definida por

$$
\zeta(z)=\sum_{k=1}^{\infty}\frac{1}{k^{z}}.
$$

Escrevendo $z=x+iy$, temos $\lvert k^{-z}\rvert = k^{-x}$, de modo que a série converge absolutamente no semiplano $x>1$ e, pelo teste de Weierstrass, uniformemente em compactos desse semiplano. A função se estende analiticamente a todo o plano complexo exceto $z=1$, onde há um polo simples de resíduo $1$ — afinal, em $z=1$ a série é a harmônica, que diverge.

A ponte com a seção anterior é esta:

$$
\zeta(-n)=-\frac{B_{n+1}}{n+1},
$$

de onde $\zeta(0)=-\tfrac12$ e, mais interessante, $\zeta(-2n)=0$ para todo natural $n$ — os chamados **zeros triviais**, que existem precisamente porque os Bernoulli de índice ímpar se anulam.

Os outros zeros — os não triviais — são o objeto da **Hipótese de Riemann**, formulada em 1859 no artigo *Über die Anzahl der Primzahlen unter einer gegebenen Grösse*: todos eles teriam parte real $1/2$. É um dos sete Problemas do Milênio, com prêmio de um milhão de dólares do Instituto Clay, e considerado por muitos o problema aberto mais importante da matemática. Não é dele que trataremos aqui — mas vale registrar que a função que estamos prestes a examinar carrega esse peso.

Antes de Riemann, porém, veio Euler. E foi ele quem provou a identidade que abriu todo o campo:

> **Fórmula do produto de Euler.** Para $\operatorname{Re}(z)>1$,
> $$\sum_{n=1}^{\infty}\frac{1}{n^{z}}=\prod_{p\ \text{primo}}\frac{1}{1-p^{-z}}.$$

Uma consequência imediata é que $\zeta(z)\neq 0$ para $\operatorname{Re}(z)>1$. Outra, mais espetacular: como $\zeta(x)\to+\infty$ quando $x\to 1^{+}$, o produto do lado direito precisa ter infinitos fatores. **Existem infinitos primos** — e a demonstração é analítica, não combinatória. Nascia ali a teoria analítica dos números.

## A beleza da fórmula de Euler

Chegamos ao ponto alto. Euler demonstrou:

> **Teorema (Euler).**
> $$\zeta(2n)=\frac{(-1)^{n-1}\,2^{2n-1}\,B_{2n}\,\pi^{2n}}{(2n)!}.$$

Vale parar e olhar para isso com o cuidado que merece.

Do lado esquerdo, uma soma infinita de recíprocos de potências — um objeto puramente aritmético, definido por adições. Do lado direito, uma potência de $\pi$, o número da geometria do círculo, multiplicada por um racional explícito. A fórmula afirma que **toda soma dessas é um racional vezes uma potência de $\pi$**. Não aproximadamente: exatamente.

Os primeiros casos:

$$
\sum_{k=1}^{\infty}\frac{1}{k^{2}}=\frac{\pi^{2}}{6},
\qquad
\sum_{k=1}^{\infty}\frac{1}{k^{4}}=\frac{\pi^{4}}{90},
\qquad
\sum_{k=1}^{\infty}\frac{1}{k^{6}}=\frac{\pi^{6}}{945}.
$$

O primeiro é o famoso Problema da Basileia, que resistiu por décadas a Jacob Bernoulli e outros antes de Euler resolvê-lo em 1735, aos vinte e oito anos. Mas a fórmula geral não para nunca; ela produz, sem esforço adicional,

$$
\sum_{k=1}^{\infty}\frac{1}{k^{26}}=\frac{1315862}{11094481976030578125}\,\pi^{26},
$$

que é o tipo de identidade que ninguém adivinharia e que nenhuma manipulação isolada produziria.

**E aqui está o que realmente importa.** A beleza da fórmula não é apenas estética: ela é *informativa*. Como Lindemann provou em 1882 que $\pi$ é transcendente, e como um racional não nulo vezes uma potência de $\pi$ é transcendente, a fórmula de Euler entrega de graça:

$$
\zeta(2n) \ \text{é irracional — na verdade, transcendente — para todo } n\ge 1.
$$

Uma fórmula fechada não é um enfeite. É um instrumento de conhecimento aritmético. Sabemos tudo sobre a natureza dos zetas pares porque sabemos escrevê-los.

## O silêncio dos ímpares

E os ímpares?

Euler tentou. Não obteve nada parecido. Não é que ele tenha se distraído: o obstáculo é estrutural, e tem a ver justamente com a paridade dos números de Bernoulli que demonstramos lá atrás. A maquinaria que produz $\zeta(2n)$ simplesmente não produz $\zeta(2n+1)$.

Ainda assim, ele conjecturou uma forma. Euler propôs que

$$
\zeta(3)=\alpha\,(\ln 2)^{3}+\beta\,\pi^{2}\ln 2,
$$

com $\alpha$ e $\beta$ racionais. Uma aposta razoável — e, até onde se sabe, falsa, ou pelo menos jamais confirmada.

O que veio depois foi uma coleção de fórmulas belíssimas e aritmeticamente inúteis. Uma pequena galeria:

**Landen, 1780.** Com $\varphi=\frac{1+\sqrt5}{2}$ a razão áurea,

$$
\zeta(3)=-\frac{5}{6}(\ln\varphi)^{3}+\frac{\pi^{2}}{6}\ln\varphi+\frac{5}{4}\sum_{n=1}^{\infty}\frac{1}{n^{3}\varphi^{2n}}.
$$

**Lerch, 1901.**

$$
\zeta(3)=\frac{7\pi^{3}}{180}-2\sum_{n=1}^{\infty}\frac{1}{n^{3}\left(e^{2n\pi}-1\right)}.
$$

**Apéry, 1979.** A série que acelera a convergência e que está no coração de sua demonstração:

$$
\zeta(3)=\frac{5}{2}\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n^{3}\binom{2n}{n}}.
$$

**Janous, 2006.**

$$
\zeta(3)=\frac{8}{7}\left(\frac{(\ln 2)^{3}}{3}+\sum_{n=1}^{\infty}\frac{1}{2^{n}}\left(\frac{\ln 2}{n^{2}}+\frac{1}{n^{3}}\right)\right).
$$

Esta última merece atenção, porque é a que mais se aproxima da conjectura de Euler. Usando a identidade conhecida $\sum_{n\ge1} 2^{-n}n^{-2}=\frac{\pi^{2}}{12}-\frac{(\ln 2)^{2}}{2}$, a fórmula de Janous se reorganiza em

$$
\zeta(3)=-\frac{4}{21}(\ln 2)^{3}+\frac{2}{21}\pi^{2}\ln 2+\frac{8}{7}\sum_{n=1}^{\infty}\frac{1}{2^{n}n^{3}}.
$$

Os dois primeiros termos são exatamente a forma que Euler conjecturou. O terceiro é o resíduo teimoso que não se deixa eliminar — e é ele que impede qualquer conclusão aritmética.

Por mais de trezentos anos, essa foi a situação: um acervo crescente de identidades para $\zeta(3)$, e nenhuma delas capaz de responder à pergunta mais elementar que se pode fazer sobre um número real.

## Apéry, 1979

Então veio a demonstração. Vou apresentá-la na forma que Frits Beukers publicou em 1979, muito mais transparente que a original — e é essa transparência que torna o título de van der Poorten irresistível.

A estratégia é o critério de irracionalidade mais antigo que existe. Se conseguirmos, para cada $n$, inteiros $A_n$ e $B_n$ tais que a quantidade $A_n+B_n\zeta(3)$ seja **não nula** mas **muito pequena**, ganhamos. Porque se $\zeta(3)=p/q$ fosse racional, então $A_n+B_n\,p/q$ seria um racional não nulo com denominador $q$, logo em valor absoluto pelo menos $1/q$ — uma barreira fixa. Basta então fazer a quantidade decair abaixo dela.

**Passo um: uma representação integral.** O objeto central é

$$
I_{r,s}=\int_{0}^{1}\!\!\int_{0}^{1}\frac{\log xy}{1-xy}\,x^{r}y^{s}\,dx\,dy .
$$

Para calculá-la, usa-se um truque que Euler amava: derivar sob o sinal de integral. Considere

$$
\int_{0}^{1}\!\!\int_{0}^{1}\frac{x^{r+\sigma}y^{s+\sigma}}{1-xy}\,dx\,dy ,
$$

expanda $\frac{1}{1-xy}$ em série geométrica e integre termo a termo. Sai

$$
\sum_{k=0}^{\infty}\frac{1}{(k+r+\sigma+1)(k+s+\sigma+1)} .
$$

Quando $r>s$, essa soma **telescopa**, e derivando em $\sigma$ e fazendo $\sigma=0$ obtém-se um número racional explícito. Quando $r=s$, ela não telescopa, e o mesmo procedimento produz

$$
I_{r,r}=-2\left(\zeta(3)-\sum_{k=1}^{r}\frac{1}{k^{3}}\right).
$$

É por essa porta que $\zeta(3)$ entra na demonstração. Em particular, com $r=s=0$,

$$
-2\zeta(3)=\int_{0}^{1}\!\!\int_{0}^{1}\frac{\log xy}{1-xy}\,dx\,dy,
$$

que é o análogo perfeito da representação clássica $\zeta(2)=\int_0^1\int_0^1\frac{dx\,dy}{1-xy}$.

O lema de Beukers organiza isso: com $d_r=\operatorname{mmc}(1,\ldots,r)$, as integrais com $r>s$ são racionais com denominador dividindo $d_r^{3}$, e as com $r=s$ envolvem $\zeta(3)$ da forma acima. Ou seja, combinações lineares inteiras dessas integrais têm exatamente a forma $(A+B\zeta(3))/d_r^{3}$.

**Passo dois: os polinômios de Legendre.** Falta escolher a combinação certa — aquela que faz a integral ficar minúscula. Beukers considera

$$
J_{n}=-\int_{0}^{1}\!\!\int_{0}^{1}\frac{\log xy}{1-xy}\,P_{n}(x)P_{n}(y)\,dx\,dy ,
$$

onde $P_n$ é o $n$-ésimo polinômio de Legendre deslocado, dado pela fórmula de Rodrigues $n!\,P_n(x)=\frac{d^n}{dx^n}\bigl[x^n(1-x)^n\bigr]$ — e o fator $1/n!$ é precisamente o que garante coeficientes inteiros.

Usando $\frac{\log xy}{1-xy}=-\int_0^1\frac{dz}{1-(1-xy)z}$, a integral dupla vira tripla; e depois de $n$ integrações por partes em $x$ e outras $n$ em $y$, todo o aparato se condensa em

$$
J_{n}=\int_{0}^{1}\!\!\int_{0}^{1}\!\!\int_{0}^{1}\frac{\bigl[x(1-x)y(1-y)z(1-z)\bigr]^{n}}{\bigl[1-(1-xy)z\bigr]^{n+1}}\,dx\,dy\,dz .
$$

**Passo três: um problema de cálculo.** Agora só falta estimar

$$
g(x,y,z)=\frac{x(1-x)\,y(1-y)\,z(1-z)}{1-(1-xy)z}
$$

no cubo unitário. É otimização de cálculo, nada mais. Substituindo $w=1-(1-xy)z$, derivando em $w$ (o máximo ocorre em $w=x$) e depois em $x$ (o máximo ocorre em $x=\sqrt2-1$), chega-se ao valor ótimo

$$
g(x,y,z)\;\le\;(\sqrt2-1)^{4}\;<\;2^{-5}.
$$

Portanto $J_n \ll 2^{-5n}$.

**O fecho.** A integral $J_n$ é estritamente positiva — o integrando é não negativo e claramente positivo perto de $(1/2,1/2,1/2)$ — e tem a forma $(A_n+B_n\zeta(3))\,d_n^{-3}$. Usando a estimativa $d_n<3^{n}$ para $n$ grande,

$$
0<\lvert A_{n}+B_{n}\zeta(3)\rvert \;\ll\; 3^{3n}\,2^{-5n}=\left(\frac{27}{32}\right)^{n}.
$$

E aqui está o milagre aritmético, escondido numa desigualdade entre dois números pequenos:

$$
3^{3}=27\;<\;32=2^{5}.
$$

O lado direito decai exponencialmente. Se $\zeta(3)=p/q$, o lado esquerdo seria $\ge 1/q$, uma constante. Contradição para $n$ suficientemente grande. $\blacksquare$

## Por que "a prova que Euler perdeu"

Agora podemos avaliar o título de van der Poorten com honestidade. Faça o inventário das ferramentas:

- integrais duplas e triplas sobre o cubo unitário — Euler;
- expansão de $\frac{1}{1-xy}$ em série geométrica e integração termo a termo — Euler, à vontade;
- derivação sob o sinal de integral — técnica que ele usou à exaustão;
- integração por partes iterada — elementar já no século XVIII;
- polinômios de Legendre — Legendre (1752–1833) é **contemporâneo** de Euler, e as manipulações necessárias não excedem o que Euler fazia rotineiramente;
- otimização de uma função de três variáveis no cubo — cálculo padrão;
- o critério de irracionalidade via denominadores — conhecido desde a Antiguidade em espírito.

Não há uma única ideia estruturalmente moderna nessa lista. Nenhuma teoria de Galois, nenhuma geometria algébrica, nenhuma análise complexa avançada.

**Com uma exceção**, e é justo apontá-la: a estimativa $d_n<3^{n}$ para o mínimo múltiplo comum de $1,\ldots,n$. Ela decorre do comportamento assintótico da função de Chebyshev, e portanto do Teorema dos Números Primos, demonstrado apenas em 1896 por Hadamard e de la Vallée Poussin. Esse ingrediente Euler não tinha.

Só que — e a ironia é deliciosa — o Teorema dos Números Primos é o desenvolvimento maduro do programa que **Euler inaugurou** com a fórmula do produto. Foi ele quem primeiro ligou a função zeta à distribuição dos primos. A peça que faltava para a demonstração era a continuação natural da sua própria descoberta.

Se ele tivesse vivido mais um século, ou se alguém tivesse feito a pergunta certa na ordem certa, esta prova pertenceria a 1750.

## A fórmula mística de Ramanujan

Há um epílogo que eu não resisto a contar.

Se a fórmula de Euler para $\zeta(2n)$ é a fonte de todo o nosso conhecimento sobre os pares, a pergunta óbvia é: existe algum análogo para os ímpares?

A resposta é **sim** — e vem de Srinivasa Ramanujan (1887–1920).

> **Teorema (Fórmula de Ramanujan para $\zeta(2n+1)$).** Sejam $\alpha,\beta>0$ com $\alpha\beta=\pi^{2}$, e $n$ inteiro positivo. Então
>
> $$
> \begin{aligned}
> \alpha^{-n}&\left(\tfrac{1}{2}\zeta(2n+1)+\sum_{m=1}^{\infty}\frac{1}{m^{2n+1}\left(e^{2m\alpha}-1\right)}\right)\\
> -\,(-\beta)^{-n}&\left(\tfrac{1}{2}\zeta(2n+1)+\sum_{m=1}^{\infty}\frac{1}{m^{2n+1}\left(e^{2m\beta}-1\right)}\right)\\
> &=2^{2n}\sum_{k=0}^{n+1}(-1)^{k-1}\frac{B_{2k}}{(2k)!}\,\frac{B_{2n+2-2k}}{(2n+2-2k)!}\,\alpha^{n+1-k}\beta^{k}.
> \end{aligned}
> $$

Olhe para o lado direito: **os números de Bernoulli estão lá**, exatamente como na fórmula de Euler. A estrutura sobreviveu. O que não sobreviveu foi a limpeza: $\zeta(2n+1)$ não aparece isolado, mas contaminado por séries envolvendo $e^{2m\alpha}-1$ que se recusam a desaparecer. A fórmula é uma identidade, não uma avaliação.

Ela não tem a elegância da de Euler, e não fornece **nenhuma** informação aritmética sobre a zeta dos ímpares. Mas é, no seu misticismo, de uma beleza estranha e inegável.

Quanto à demonstração, os slides da minha palestra registram a versão canônica: *Ramanujan a recebeu em sonho, diretamente das mãos da deusa Mahalakshmi.* Ele creditava a ela as cerca de 3900 fórmulas que deixou. Hardy, que o descobriu, dizia que sua maior contribuição à matemática foi ter encontrado Ramanujan.

## O que ainda não sabemos

Encerro com o estado da arte, que é ao mesmo tempo humilhante e estimulante.

> **Conjectura.** $\zeta(2n+1)$ é irracional para todo $n\ge 1$.

Aberta. Quase cinquenta anos depois de Apéry, o que se sabe é:

- $\zeta(3)$ é irracional (Apéry, 1979). É o **único** valor ímpar sobre o qual temos certeza.
- Infinitos valores $\zeta(2n+1)$ são irracionais (Rivoal, 2000; Ball–Rivoal, 2001) — mas a demonstração não identifica **quais**.
- Pelo menos um dentre $\zeta(5),\zeta(7),\zeta(9),\zeta(11)$ é irracional (Zudilin, 2001). Novamente: não sabemos qual.

Ou seja: não sabemos se $\zeta(5)$ é irracional. Não sabemos se $\zeta(3)/\pi^{3}$ é irracional. Não sabemos se $\zeta(3)$ é transcendente — apenas que é irracional. Toda a informação que temos de graça para os pares, via fórmula de Euler, permanece indisponível para os ímpares.

A moral, para mim, é sobre o valor das formas fechadas. Sabemos tudo sobre $\zeta(2n)$ porque Euler soube **escrevê-lo**. A ignorância sobre $\zeta(2n+1)$ é, no fundo, a ignorância de uma expressão. E a prova de Apéry mostra que, às vezes, o obstáculo não é a falta de ferramentas — é a falta da pergunta.

Euler tinha o martelo. Faltou saber onde bater.

## Referências

1. R. Apéry, *Irrationalité de $\zeta(2)$ et $\zeta(3)$*, Journées Arithmétiques de Luminy, Astérisque n. 61 (1979), 11–13.
2. F. Beukers, *A note on the irrationality of $\zeta(2)$ and $\zeta(3)$*, Bulletin of the London Mathematical Society 11 (1979), 268–272.
3. A. van der Poorten, *A proof that Euler missed… Apéry's proof of the irrationality of $\zeta(3)$*, The Mathematical Intelligencer 1 (1978/79), 195–203.
4. B. C. Berndt e A. Straub, *Ramanujan's formula for $\zeta(2n+1)$*, in: Exploring the Riemann Zeta Function — 190 Years from Riemann's Birth, Springer, 2017, pp. 13–34.
5. T. Rivoal, *La fonction zêta de Riemann prend une infinité de valeurs irrationnelles aux entiers impairs*, Comptes Rendus de l'Académie des Sciences 331 (2000), 267–270.
6. W. Zudilin, *One of the numbers $\zeta(5),\zeta(7),\zeta(9),\zeta(11)$ is irrational*, Russian Mathematical Surveys 56 (2001), 774–776.
