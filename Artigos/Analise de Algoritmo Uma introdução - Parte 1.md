## Analise de Algoritmo: Uma introdução - Parte 1

Se você está iniciando no mundo da programação, é provável que tenha se perguntado como medir a eficiência e desempenho de um algoritmo, e como saber qual é o mais eficiente entre dois algoritmos que resolvem o mesmo problema? Para responder essas perguntas, é necessário entender que, ao ser executado por uma máquina, um algoritmo consome diversos recursos que podem ser medidos, como memória (**complexidade em espaço**), processamento (**complexidade em tempo**) e banda de internet, entre outros. Neste artigo, focaremos apenas na complexidade em tempo.

A complexidade em tempo é uma medida que descreve o tempo de execução de um algoritmo em relação ao tamanho da entrada. Ela representa a quantidade de tempo que um algoritmo leva para processar uma determinada quantidade de dados de entrada, ou seja, a complexidade está diretamente ligada à quantidade de dados que ele processa (N) e à quantidade de instruções executadas(Q).

Existem diferentes formas de medir a complexidade de um algoritmo, uma delas é a forma empírica, na qual é executado um algoritmo, medido o tempo de execução e depois comparado em diferentes algoritmos. No entanto, essa forma de medição pode ser influenciada por diversos fatores externos, como o hardware utilizado (desempenho do processador, memória RAM, etc.), a linguagem de programação e o compilador utilizados, além das entradas de teste e do ambiente de execução. Portanto, essa forma de medir a complexidade de um algoritmo pode não ser muito precisa e pode levar a conclusões equivocadas.

Outro método mais eficiente é o analítico, que tem uma abordagem mais precisa para medir a complexidade que busca encontrar uma expressão matemática para traduzir o desempenho em quantidade de instruções. Diferentemente de calcular o tempo de execução em segundos ou minutos, o objetivo é contar as instruções que o algoritmo executa para chegar em uma formula matemática.

Em um computador real, podem ser encontrados vários tipos diferentes de instruções, como aritméticas (soma, subtração, multiplicação, divisão, resto, piso, teto), de movimentação de dados (carregar, armazenar, copiar) e de controle (desvio condicional, chamada e retorno de sub-rotinas). No entanto, é extremamente difícil medir o custo de cada instrução, já que eles podem variar entre hardwares, linguagens de programação e outros fatores físicos. Para fins didáticos, cada instrução é considerada ter um custo constante.

## Exemplos

Vamos analisa dois algoritmos escrito em Python para tem um entendimento melhor.

Exemplo 1: Algoritmo que recebe dois número, faz a soma e retorna se é maior que cem ou menor:

```python
number1 = int(input("digite um número: "))        # 2 instruções
number2 = int(input("digite um número: "))        # 2 instruções

soma = number1 + number2                          # 1 instrução

if(soma>100):                                     # 1 instrução
    print("maior que cem")                        # 1 instrução
else:
    print("menor ou igual a cem")                 # 1 instrução
```

- Na primeira e segunda linha temos duas instruções, receber um valor e converter em inteiro;
- Na quarta linha temos uma soma;
- Na sexta temos uma comparação se o número é maior que cem;
- na sétima e nona linha temos uma instrução em cada, mas a estrutura **IF/ELSE** é mutuamente exclusivas, caso seja executado o bloco do **IF** não será executado o bloco do **ELSE** e vice-versa. Neste caso as duas juntas são executadas N vezes.

Então somando as instruções temos a função T(n) = 7 

Exemplo 2: Algoritmo que percorre uma lista de números inteiros e analise se é par ou impar:

```python
def numeroPar(n):
    for i in n:                 # 1 instrução executada N vezes
        if i % 2 == 0:          # 2 instruções - resto da divisão = N vezes || conparação = N vezes
            print("Par")        # 1 instrução 
        else:                   
            print("impar")      # 1 instrução
```

- Na segunda linha temos um **FOR** com uma instrução de atribuição que será executada N vezes (tamanho da lista). 

- Na terceira linha temos duas instruções: calcular o resto da divisão e comparar se o resultado é igual a zero, cada uma será executada N vezes. 

- Na quarta e sexta temos um retorno cada.

Então somando as instruções temos a função T(n) = n + (n+n) + n = 4n

### Taxa de Crescimento

A partir de uma função que representa o custo, é possível realizar a análise gráfica do algoritmo e tentar prever a **taxa de crescimento** baseada no tamanho da entrada. Vamos utilizar a função T(n) = 4n e as entradas de tamanho 0, 10, 20, 30, 40 e 50:

T(0) = 4.0 = 0

T(10) = 4.10 = 40

T(20) = 4.20 = 80

T(30) = 4.30 = 120

T(40) = 4.40 = 160

T(50) = 4.50 = 200

<img src=".\imagens\1 - linear.png" style="zoom:40%;" />

### Classificação de Algoritmos

Agora que você sabe calcular a complexidade de Algoritmos, podemos classificados em algumas categorias principais: Complexidade Constante O(1), Complexidade  Logarítmica O(log n), Complexidade Linear O(n),  Complexidade Quadrática O(n²) e Complexidade Fatorial(n!).

