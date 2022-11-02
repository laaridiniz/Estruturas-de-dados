<h1 align="center"> ⭐Busca Binária⭐ </h1>

<p align="justify">Problema: preciso descobrir qual o número sorteado entre 1 e 100. Qual seria meu primeiro chute?<br>
<br>R: 50<br>
<br>
Se chutar sempre metade da metade, em quantos passos se acerta o número?<br>
<br>
Para resolver esse problema, podemos usar o seguinte algoritmo:<br></p>

```

from random import randint
sorteado = randint(1,1000)
while True:
    x = int(input('chute: '))
    if x == sorteado:
        print('Ganhou: ')
        break
    elif x > sorteado:
        print ('Alto')
    else:
        print('Baixo')
#acerte dez chutes
```

<p align="justify">Esse algoritmo é muito rápido, quanto maior, mais vale a pena usar. Para 1 milhão, gasta-se apenas 30 passos.<br></p>

## Algoritmo de busca binária

```
cont = 0
def busca_binaria(x, v):
  global cont
  e = -1
  d = len(v)
  while e < d-1: 
    m = (e + d) // 2
    cont = cont + 1
    if v[m] < x:
      e = m
    else:
      d = m
  return d

v = list(range(1000000))
from random import randint
print (busca_binaria(randint(1, 1000000), v))
print (cont)
```

<p align="justify">O "cont" é usado para contar a quantidade de tentativas. O x é o elemento que estou procurando no vetor v. O lado esquerdo começa com -1 (e = -1) e o lado direito com o tamanho do vetor (len(v)). Enquanto o lado esquerdo for menor que o lado direito -1 (enquanto não estiverem grudados um ao lado do outro), o vetor ( e + d) será dividido na metade e será verificado se o x é maior ou menor que o v[m] e faço o ajuste.<br> 
<br>
Obs.: e = d-1 significa que os elementos são contíguos.<br>
<br>
A busca binária é como a invenção da roda no mundo das Estruturas de Dados. Isto porque divide o mundo em dois, a cada passo tenho metade das buscas. Além disso, podemos reaproveitar a ideia de dividir o mundo em dois em vários outros contextos. O oposto também é rápido, dobra-se o número de resultados bons a cada passo.<br>
<br>
Usos:<br><br>
a) Procurar um nome na lista abrindo a lista no meio;<br><br>
b) Desenhar 128 retângulos em uma folha dobrando a folha sucessivamente ao meio; <br><br>
c) Fazer o índice de um banco de dados.<br>
<br>
Custa log (n, 2) passos para dividir, onde n é o tamanho do vetor. <br>
<br>
Suponha que precise desenhar 128 retângulos em numa folha de papel. Existem duas formas básicas:<br></p>

* Mede-se a largura e comprimento, divida a folha em 128 retângulos, desenhando-se um por um.
* Pode-se dobrar a folha no meio, e depois dobrar novamente no meio e assim pr diante em 7 passos tem-se 128 retângulos.

<p align="justify">Se você tem uma lista telefonica (páginas amarelas) e deseja descobrir um telefone, você pode abrí-la ao meio para ir mais rápido. Essa é a mesma ideia de busca binária.<br>
<br>
Viu-se busca binária num vetor ordenado, porém na vida real não encontra-se vetores ordenados, então é necessário ordenar o vetor antes de usar busca binária. Para ordenar existem vários algoritmos. Os que funcionam rápido usam IDEIA da busca binária, de dividir o mundo em dois.<br></p>

## Curiosidade

<p align="justify">Também é possível usar a busca binária para converter um número decimal para binário:<br></p>

```
def dec2bin(n):
    p = []
    while n != 0:
        p.append(n%2)
        n =n//2
    while len(p) > 0:
        print(p.pop(), end = '')

dec2bin(18)
```
