<h1 align="center">⭐Matrizes⭐</h1>

<p align="justify">Quando se fala em análise de vetores, deve-se ter em mente três operações fundamentais: busca, inserção e remoção.<br>
<br>
No caso da remoção, o pior caso seria precisar remover o primeiro elemento do vetor, uma vez que precisaria mover todos os outros para a esquerda.<br>
<br>
A mesma coisa acontece com a inserção, cujo pior caso também se resume à inserção de elemento no início do vetor, considerando que será necessário mover todos os demais para a direita para poder ter espaço para o novo elemento.<br>
</p>
<p align="justify"><b>Problema: quero saber o vetor de distâncias mínimas da cidade origem 3 até as outras cidades.</b><br>
<br>
Em primeiro lugar, preciso de uma estrutura de dados para representar o desenho.<br>
<br>
Existem duas possibilidades:<br>
<br>
a) Matriz de 0s e 1s, onde a linha representa a origem e a coluna o destino, e o valor 1 significa que tem caminho entre origem e destino (mais velocidade);<br>
<br>
b) Dicionário, onde a chave é origem e tenho uma lista de destinos (consome menos espaço).<br>
<br>
As duas possibilidades têm vantagens e desvantagens. Uma matriz ocupa muito espaço, além de ter muitas posições com zero (posições inúteis). Porém, é muito mais rápido perguntar se uma cidade é vizinha da outra.<br>
<br>
No dicionário, se uma cidade tiver muitos vizinhos, vou ter que andar até o final até descobrir se é vizinho ou não. Na matriz, a resposta é imediata.<br>
<br>
Vamos usar matriz, já que o número de cidades não é tão grande e posso até otimizar e guardar o conteúdo em um bit, já que é 0 ou 1.
Para andar pela cidade preciso guardar as seguintes, para a partir delas ir para frente. Para isso, vou usar uma estrutura chamada fila.<br>
<br></p>

## Fila

<p align="justify">FILA -> FIFO = first in, first out<br>
<br>
Qual é a estrutura lógica do programa?<br></p>

```
fila = origem
enquanto a fila não estiver vazia (último item)
	retira o primeiro
	verifica se o primeiro tem vizinho
	para cada vizinho calcula a distância e
coloca o vizinho na fila
```

Como vou garantir que a distância é mínima?<br>
<br>
Tenho que guardar as distâncias num local.<br>
<br>
Sugestão: a distância é sempre positiva. Vou começar com -1 para dizer que nunca passei por lá.<br>

```
A = [[0, 1, 0, 0, 0, 0], 
     [0, 0, 1, 0, 0, 0],
     [0, 0, 0, 0, 1, 0],
     [0, 0, 1, 0, 1, 0],
     [1, 0, 0, 0, 0, 0],
     [0, 1, 0, 0, 0, 0]]

def Distancias(n, origem):
  d = [-1] * n
  d[origem] = 0
  f = []
  f.append(origem)
  while len(f) > 0:
    x = f.pop(0)
    for y in range(n):
      if A[x][y] == 1 and d[y] == -1:
        d[y] = d[x] + 1
        f.append(y)
  return d

print (Distancias(len(A), 3))
```

## Pilha

<p align="justify">O último a ser colocado é o primeiro a ser tratado, como uma pilha de dados. {()} [()] A expressão é bem formada? Usa-se pilha para saber disso. ([{)]} náo é bem formado.<br>
<br>
Qual é a lógica? Tudo o que abre, significa menino, e coloca-se na pilha. Tudo o que fecha, é menina, e ela só pode ver o último que entrou, isto é, no topo da pilha. Se o topo for compatível, então deu match, porém, se for diferente, deu ruim. Por último, se sobrou menino sozinho na pilha também deu ruim.<br></p>

## Resumo

Existem problemas muito difíceis que conseguimos resolver utilizando estrutura de dados:
1) Definimos uma matriz para representar o desenho, vimos que apesar de gastar mais espaço, como temos poucas cidades, vale a pena porque é muito mais rápido consultar se é vizinho;
2) Definimos uma fila para guardar as cidades em que vamos chegando, assim podemos ir avançando até onde pudemos ir;
3) Com um vetor começando com -1 sinalizamos que nunca estivemos lá, assim garantimos que a distância é mínima.
