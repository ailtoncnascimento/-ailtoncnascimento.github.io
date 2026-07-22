---
title: "Uma inteligência artificial encontrou um contraexemplo para uma conjectura de 87 anos?"
date: 2026-07-22 10:00:00 -0300
categories: [Matemática, Curiosidades]
tags: [inteligência artificial, álgebra, geometria algébrica, conjectura jacobiana]
math: true
description: Um exemplo polinomial explícito em dimensão três parece encerrar a Conjectura Jacobiana — mas deixa intacto o misterioso caso bidimensional.
---

> *Um exemplo polinomial explícito, anunciado com o auxílio de inteligência artificial, parece encerrar a Conjectura Jacobiana em dimensão três — mas deixa intacto o misterioso caso bidimensional.*

Uma das conjecturas mais conhecidas da álgebra e da geometria algébrica pode ter recebido, de maneira bastante inesperada, uma resposta negativa.

Em julho de 2026, enquanto assistia a final da Copa do Mundo de 2026 entre Argentina e Espanha, o matemático **Levent Alpöge** divulgou uma aplicação polinomial

$$
F\colon \mathbb{C}^{3}\longrightarrow \mathbb{C}^{3}
$$

que possui determinante jacobiano constante e diferente de zero, mas não é injetiva. Segundo o anúncio, o exemplo foi encontrado com o auxílio do modelo experimental de inteligência artificial **Claude Fable 5**.

O resultado atraiu imediatamente a atenção da comunidade matemática porque contradiz, em dimensão três, a famosa **Conjectura Jacobiana**, problema que remonta a 1939.

O aspecto mais surpreendente é que o contraexemplo pode ser escrito em poucas linhas e suas duas propriedades fundamentais podem ser verificadas por cálculos algébricos exatos.

## O que é a Conjectura Jacobiana?

Considere uma aplicação polinomial

$$
F=(F_{1},\ldots,F_{n})\colon \mathbb{C}^{n}\longrightarrow\mathbb{C}^{n},
$$

em que cada componente $F_{j}\in \mathbb{C}[x_{1},\ldots,x_{n}]$ é um polinômio.

A matriz jacobiana de $F$ é definida por

$$
JF(x)=
\begin{pmatrix}
\dfrac{\partial F_{1}}{\partial x_{1}} & \cdots & \dfrac{\partial F_{1}}{\partial x_{n}}\\[6pt]
\vdots & \ddots & \vdots\\[6pt]
\dfrac{\partial F_{n}}{\partial x_{1}} & \cdots & \dfrac{\partial F_{n}}{\partial x_{n}}
\end{pmatrix}.
$$

Seu determinante, $\det JF(x)$, mede localmente como a transformação distorce volumes e indica se ela é localmente invertível.

A Conjectura Jacobiana afirmava que, sobre um corpo de característica zero, como $\mathbb{C}$, a condição

$$
\det JF(x)\equiv c, \qquad c\neq 0,
$$

deveria implicar que $F$ possui uma inversa polinomial. Em outras palavras, deveria existir uma aplicação $G=(G_{1},\ldots,G_{n})\colon\mathbb{C}^{n}\to\mathbb{C}^{n}$, cujas componentes também fossem polinômios, tal que

$$
G\circ F=F\circ G=\operatorname{Id}_{\mathbb{C}^{n}}.
$$

Esquematicamente, a conjectura dizia:

$$
\boxed{\ \det JF\equiv c\neq 0 \quad\Longrightarrow\quad F\text{ é um automorfismo polinomial}.\ }
$$

A hipótese garante, pelo Teorema da Função Inversa, que $F$ é localmente invertível em todos os pontos. O salto conceitual da conjectura consistia em afirmar que essa inversibilidade local deveria produzir uma inversibilidade *global*, com inversa ainda pertencente à categoria polinomial.

## Um exemplo simples de aplicação invertível

Considere $F(x,y)=\bigl(x+y^{2},y\bigr)$. Sua matriz jacobiana é

