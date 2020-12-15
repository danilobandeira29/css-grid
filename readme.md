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
