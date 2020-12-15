# CSS GRID

## GRID
- Bidimesional.
- Contém linhas e colunas.
- Consigo organizar os elementos dentro dessas linhas e colunas.

## GRID ou FLEXBOX

- GRID: Duas dimensões(colunas e linhas).
- FLEXBOX: Apenas uma dimensão(ou coluna ou linha).
- Um complementa o trabalho do outro.
- Verificar quais navegadores não estão utilizando GRID.

## Propriedades

Vamos separar em 2 grupos: `container` e `item(s)`.

### CONTAINER
- `display: grid`(define que é o template é grid)
- `grid-template-columns`(define a quantidade de colunas)
- `grid-template-rows`(define a quantidade de linhas)
- `grid-gap`(espaçamento)
- - `grid-column-gap`(entre coluna)
- - `grid-row-gap`(entre linha)
- `grid-template-area`(delimita áreas)
- ... e mais 4 propriedades de alinhamento.

### ITEM(S)
- `grid-column`(informa onde o item ficará na coluna)
- - `grid-column-start`(onde é a linha inicial do item no grid)
- - `grid-column-end`(onde é a linha final do item no grid)

- `grid-row`(informa onde o item ficará na linha)
- - `grid-row-start`(se é no inicio)
- - `grid-row-end`(se é no fim)

- `grid-area`(onde ficará na área, caso eu utilize o `grid-template-area`)

- ... e mais 2 propriedades de alinhamento

<p align="center">
  <img src="https://ik.imagekit.io/xfddek6eqk/grid-template_NMHuiFKqm.png"/>
</p>

Na imagem acima é possível observar as linhas imaginárias(virtuais) que definem uma grid. As propriedades `grid-column-start` e `grid-row-start` fazem referência ao inicio do item no respectivo eixo. Enquanto a `grid-column-end` e `grid-row-end` faz referência ao fim do item no respectivo eixo.

Posso alterar a ordem que os items são mostrados na grid as propriedades acima, como mostrado no exemplo a seguir:

<p align="center">
  <img src="https://ik.imagekit.io/xfddek6eqk/grid-template-example_Qqfu8gksa.png"/>
</p>

```css
.container {
  display: grid;
  grid-template-columns: 3fr 1fr;
  grid-template-rows: 20vh 70vh 10vh;
  grid-template-areas: 
    "h h"
    "m a"
    "f f"
}

header {
  background: #fc5c9c;

  /*sem shorthand*/
  grid-column-start: 1;
  grid-column-end: 3;
  grid-row-start: 1;
  grid-row-end: 2;

  /*ou posso utilizar shorthand dessa forma*/
  grid-column: 1/3;
  grid-row: 1/2;

  /*ou posso utilizar o area o item, caso esteja sendo usando no container*/
  grid-area: h;
}

main {
  background: #fccde2;

  grid-area: m;
}

aside {
  background: #fcefee;

  grid-area: a;
}

footer {
  background:#c5e3f6;

  grid-area: f;
}
```

Com o `grid-template-areas` eu dou nomes as linhas e colunas, ao invés de me preocupar com as linhas imaginárias(virtuais) da grid.

## GRID Alinhamentos

Existem 6 propriedades de alinhamentos:
1. `justify-content`
2. `align-content`
3. `justify-items`
4. `align-items`
5. `justify-self`
6. `align-self`

Vamos separá-los em 2 grupos:
1. `justify` e `align`
2. `content`, `items` e `self`

### justify e align

Sabendo que o grid é bidimensional, ou seja, linhas e colunas, temos:
- **eixo x** é horizontal.
- **eixo y** é vertical.

### content, items e self

Ao utilizar `justify` ou `align` temos acesso as propriedades: `content`, `items` e `self`.

#### content
`justify-content` e `align-content` permite alinhar o próprio grid, relativo ao espaço fora do grid.

**Ou seja, me permite alinhar o grid de acordo com o espaço em volta dele, o espaço em que ele está inserido**

O uso dessas propriedades são raras, pois só é aplicado caso o grid seja menor que a área definida.(Por exemplo, quando usamos em px o tamanho do grid, poderemoes terminar com o grid pequeno para o tamanho da área do grid)

7 valores disponiveis para os alinhamentos:
1. start
2. end
3. center
4. stretch
5. space-around
6. space-between
7. space-evenly

#### items
`justify-items` e `align-items` permite alinhas os itens do nosso grid em qualquer espaço disponível na célula que ele habitar.

**Se o item for menor que a area da célula da grid, então eu posso utilizar `justify/align-items` no próprio grid para alinhar cada item.**

```css
html, body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  width: 100vw;
  height:100vh;
}


.container {
  height: 100vh;
  width: 100vw;
  background: black;

  display: grid;

  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-gap: 5px;

  justify-items: center;
  align-items: center;

}

.container > div {
  background: #ccc;

  height: 50%;
  width: 50%;
}
```
Nessa imagem, a grid ocupa toda o espaço disponível da tela(height e width), porém o contéudo da célula é menor do que o espaço disponível da célula. Logo, posso alinhar o contéudo de cada célula utilizando o `item`.
<p align="center">
  <img src="https://ik.imagekit.io/xfddek6eqk/grid-items_fubqPg7gy.png"/>
</p>

4 valores disponiveis para os alinhamentos:
1. start
2. end
3. center
4. stretch

#### self

`justify-self` e `align-self` permite alinhar o item em si.

Faz a mesma coisa do `justify-items` e `align-items`, porém, aplicado diretamente no elemento de um grid ao invés do container da grid.

```css
html, body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  width: 100vw;
  height:100vh;
}


.container {
  height: 100vh;
  width: 100vw;
  background: black;

  display: grid;

  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-gap: 5px;

}

.container > div {
  background: #ccc;

  height: 50%;
  width: 50%;

  justify-self: center;
  align-self: center;
}

```