$$
JF(x,y)=
\begin{pmatrix}
1 & 2y\\
0 & 1
\end{pmatrix},
\qquad
\det JF(x,y)=1.
$$

Nesse caso, a inversa pode ser encontrada explicitamente:

$$
F^{-1}(u,v)=\bigl(u-v^{2},v\bigr).
$$

Portanto, esse exemplo possui exatamente o comportamento previsto pela Conjectura Jacobiana: jacobiano constante não nulo e inversa polinomial. O problema era saber se isso sempre aconteceria.

## O contraexemplo anunciado

Defina $F(x,y,z)=\bigl(F_{1},F_{2},F_{3}\bigr)$, onde

$$
\begin{aligned}
F_{1}(x,y,z) &= (1+xy)^{3}z + y^{2}(1+xy)(4+3xy),\\
F_{2}(x,y,z) &= y+3x(1+xy)^{2}z + 3xy^{2}(4+3xy),\\
F_{3}(x,y,z) &= 2x-3x^{2}y-x^{3}z.
\end{aligned}
$$

Essa é uma aplicação polinomial de $\mathbb{C}^{3}$ em $\mathbb{C}^{3}$. Um cálculo direto fornece

$$
\boxed{\det JF(x,y,z)=-2}
$$

para todo $(x,y,z)\in\mathbb{C}^{3}$. Assim, a aplicação satisfaz perfeitamente a hipótese da Conjectura Jacobiana: seu determinante jacobiano é uma constante diferente de zero.

Entretanto, considere os três pontos

$$
P_{0}=\left(0,0,-\tfrac14\right), \qquad
P_{+}=\left(1,-\tfrac32,\tfrac{13}{2}\right), \qquad
P_{-}=\left(-1,\tfrac32,\tfrac{13}{2}\right).
$$

Eles são claramente distintos. Apesar disso, verifica-se que

$$
F(P_{0})=F(P_{+})=F(P_{-})=\left(-\tfrac14,0,0\right).
$$

Portanto, $F$ não é injetiva. Como toda aplicação que possui inversa deve necessariamente ser injetiva, segue que $F$ não possui inversa polinomial — na verdade, não possui sequer uma inversa global como função. Temos, assim, $\det JF\equiv -2\neq 0$, mas $F$ envia três pontos distintos ao mesmo valor. Logo,

$$
\boxed{\ \det JF\equiv -2 \quad\text{não implica que}\quad F\text{ seja globalmente invertível}.\ }
$$

Esse é precisamente o tipo de exemplo capaz de refutar a Conjectura Jacobiana em dimensão três.

## Verificação direta das imagens

Vejamos o ponto $P_{0}=\left(0,0,-\tfrac14\right)$. Como $xy=0$, temos

$$
F_{1}(P_{0})=(1+0)^{3}\left(-\tfrac14\right)+0=-\tfrac14, \qquad F_{2}(P_{0})=0, \qquad F_{3}(P_{0})=0.
$$

Portanto, $F(P_{0})=\left(-\tfrac14,0,0\right)$.

Para $P_{+}=\left(1,-\tfrac32,\tfrac{13}{2}\right)$, temos

$$
xy=-\tfrac32, \qquad 1+xy=-\tfrac12, \qquad 4+3xy=-\tfrac12.
$$

Consequentemente,

$$
\begin{aligned}
F_{1}(P_{+}) &= \left(-\tfrac12\right)^{3}\tfrac{13}{2} + \left(\tfrac94\right)\left(-\tfrac12\right)\left(-\tfrac12\right)\\
&= -\tfrac{13}{16}+\tfrac{9}{16} = -\tfrac14.
\end{aligned}
$$

Além disso,

$$
\begin{aligned}
F_{2}(P_{+}) &= -\tfrac32 + 3\left(\tfrac14\right)\tfrac{13}{2} + 3\left(\tfrac94\right)\left(-\tfrac12\right)\\
&= -\tfrac{24}{16}+\tfrac{78}{16}-\tfrac{54}{16} = 0,
\end{aligned}
$$

enquanto

