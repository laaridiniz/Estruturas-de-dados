<h1 align="center">⭐Dicionários⭐</h1>

<p align="justify">Anteriormente foi usada a recursão para calcular a sequência de Fibonacci, como podemos ver a seguir:</p>

```
def fib(n):
    if n <= 2: return 1
    return fib(n-1) + fib(n-2)
print(fib(10))
```

<p align="justify">Também é possível fazer o mesmo cálculo usando dicionários para armazenar os valores:</p>

```
dic = {}
def fib(n):
    if n<=2: return 1
    if n not in dic: dic[n] = fib(n-1) + fib(n-2)
    return dic[n]
print(fib(100))
```

<p align="justify">Obs.: Embora armazenar dados exija mais espaço, evita repetição.<br>

Usando dicionário, é possível guardar as respostas já calculadas. Assim eu não repito mais e o programa fica muito mais rápido. Porém, usando o dicionário meu código fica mais feio.<br>
<br>
Dicionário, então, pode ser entendido como uma estrutura chave-valor pois, diferentemente de uma lista encadeada, que guarda apenas um valor por vez, os dicionários são coleções de itens e seus elementos são armazenados de forma não ordenada.<br>
<br>
Seus elementos contém uma chave e um valor, isto é:<br>
- Uma chave que vai servir para indexar (posicionar) determinado elemento no dicionário;<br>
- Um valor que aceita diversos tipos como listas, outros dicionários, inteiros, strings etc.
<br>
Sua sintaxe básica é: <b>{'chave':'valor'}</b>. Ou seja, utiliza-se <b>{}</b> (chaves) para delimitar o dicionário e a chave é separada do valor por <b>:</b> (dois pontos).<br>
<br>
Se ao utilizar <b>type()</b> a saída for <b>class 'dict'</b>, então estaremos diante de um dicionário.<br>
<br>
Por fim, o jeito de deixar de repetir sem mudar o código é usar bibliotecas. Com isso, posso usar a memória cache para guardar os retornos já calculados. Uso um decorador do Python, chamado lru_cache, lru = less results used. O decorador faz um envelope da função Fibonacci e dá super poderes sem mudar o código:<br>
<br>

```
from functools import lru_cache
@lru_cache(maxsize=None)
def fib(n):
    print(n)
    if n<=2: return 1
    return fib(n-1) + fib(n-2)
print(fib(100))
```

<p align="justify">Obs.: Para acessar itens ou acessar um valor de um dicionário, podemos usar sua chave, por exemplo:<br></p>

```
pessoa = {'nome':'Pythonico', 'altura':'1.65', 'idade': '20'}
print(pessoa['nome'])
```
    
