<h1 align="center">⭐Recursividade⭐</h1>

## Conceito

<p align="justify">Recursividade, Recursão ou Recorrência são sinônimos e se referem à capacidade que uma função ou subrotina tem de invocar a si mesma. Ou seja, na prática é uma função que chama a si própria no código.<br>
<br>
O exemplo mais comum é o cálculo de fatorial. Esse cálculo parte da seguinte regra geral: <b>0! ou 1! = 1</b>.<br>
<br>
Pensando logicamente é possível encontrar a seguinte expressão:<br></p>
<p>fat(0) ou fat(1) = 1<br>
n! = n*(n-1)!<br>
4! = 4x3! = 4x3x2! = 4x3x2x1! = 4x3x2x1 = 24<br>
</p>
<p align="justify">Assim, esse cálculo em uma função de fatorial escrita em Python ficaria da seguinte forma:<br></p>

```
def fat(n):
    if n == 0 or n==1: return 1
    else:
        return n*fat(n-1)

print(fat(4))
```

<p align="justify">A maior parte das funções recursivas tem a seguinte estrutura:<br>

```
def f(argumentos):
	se caso simples:
		devolve valor que sei
	senão:
		faz alguma conta que diminui os argumentos
		devolve valor composto que monta o resultado que quero
```

Repare que no fatorial recursivo <b>não tem while</b> e <b>não tem for</b>. Então como ele faz a repetição? Ele faz a repetição no *return*.<br>

```
fat(4):
	if 4 == 0 or 4 == 1:
	else:
		return 4 * fat(3)
fat(3):
	if 3 == 0 or 3 == 1:
	else:
		return 3 * fat(2)
fat(2):
	if 2 == 0 or 2 == 1:
	else:
		return 2 * fat(1)
fat(1):
	if 1 == 0 or 1 == 1: return 1
```

</p>

## Exemplos

<p>1) Cálculo de potência:</p>

```
def pot(x,n):
    if n == 0: return 1
    return x * pot(x, n-1)

print(pot(2,3))
```

<p>2) Fatiamento de strings:</p>

```
def inv(s):
    if len(s) == 0: return ""
    return inv(s[1:]) + s[0]
print(inv("abacate"))
```

<p>3) Cálculo de MDC:</p>

```
def mdc(a,b):
    if a % b == 0: return b
    return mdc(b, a%b)
print(mdc(21,15))
print(mdc(15,21))
```

<p>4) Soma dos dígitos de um inteiro (n):</p>

```
def sd(n):
    #sd(123) = 6 = 1 + 2 + 3
    if n <= 9: return n
    return sd(123 // 10) + n % 10
print(sd(123))
```

<p>5) Sequência de Fibonacci:</p>

```
def fib(n):
    if n <= 2: return 1
    return fib(n-1) + fib(n-2)
print(fib(10))
```