$$
\begin{aligned}
F_{3}(P_{+}) &= 2 -3\left(-\tfrac32\right) -\tfrac{13}{2}\\
&= 2+\tfrac92-\tfrac{13}{2} = 0.
\end{aligned}
$$

Logo, $F(P_{+})=\left(-\tfrac14,0,0\right)$. O cálculo para $P_{-}$ é análogo e fornece o mesmo resultado.

## Por que o determinante não nulo não foi suficiente?

À primeira vista, pode parecer contraditório que uma aplicação com $\det JF(x)\neq 0$ em todos os pontos envie pontos distintos para o mesmo lugar. Não há, entretanto, contradição com o Teorema da Função Inversa.

Esse teorema garante apenas que, para cada ponto $p$, existem vizinhanças $U$ de $p$ e $V$ de $F(p)$ tais que $\left.F\right|_{U}\colon U\to V$ é invertível. Isso é uma propriedade *local*. Ela não exclui a possibilidade de que regiões distantes do domínio sejam enviadas para a mesma região da imagem.

O novo exemplo evidencia exatamente essa diferença: invertibilidade local $\not\Longrightarrow$ invertibilidade global. A Conjectura Jacobiana afirmava que a estrutura polinomial seria rígida o suficiente para eliminar esse fenômeno. O exemplo mostra que, ao menos em três variáveis, essa expectativa não se confirma.

## Uma história que pode ter começado antes de 1939

O problema é tradicionalmente atribuído ao matemático alemão **Ott-Heinrich Keller**, que o formulou em 1939 no contexto das transformações polinomiais. Por essa razão, ele também ficou conhecido como *Problema de Keller* ou *Conjectura Jacobiana de Keller*.

Uma pesquisa histórica recente, contudo, identificou uma formulação essencialmente equivalente em um artigo de **L. Kraus**, publicado em 1884. Kraus acreditava ter demonstrado o resultado, mas o argumento continha uma falha em sua etapa final, relacionada ao comportamento da aplicação no infinito. Essa descoberta histórica torna a trajetória do problema ainda mais interessante: embora o enigma seja usualmente chamado de uma conjectura de 87 anos, suas raízes podem remontar a mais de 140 anos.

## O problema é fácil em uma variável

Em dimensão um, a afirmação é elementar. Se $F\colon\mathbb{C}\to\mathbb{C}$ é um polinômio e $F'(x)\equiv c\neq 0$, então necessariamente $F(x)=cx+d$ para alguma constante $d\in\mathbb{C}$. Sua inversa é

$$
F^{-1}(y)=\frac{y-d}{c},
$$

que também é polinomial. Portanto, a Conjectura Jacobiana é verdadeira para $n=1$. O novo contraexemplo mostra que ela é falsa para $n=3$.

## E o caso de duas variáveis?

O ponto mais intrigante é que o exemplo tridimensional não resolve automaticamente o caso $F\colon\mathbb{C}^{2}\to\mathbb{C}^{2}$. Assim, permanece aberta a seguinte pergunta:

> **Em aberto.** Se $F\colon\mathbb{C}^{2}\to\mathbb{C}^{2}$ é polinomial e $\det JF$ é uma constante não nula, então $F$ é um automorfismo polinomial?

Em outras palavras, a Conjectura Jacobiana pode ser falsa no cenário geral, mas continuar verdadeira em dimensão dois. O caso bidimensional, portanto, torna-se agora ainda mais singular.

## Por que o exemplo também afeta dimensões superiores?

Uma vez obtido um contraexemplo em dimensão três, podemos construir contraexemplos em qualquer dimensão $n\geq 3$. Basta definir $\widetilde{F}\colon\mathbb{C}^{n}\to\mathbb{C}^{n}$ por

$$
\widetilde{F}(x,y,z,u_{4},\ldots,u_{n}) = \bigl(F(x,y,z),u_{4},\ldots,u_{n}\bigr).
$$

A matriz jacobiana de $\widetilde{F}$ possui a forma em blocos

