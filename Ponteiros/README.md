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

<p align="justify"></p>
