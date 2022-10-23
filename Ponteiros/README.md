<h1 align="center">⭐Ponteiros⭐</h1>

<br id="topo">

<p align="justify">Vetores em C são dados contíguos, isto é, um dado do ladinho do outro (!= Python em que os dados ficam na memória). Isto tem vantagens e desvantagens. Num vídeo-game, se eu quiser mudar uma área enorme, p. ex. sprite, é mais fácil com dados contíguos. Porém, no alto nível, se eu quiser inserir ou remover elementos, é muito ruim, porque preciso mover todos os elementos da direita do inserido ou removido.<br>
<br>
Nessa linha de raciocínio, podemos dizer que o pior caso seria ter que inserir ou remover no início. Como eu resolvo isso? Usando dados.<br>
<br>
Há uma estrutura de dados chamada <b>lista ligada</b> ou <b>lista encadeada</b>. Pensando em uma caça ao tesouro, inserir ou remover pista ficaria muito rápido porque não mudaria os dados de lugar, somente as pistas.<br>
<br>
Em C, há um tipo de dado chamado <b>ponteiro</b>, que serve apenas para apontar a região da memória onde está o dado. Ou seja, o ponteiro é uma variável que armazena endereços/índices da memória onde estão os dados. Em linhas de código, encontramos um ponteiro da seguinte forma:<br></p>

```
int k;
int *p;
p = &k; //p aponta para o endereço do inteiro k na memória
*p = 42; //posso colocar dados na variável k usando o ponteiro p</p>
```

<p align="justify">Em outras palavras é possível dizer que usando ponteiros consigo inserir ou remover dados que não são contíguos apenas mudando-os de posição.<br>
<br>
Implementação:
<br></p>

```
struct{
	int conteudo;
	struct cel * seg; //seguinte
}
type struct cel celula;
```

<p align="justify">Existem duas formas de você passar argumentos para uma função em C:<br>
<br>
a) Passagem por valor, comente uma cópia das variáveis;<br>
<br>
b) Passagem por referência, isto é, ponteiros para as variáveis de origem<br>
<br>
Python também faz tudo por referência, mas no alto nível. Já a linguagem C foi desenhada para construir um sistema operacional (Linux), por isso é tão baixo nível e por isso é mais difícil programar em C. Nessa linguagem, os perigos maiores se devem aos ponteiros.<br>
<br>
Regras:<br>
<br>
1) Ponteiro e coisa apontada são diferentes;<br>
<br>
2) Não tem sentido ponteiro que não aponta para nada.<br>
<br>
É melhor inserir elementos novos no final ou no começo da lista? No começo! Porque, se inserir no final, tenho que andar até o final e isso é ineficiente. Imagine 1 milhão de elementos, se eu tiver que andar até o final vou gastar muito tempo.<br>

_Programar em C = preocupação com eficiência do código_

O que significam as flechas? São o conteúdo de um ponteiro que é <b>struct</b>. P. ex.:<br>
</p>

```
struct cel {
	int conteudo;
	struct cel seg
}
typedef struct cel celula;
celula *nova;
nova = malloc(sizeof(celula));
nova->conteudo = y
(*nova).conteudo = y; // igual

nova->seg = p->seg;
(*nova).seg = (*p).seg; // igual
```

<p align="justify">Por que eu tenho um elemento sem nada no início?<br>
<br>
Eu chamei de <b>cabeça</b> esse elemento.<br>
<br>
Por dois motivos:<br>
<br>
1) Não preciso testar lista vazia toda hora no insere, porque sempre tenho a cabeça, nunca está vazio;<br>
<br>
2) Não preciso usar ponteiros para ponteiros. Se não tiver cabeça, preciso alterar lst, que aponta para o início. Só que lst é um ponteiro e se eu passar o endereço de um ponteiro, isso vira no insere, ponteiro para ponteiro.<br>
<br>
Assim, podemos dizer que os ponteiros agregam maior eficiência e clareza ao código.</p>

→ [Voltar ao topo](#topo)

## Resumo

<p align="justify">Os ponteiros são muito usados em C e podem ser utilizados de duas formas principalmente:<br>
<br>
1) Passagem de variável por referência;<br>
<br>
2) Vetor de alocação dinâmica.<br>
<br>
Regras para aplicação de ponteiros:<br>
<br>
1) Ponteiro e coisa apontada são diferentes;<br></p>

```
int *p; 
p = malloc(sizeuf(int));
//são coisas diferentes 
```

<p align="justify">
2) Não tem sentido ponteiro não inicializado (não aponta para nada);<br>
<br>
Com ponteiros implemento "caça ao tesouro", isto é, Listas Ligadas ou Listas Encadeadas.<br>
<br>
Ponteiros têm muitos detalhes de implementação:<br>
<br>
a) Insiro no começo, porque andar até o fim é ineficiente. Logo, se quero 1 2 3, preciso inserir ao contrário, 3 2 1;<br>
<br>
b) Uso cabeça de lista, porque assim tenho duas vantagens:<br></p>

* Não preciso testar lista vazia;
	
* Não uso ponteiros para ponteiros.

```
int * p;
int k;
p = & k;
*p = 42;
```

* & aponta para ponteiro que já é ponteiro
* int * p = é usado na declaração para dizer que é ponteiro e no acesso para indiretamente mudar o endereço
* & passa a posição na memória de uma variável (acessar de longe o k)
* (*p). conteudo = p -> conteudo (flechinha serve para trocar (*p))

<p align="justify"> Apesar de C conseguir otimizar códigos no baixo nível, hoje temos soluções boas no alto nível, por exemplo:<br>
<br>
1) Concorrência em Go e NodeJS;<br>
<br>
2) Iteradores com yield em Python;<br></p>