$$
J\widetilde{F} =
\begin{pmatrix}
JF & 0\\
0 & I_{n-3}
\end{pmatrix},
\qquad
\det J\widetilde{F} = \det JF\cdot\det I_{n-3} = -2.
$$

Como a primeira parte da aplicação continua não sendo injetiva, $\widetilde{F}$ também não é injetiva. Portanto, o mesmo fenômeno ocorre em todas as dimensões $n\geq 3$.

## Por que esse resultado surpreendeu os matemáticos?

Durante décadas, grande parte dos esforços foi direcionada à tentativa de *demonstrar* a conjectura, e não à busca de um contraexemplo. Isso se explica, em parte, porque a afirmação parecia intuitivamente plausível: se uma transformação polinomial nunca degenera localmente, seria natural esperar que ela não dobrasse o espaço sobre si mesmo.

Além disso, vários casos particulares foram demonstrados, e importantes reduções teóricas reforçaram a ideia de que o problema possuía uma estrutura profunda e rígida. Em 1982, Hyman Bass, Edwin Connell e David Wright publicaram um trabalho fundamental mostrando que o estudo da conjectura geral podia ser reduzido a classes especiais de aplicações polinomiais, ao custo de aumentar a dimensão. Essas reduções, embora decisivas para o desenvolvimento da área, não forneceram uma solução completa. Por isso, o aparecimento de um exemplo explícito, relativamente curto e diretamente verificável causou tanta surpresa.

## O papel da inteligência artificial

Segundo os relatos iniciais, Levent Alpöge e Akhil Mathew utilizaram o modelo Claude Fable 5 durante a investigação que levou ao exemplo. Ainda não foi divulgada uma documentação acadêmica completa contendo:

- os comandos fornecidos ao modelo;
- as respostas intermediárias produzidas pela inteligência artificial;
- os critérios usados para orientar a busca;
- a divisão precisa entre as ideias humanas e as sugestões da máquina;
- o processo pelo qual o exemplo final foi simplificado e verificado.

Essa distinção é importante. Há pelo menos três tarefas diferentes envolvidas:

1. encontrar ou sugerir uma expressão candidata;
2. verificar simbolicamente que o determinante jacobiano é constante;
3. compreender conceitualmente por que a construção funciona.

Um sistema de álgebra computacional pode verificar mecanicamente a identidade $\det JF=-2$ e também confirmar que $F(P_{0})=F(P_{+})=F(P_{-})$. O verdadeiro desafio científico está em explicar como se chegou a uma expressão tão específica e se a inteligência artificial desempenhou apenas o papel de calculadora, de exploradora algébrica ou de colaboradora capaz de sugerir a ideia central da construção.

## Uma curiosidade: descobrir pode ser difícil, verificar pode ser fácil

Esse episódio ilustra uma característica frequente da matemática. A descoberta de um exemplo pode exigir uma busca extremamente sofisticada, mas, depois que o exemplo é apresentado, sua validade pode ser confirmada por cálculos relativamente curtos. No caso em questão, as duas verificações decisivas são $\det JF\equiv -2$ e $F(P_{0})=F(P_{+})=F(P_{-})$.

Essas identidades são objetivas e podem ser examinadas independentemente do método usado para encontrar $F$. Isso diferencia a situação de uma demonstração longa e conceitualmente complexa, na qual cada etapa do argumento precisa ser cuidadosamente auditada.

## Uma verificação por computador

O cálculo também pode ser realizado em um sistema de álgebra computacional. Em `SymPy`, por exemplo, pode-se usar:

```python
import sympy as sp

x, y, z = sp.symbols('x y z')

F1 = (1+x*y)**3*z + y**2*(1+x*y)*(4+3*x*y)
F2 = y + 3*x*(1+x*y)**2*z + 3*x*y**2*(4+3*x*y)
F3 = 2*x - 3*x**2*y - x**3*z

J = sp.Matrix([F1, F2, F3]).jacobian([x, y, z])

print(sp.factor(J.det()))
```

O resultado obtido é `-2`. Para conferir as imagens dos três pontos:

