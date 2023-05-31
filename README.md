# Estutura de dados

## Objetivo

O objetivo é apresentação e modelagem de estruturas de dados, entendendo conceitos fundamentais, usando o JavaScript, para fazer a apresentação dos tipos de estruturas de dados, e conceitos fundamentais que envolvem o JavaScript.

## Por que **JavaScript**?

Porque JavaScript é a linguagem da WEB, então, faz todo o sentido sua utilização, além de ser uma liguagem de alto nível, ou seja, chega mais próximo do entendimento humano.

## Por que estudar estruturas de dados?

Para organizar os dados da aplicação, pois vamos lidar com vários tipos de dados, então é necessário entendê-los. Precisamos entendê-los para tomar decisões melhores na construção da organização de dados. Além de, melhorar a escrita de algoritmos, e dar mais eficiência para a nossa aplicação.

## O que é estruras de dados

Uma maneira de organizar e ordernar informações (dados) de forma eficiente, essas informações têm um papel fundamental na programação. Essas informações são **números**, **strings**, **booleanos**, **null**, **undefined**, **objetos** e **arrays**.

## Gerenciamento dos dados

A estrutura de dados tem haver com a gestão dos dados da nossa aplicação. Podemos dividir a gestão em 3 etapas:

- Modelar a estrutura;
- Dar vida à estrutura (usar essa estrutura);
- Criar as funcionalidades dessa estrutura.
  - Exemplo: inserir, excluir, buscar, exibir, contar...

## Explicando Arrays

Arrays, vetor ou arranjo, é uma estrutura amplamente utilizada e implementada em quase todas as linguagens de programação.

Uma das estruturas mais básicas, simples de criar e utilizar.

```js
[1, 'a', true, ['b'], function()]
```

No exemplo acima, há no total 5 elementos, o número 1, uma string com a letra _a_, um booleano `true`, um array e uma função. A ordem de contagem de um array começa no 0.

### Características

**Acesso pelo index (posição):** Quando colocamos um array dentro de uma variável, podemos acessar um elemento do array por meio da ordem de contagem:

```js
let nomes = ["Kaio", "Igor", "Luiz"]

let primeiro_nome = nomes[0] // Kaio
let segundo_nome = nomes[1] // Igor
let terceiro_nome = nomes[2] // Luiz
```

**Aceita valores duplicados:** Podemos inserir valores com o mesmo valor e mesmo tipo dentro do array:

```js
[1, 1, 1, "a", "a", "a"]
```

**Os arrays são dinâmicos**: É possível ter dados de diferentes tipos misturados dentro de um Array. String, numbers, booleanos, objetos, funções e até outros arrays.

```js
[1, 'a', true, ['b'], function(), {letra: 'c'}]
```

**Métodos**: Existem muitos métodos de array, funcionalidades expecíficas para arrays como `push()`, `pop()`, `find()`, `filter()` entre outros.

> Dependendo do tamanho do array, para executar alguma atividade como encontrar e/ou deletara um elemento, será necessário de um uso maior de performance.

## Array na prática

### Propriedade lenght

Vimos que é possível, colocar arrays dentro de variáveis:

```js
let array_números = [21, 34, 22.5, 76.77, 33]
```

Acessar um elemento específico:

```js
let array_números = [21, 34, 22.5, 76.77, 33]
console.log(array_números[2]) // 22.5
```

Logo, é possível também, com um comando, saber a quantidade de elementos em um array, utilizando o `length`:

```js
let array_números = [21, 34, 22.5, 76.77, 33]
console.log(array_números.lenght) // 5
```

### Iterando o array

Podemos iterar o array, ou seja, podemos usar o `for...of`, um comando para percorrer o array, e fazer alguma mudança em cada um dos dados:

```js
let array_números = [21, 34, 22.5, 76.77, 33]

for (let elemento of array_números) {
  console.log(elemento * 2)
}
```

Esse comando vai mostrar no console, cada um dos elementos multiplicado por 2.

### Método `find()`

Vamos ver agora o método `find()`, que vai encontrar um elemento específico.

```js
const nomes = ["Paulo", "Ana", "Nicolas", "Beatriz"]

const nicolas = nomes.find((nome) => nome === "Nicolas")

console.log(nicolas) // "Nicolas"
```

O comando acima está procurando algum elemento no array `nomes`, cujo nome é igual a "Nicolas", e colocando dentro da constante `nicolas`.

### Deletando um array

Usamos o método `splice()`, para deletar um ou mais elementos do array, com base em sua posição e na quantidade de elementos a serem deletados:

```js
const nomes = ["Paulo", "Ana", "Nicolas", "Beatriz"]

nomes.splice(1, 1)

console.log(nomes) // ["Paulo", "Nicolas", "Beatriz"]
```

`nomes.splice(1, 1)` este comando deleta elemento apartir da posição 1, e estimar a quantidade de elementos que vão ser excluidos.

## Matriz

Matriz ou vetor multidimencional, basicamente, é um Array dentro de outro Array, e podemos fazer isso em diversos níveis.

```js
const estudantes = [
  ["Matheus", 23, "SP"],
  ["Larissa", 19, "MG"],
  ["Otávius", 20, "AC"],
  ["Manuela", 22, "RS"],
]
```

Para acessar, por exemplo, a idade da Larissa, podemos fazer o seguinte:

```js
const idade_larissa = estudantes[1][1]
console.log(idade_larissa) // 19

const estado_manuela = estudantes[3][2]
console.log(idade_larissa) // "RS"
```

## Explicando o conceito de Stack na programação

Stack significa "pilha", como se fosse uma pilha de livros. Essa pilha é linear, vem um após o outro. Entretanto, o último a entrar é o primeiro a sair, isso é o que chamamos de **LIFO** (Last In FIrst Out).

![LIFO](https://www.tutorialspoint.com/data_structures_algorithms/images/stack_representation.jpg)

## Stack na prática

**Passo 1**: Modelando a estrutura

```js
class Stack {
  constructor() {
    this.data = []
    this.pos = -1
  }

  // adiciona dados à pilha
  push(value) {
    this.pos++
    this.data[this.pos] = value
    return this.data
  }

  // deleta o último elemento colocado à pilha
  pop() {
    if (this.pos < 0) return undefined
    const poppedPos = this.data[this.pos]
    delete this.data[this.pos]
    this.pos--
    return poppedPos
  }

  // mostra qual foi o último dado colocado na pilha
  peek() {
    return this.pos >= 0 ? this.data[this.pos] : undefined
  }

  // mostrando a quantidade de dados na pilha
  size() {
    return this.data.length
  }
}
```

Utilizamos o conceito de classes, então, criamos a classe `Stack`, em seguida, vem o `constructor() {}`, que é a função executada assim que criar o objeto mais tarde. Dentro do _constructor_, será criado um array (`this.data`) que é o array, no qual, é o lugar onde estará guardado os dados, e também terá uma posição (`this.pos`) que começará com -1, e crescerá ou diminuirá com o adicionamento, ou remoção dos dados.

Depois, será criado os `métodos fundamentais`:

- `push()`: adiciona um elemento à pilha.

  - Nesse método, precisamos receber um valor, que será o dado colocado na pilha, então, `push(value) {}`;
  - Dentro das chaves, incrementamos a posição, ou seja, pegamos o valor anterior (-1) e somamos mais 1. Isto, pois a cada valor colocado na pilha, uma nova posição será definida;
  - Depois disso, pegamos o `this.data`, na posição atual irá receber o `value` (`this.data[this.pos] = value`);
  - E retornará todo o array, caso for exibido em um console.

- `pop()`: tira o último elemento adicionado à pilha

  - Se a posição for menor que 0: retorne undefined
  - Pega o último dado com a posição atual e coloca em `poppedPos`
  - Deleta o último dado colocado
  - Decrementa, subtrai 1, a posição atual
  - Retorna o dado que acabou de ser deletado, que está dentro de `poppedPos`

- `peek()`: obtém o último elemento colocado à pilha

  - Se a posição for maior ou igual a 0: retornar o último dado colocado, se não, retornar undefined

- `size()`: obtém o número de elementos na pilha
  - Retorna o `length` de `this.data`

**Passo 2**: Utilizando a estrutura

```js
// instânciando a pilha
const stack = new Stack()

// adicionando dados
stack.push("data1")
stack.push("data2")
console.log(stack.push("data3"))

// mostrando qual foi o último dado colocado
console.log(stack.peek())

// deletando o último elemento colocado
console.log(stack.pop())

// mostrando o tamanho dos dados
console.log(stack.size())
```

## Explicando o conceito de Queue na programação

Queue significa fila, e se nome faz jus à sua função. Queue é como uma fila de uma loja ou restaurante, de maneira linear, assim como o Stack, mas ao contrário do Stack, não é usado FILO (First In Last Out). No Queue se usa o FIFO (First In First Out), ou seja, o primeiro a entrar na fila é o primeiro a sair dela.

![Queue](https://talentbattle.in/Files/C4U_Images/C4U_CKEDITOR_IMAGES/IMG10952_IMG10379_Queue1.png)

Explicando:

- **Enqueue**: Entrando na fila
- **Dequeue**: Saindo da fila
- **Front** (frente): é a referência do primeiro elemento a entrar na fila.
- **Back** (fundo): é a referência do último elemento a entrar na fila.

## Queue na prática

Os passos de criação do Queue são semelhantes aos passos de criação do Stack. Os métodos que iremos criar são `enqueue()`, para adicionar dados na fila e o `dequeue()`, para remover dados da fila. Temos também o `size()` para mostrar o tamanho da fila e o `front()` para pegar o primeiro elemento da fila.

**Passo 1**: Modelando a estrutura

```js
class Queue {
  constructor() {
    this.data = []
  }

  enqueue(value) {
    this.data.push(value)
    return `${this.data[0]} has been added to the queue`
  }

  dequeue() {
    const data = this.data[0]
    this.data.shift()
    return `${data} has been deleted`
  }

  size() {
    return `there are  ${this.data.length} elements in the queue: ${this.data}`
  }

  front() {
    return this.data[0]
  }
}
```

**Passo 2**: Utilizando a estrutura

```js
const queue = new Queue()

// adicionando dados à queue
queue.enqueue("data1")
queue.enqueue("data2")
queue.enqueue("data3")
console.log(queue.enqueue("data4"))

// removendo o primeiro elemento da queue
console.log(queue.dequeue())

// obtendo o primeiro elemento da queue
console.log(queue.front())

// Obtendo o tamanho da queue
console.log(queue.size())
```