![](.\imagens\1 - gráfico.png)

#### Constante O(1)

Algoritmos constantes são aqueles cuja complexidade não varia com o tamanho da entrada. Isso significa que, independentemente do tamanho da entrada, o tempo de execução do algoritmo será sempre o mesmo. Por exemplo, um algoritmo que simplesmente imprime uma mensagem na tela sempre terá um tempo de execução constante, não importando o tamanho da entrada. A notação assintótica para algoritmos constantes é O(1).

<img src=".\imagens\1 - constante.png" style="zoom:40%;" />

#### logarítmicos O(log n)

Algoritmos logarítmicos são aqueles cujo tempo de execução cresce de forma logarítmica em relação ao tamanho da entrada. Em outras palavras, à medida que o tamanho da entrada aumenta, o tempo de execução aumenta em uma taxa muito mais lenta do que o tamanho da entrada.

Um exemplo comum de algoritmo logarítmico é a pesquisa binária (binary search). Nesse algoritmo, uma lista ordenada é dividida pela metade repetidamente até que o elemento procurado seja encontrado ou até que seja determinado que ele não está na lista. Como a lista é dividida pela metade a cada passo, o número de elementos a serem verificados é reduzido pela metade a cada iteração, o que leva a um crescimento logarítmico no tempo de execução.

<img src=".\imagens\1 - logarítmicos.png" style="zoom:40%;" />

#### Linear O(n)

Algoritmos lineares, também conhecidos como algoritmos de tempo linear, são aqueles que têm uma taxa de crescimento diretamente proporcional ao tamanho da entrada. Isso significa que à medida que a entrada aumenta, o tempo de execução do algoritmo também aumenta na mesma proporção.

Os algoritmos lineares são geralmente considerados bastante eficientes, pois o tempo de execução aumenta de forma previsível com o tamanho da entrada. Alguns exemplos de algoritmos lineares incluem a busca linear em uma lista e a soma de todos os elementos em uma lista.

<img src=".\imagens\1 - linear.png" alt="1 - linear" style="zoom:40%;" />

#### Quadrático O(n²) 

Algoritmos quadráticos são aqueles cuja taxa de crescimento é proporcional ao quadrado do tamanho da entrada. Esses algoritmos tendem a ter um desempenho ruim para entradas grandes. Outro exemplo de algoritmo quadrático é o algoritmo que percorre uma matriz NxN, que consiste em um loop dentro de outro loop.

<img src=".\imagens\1 - Quadrático.png" style="zoom:40%;" />

#### Fatorial O(n!)

Algoritmos fatoriais são aqueles cuja complexidade é proporcional a um fatorial, ou seja, cresce muito rapidamente com o aumento do tamanho da entrada. Algoritmos com complexidade fatorial são geralmente considerados ineficientes para tamanhos de entrada maiores. Um exemplo é o algoritmo que calcula o fatorial de um número, Por exemplo: 

- O fatorial de 5 é igual a 5 x 4 x 3 x 2 x 1 = 120.
- O fatorial de 10  é igual a 10 x 9 x 8 x 7 x 6 x 5 x 4 x 3 x 2 x 1 = 3628800.

De maneira geral, algoritmos fatoriais são considerados muito ineficientes e só são utilizados para tamanhos de entrada muito pequenos. Para tamanhos de entrada maiores, é necessário utilizar algoritmos mais eficientes que tenham uma complexidade menor.

<img src=".\imagens\1 - fatorial.png" style="zoom:40%;" />

### Conclusão

O propósito deste artigo é apresentar uma introdução à análise de algoritmos, enfatizando a avaliação da eficiência de um algoritmo em termos de complexidade de tempo, Isso se refere ao tempo de execução do algoritmo em relação ao tamanho da entrada. Compreender a análise de algoritmos é fundamental para se tornar um programador melhor, pois ajuda a implementar algoritmos mais eficientes e a compreender o comportamento dos algoritmos à medida que os dados aumentam. Sugestão de plataforma para estudar e treinar algoritmos: [hackerrank](https://www.hackerrank.com)  e [beecrowd](https://www.beecrowd.com.br/judge/pt/login)

Agradeço a que leu ate aqui. Critica, sugestões, correções nos comentários abaixo ou no meu e-mail: nathansalesmello@gmail.com. 

 **Próximo Artigo **Notação Assintótica: melhor e pior caso - Em Breve.

### Referências

- Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, Clifford Stein. Algoritmos:  Teoria e Prática. 3a edição. Elsevier, 2012.

- Santiago, David. Análise de algoritmos: como se faz? Disponível em: <https://algol.dev/analise-algoritmos-como-se-faz/>; Acessado em: 17 de abril de 2023.

- Abrantes, Wagner. Análise da Complexidade de Algoritmos. Disponível em: <https://www.iugu.com/iugu4devs/blog/analise-complexidade-algoritmos>; Acessado em: 17 de abril de 2023.

- Know Thy Complexities. Disponível em: <https://www.bigocheatsheet.com>; Acessado em: 17 de abril de 2023.