```python
points = [
    (0, 0, -sp.Rational(1,4)),
    (1, -sp.Rational(3,2), sp.Rational(13,2)),
    (-1, sp.Rational(3,2), sp.Rational(13,2))
]

for p in points:
    values = [
        sp.simplify(F.subs(dict(zip((x,y,z), p))))
        for F in (F1, F2, F3)
    ]
    print(values)
```

O programa retorna, nos três casos, `[-1/4, 0, 0]`.

## O que está estabelecido e o que ainda precisa ser esclarecido?

É importante separar duas afirmações.

**Primeira afirmação: o exemplo divulgado possui as propriedades anunciadas.** Essa parte pode ser verificada diretamente: $\det JF=-2$ e a aplicação não é injetiva. Salvo algum problema na formulação pública do problema, isso fornece de fato um contraexemplo à versão geral da Conjectura Jacobiana em dimensão três.

**Segunda afirmação: a inteligência artificial resolveu autonomamente o problema.** Essa conclusão exige mais cautela. Sem o registro completo da interação, não é possível determinar com precisão quanto da estratégia foi fornecido pelos matemáticos, quanto foi sugerido pelo modelo, se a IA encontrou o exemplo diretamente ou se apenas completou uma construção previamente orientada, e quais tentativas incorretas antecederam a resposta final.

A relevância do resultado matemático não depende dessa atribuição. Entretanto, a avaliação de seu significado para a história da inteligência artificial depende fortemente desses detalhes.

## Conclusão

Se o exemplo permanecer válido após sua apresentação formal e sua análise pela comunidade, a situação da Conjectura Jacobiana poderá ser resumida da seguinte maneira:

| Dimensão | Situação |
| :-: | :-: |
| $n=1$ | verdadeira |
| $n=2$ | ainda em aberto |
| $n\geq 3$ | falsa pelo contraexemplo divulgado |

Mais do que encerrar um problema clássico em sua forma geral, o episódio pode marcar uma nova etapa na relação entre matemáticos e sistemas de inteligência artificial. A máquina não substitui a necessidade de demonstração, verificação e compreensão. Contudo, ela pode tornar-se uma ferramenta poderosa para explorar espaços algébricos muito grandes, testar estruturas e sugerir objetos que dificilmente seriam encontrados por uma busca manual.

Neste caso, toda a surpresa cabe em duas identidades:

$$
\boxed{\det JF=-2}
$$

e

$$
\boxed{\ F\left(0,0,-\tfrac14\right) = F\left(1,-\tfrac32,\tfrac{13}{2}\right) = F\left(-1,\tfrac32,\tfrac{13}{2}\right) = \left(-\tfrac14,0,0\right).\ }
$$

Um problema com raízes no século XIX pode ter sido derrubado por um exemplo que cabe em uma única publicação nas redes sociais. A forma como fazemos Matemática passa por uma profunda transformação, e nós, matemáticos profissionais, precisamos nos adaptar a estes novos tempos. 

## Referências

1. O.-H. Keller, *Ganze Cremona-Transformationen*, Monatshefte für Mathematik und Physik, vol. 47, 1939, pp. 299–306.
2. H. Bass, E. H. Connell e D. Wright, *The Jacobian Conjecture: Reduction of Degree and Formal Expansion of the Inverse*, Bulletin of the American Mathematical Society, vol. 7, n. 2, 1982, pp. 287–330.
3. A. van den Essen, *To Believe or Not to Believe: The Jacobian Conjecture*, Rendiconti del Seminario Matematico, Università e Politecnico di Torino, vol. 55, n. 4, 1997.
4. L. O. Rodríguez Díaz, *On the Origin of the Jacobian Conjecture*, Comptes Rendus Mathématique, vol. 364, 2026, pp. 363–370.
5. L. Alpöge, comunicação pública contendo o exemplo polinomial em dimensão três, julho de 2026.
6. *AI's solution to 87-year-old riddle takes mathematicians by surprise*, New Scientist, julho de 2026.
