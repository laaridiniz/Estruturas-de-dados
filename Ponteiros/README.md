<h1 align="center">⭐Ponteiros⭐</h1>

<p align="justify">Vetores em C são dados contíguos, isto é, um dado do ladinho do outro (!= Python em que os dados ficam na memória). Isto tem vantagens e desvantagens. Num vídeo-game, se eu quiser mudar uma área enorme, p. ex. sprite, é mais fácil com dados contíguos. Porém, no alto nível, se eu quiser inserir ou remover elementos, é muito ruim, porque preciso mover todos os elementos da direita do inserido ou removido.<br>
<br>
Nessa linha de raciocínio, podemos dizer que o pior caso seria ter que inserir ou remover no início. Como eu resolvo isso? Usando dados.<br>
<br>
Há uma estrutura de dados chamada <b>lista ligada</b> ou <b>lista encadeada</b>. Pensando em uma caça ao tesouro, inserir ou remover pista ficaria muito rápido porque não mudaria os dados de lugar, somente as pistas.<br>
<br>
Em C, há um tipo de dado chamado <b>ponteiro</b>, que serve apenas para apontar a região da memória onde está o dado. Em linhas de código, encontramos um ponteiro da seguinte forma:<br></p>

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
2) Não preciso usar ponteiros para ponteiros. Se não tiver cabeça, preciso alterar lst, que aponta para o início. Só que lst é um ponteiro e se eu passar o endereço de um ponteiro, isso vira no insere, ponteiro para ponteiro.<br></p>

## Material complementar

https://www.youtube.com/watch?v=hkRC0wdZUUU