```
for k in range (10000000000000000000000000000):
	if k == 42:
		print('achei')
		break
		
```

<p align="justify">
3) Algoritmos probabilísticos.<br>
<br>
Vamos ver exemplos de resolução de exercícios onde esses detalhes todos em C são importantes:<br>
</p>

* 1) Lista Ligada Vetor para Lista.c

```
#include <stdio.h>
#include <stdlib.h>

struct cel {
       int conteudo;
       struct cel *seg; /* seguinte */
};

typedef struct cel celula;

void Imprima (celula *lst) {
     celula *p;
     for (p = lst->seg; p != NULL; p = p->seg)
         printf ("%d\n", p->conteudo);
}

void Insere(int y, celula *p){
    celula *nova;
    nova = malloc(sizeof(celula));
    nova->conteudo = y;
    nova->seg = p->seg;
    p->seg = nova;
}

int randint(int a, int b){
    double r, x, R = RAND_MAX;
    int i;
    r = rand();
    x = r / (R + 1);
    i = (int) (x * (b - a + 1));
    return a + i;
}

int main(void){
    int v[10]; 
    int k;
    
    for (k = 0; k < 10; k++) {
        v[k] = randint(10, 100);
        printf ("%d ", v[k]);
    }
    putchar('\n');
    celula *lst;
    lst = malloc(sizeof(celula));
    lst->seg = NULL;
    
    for (k = 9; k >= 0; k--) 
         Insere(v[k], lst);

    Imprima(lst);
    system("pause");
}
```

Neste caso, percorro o vetor ao contrário porque insiro no início da lista.

* 2) Lista Ligada Concatena.c (ex. 10):

```
#include <stdio.h>
#include <stdlib.h>
struct cel {
       int conteudo;
       struct cel *seg; /* seguinte */
};
typedef struct cel celula;
void Imprima (celula *lst) {
     celula *p;
     for (p = lst->seg; p != NULL; p = p->seg)
         printf ("%d", p->conteudo);
     putchar('\n');
}
void Insere(int y, celula *p){
    celula *nova;
    nova = malloc(sizeof(celula));
    nova->conteudo = y;
    nova->seg = p->seg;
    p->seg = nova;
}
int randint(int a, int b){
    double r, x, R = RAND_MAX;
    int i;
    r = rand();
    x = r / (R + 1);
    i = (int) (x * (b - a + 1));
    return a + i;
}

void concatena(celula *lst1, celula *lst2){
    celula *p;
    p = lst1->seg;
    while (p->seg != NULL)
        p = p->seg;
    
    p->seg = lst2->seg;
    free(lst2);
}

int main(void){
    int i;
    celula *lst1, *lst2;
    lst1 = malloc(sizeof(celula));
    lst1->seg = NULL;
    lst2 = malloc(sizeof(celula));
    lst2->seg = NULL;
    srand(time(NULL));
    for (i = 0; i < 10; i++) {
        Insere(randint(0, 9), lst1);
        Insere(randint(0, 9), lst2);
    }
    Imprima(lst1);
    Imprima(lst2);
    concatena(lst1, lst2);
    printf("Concatena: ");
    Imprima(lst1);       
    system("pause");
}
```

Uso este código para andar até o final da primeira lista e, na sequência, apontar o final para o início da segunda e  devolver para a memória a cabeça da segunda.


* 3) Lista Ligada Libera.c (ex. 18):

```
#include <stdio.h>
#include <stdlib.h>
struct cel {
       int conteudo;
       struct cel *seg; /* seguinte */
};
typedef struct cel celula;
void Imprima (celula *lst) {
     celula *p;
     for (p = lst->seg; p != NULL; p = p->seg)
         printf ("%d", p->conteudo);
     putchar('\n');
}
void Insere(int y, celula *p){
    celula *nova;
    nova = malloc(sizeof(celula));
    nova->conteudo = y;
    nova->seg = p->seg;
    p->seg = nova;
}
void Remove (celula *p) {
    celula *lixo;
    lixo = p->seg;
    p->seg = lixo->seg;
    free (lixo);
}
int randint(int a, int b){
    double r, x, R = RAND_MAX;
    int i;
    r = rand();
    x = r / (R + 1);
    i = (int) (x * (b - a + 1));
    return a + i;
}
celula * libera(celula *lst){
    celula *p, *q;
    p = lst;
    while (p != NULL){
    	q = p->seg;
    	free(p);
        p = q;
    }
    return NULL;
}
int main(void){
    int i;
    celula *lst;
    lst = malloc(sizeof(celula));
    lst->seg = NULL;
    srand(time(NULL));
    for (i = 0; i < 10; i++)
        Insere(randint(0, 9), lst);
    printf("Antes: ");
    Imprima(lst);
    lst->seg = libera(lst);
    Imprima(lst);
    system("pause");
}
```

Neste código, antes de devolver para a memória preciso salvar o seguinte, senão não sei mais para onde devo ir.

<p align="justify"> Obs.: Inversão e Josephus não cai na prova.<br></p>

* Referência em Python

```
a = [1, 2 ,3]
b = a
a[0]= 42
id(a) será o mesmo que id(b)


para ser diferente tenho que criar um novo objeto, cópia de a 
b = list(a)

a = [1,2,3]
b = lista(a)
a[0]= 42
a será [42,2,3]
b será [1,2,3]
além disso, id(a) será diferente de id(b)
```


```
a = [42, 2, 3]
b = list(a) -> b = [42, 2, 3] // b será uma cópia de a em outro endereço
```

→ [Voltar ao topo](#topo)

## Materiais complementares

https://www.youtube.com/watch?v=hkRC0wdZUUU <br>
https://www.dropbox.com/sh/y9irhflkjlrvy2j/AAA1Uwzd8-L4HlMNiwUFrOfda?dl=0
