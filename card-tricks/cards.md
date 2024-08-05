## **Card Tricks**

### Instruções

Como uma aspirante a maga, Elyse precisa praticar alguns conceitos básicos. Ela tem um baralho de cartas que deseja manipular.

Para facilitar um pouco, ela usa apenas as cartas de 1 a 10.

1. **Criar um slice com algumas cartas:**

Quando pratica com suas cartas, Elyse gosta de começar com suas três cartas favoritas do baralho: 2, 6 e 9. Escreva uma função `FavoriteCards` que retorne uma fatia com essas cartas na ordem especificada.

```go
cards := FavoriteCards()
fmt.Println(cards)
// Saída: [2 6 9]
```

1. **Retorne a carta na posição do índice da pilha fornecida.**

```go
card := GetItem([]int{1, 2, 4, 1}, 2) // card == 4
```

Se o índice estiver fora dos limites (ou seja, se for negativo ou estiver após o final da pilha), queremos retornar -1:

```go
card := GetItem([]int{1, 2, 4, 1}, 10) // card == -1
```

> **Observação**
> 

> Por convenção em Go, um erro é retornado em vez de retornar um valor "fora dos limites". Aqui, o valor "fora dos limites" é -1 quando um número positivo é esperado. Retornar um erro com o valor zero será abordado em um exercício futuro.
> 
1. **Troque a carta na posição do índice pela nova carta fornecida e retorne a pilha ajustada. Note que isso modificará o slice de entrada, o que é o comportamento esperado.**

```go
index := 2
newCard := 6
cards := SetItem([]int{1, 2, 4, 1}, index, newCard)
fmt.Println(cards)
// Saída: [1 2 6 1]
```

Se o índice estiver fora dos limites (ou seja, se for negativo ou estiver após o final da pilha), queremos adicionar a nova carta ao final da pilha:

```go
index := -1
newCard := 6
cards := SetItem([]int{1, 2, 4, 1}, index, newCard)
fmt.Println(cards)
// Saída: [1 2 4 1 6]
```

1. **Adicione a(s) carta(s) especificada(s) no parâmetro `values` ao topo da pilha.**

```go
slice := []int{3, 2, 6, 4, 8}
cards := PrependItems(slice, 5, 1)
fmt.Println(cards)
// Saída: [5 1 3 2 6 4 8]
```

Se nenhum argumento for dado para o parâmetro `values`, então o resultado será o slice original.

```go
slice := []int{3, 2, 6, 4, 8}
cards := PrependItems(slice)
fmt.Println(cards)
// Saída: [3 2 6 4 8]
```

1. **Remova a carta na posição do índice da pilha e retorne a pilha. Note que isso pode modificar o slice de entrada, o que é aceitável.**

```go
cards := RemoveItem([]int{3, 2, 6, 4, 8}, 2)
fmt.Println(cards)
// Saída: [3 2 4 8]
```

Se o índice estiver fora dos limites (ou seja, se for negativo ou estiver após o final da pilha), queremos deixar a pilha inalterada:

```go
cards := RemoveItem([]int{3, 2, 6, 4, 8}, 11)
fmt.Println(cards)
// Saída: [3 2 6 4 8]
```

### Código

```go
package cards

// FavoriteCards retorna uma fatia com as cartas 2, 6 e 9 nessa ordem.
func FavoriteCards() []int {
	panic("Por favor, implemente a função FavoriteCards")
}

// GetItem recupera um item de uma fatia na posição dada.
// Se o índice estiver fora dos limites, deve retornar -1.
func GetItem(slice []int, index int) int {
	panic("Por favor, implemente a função GetItem")
}

// SetItem escreve um item em uma fatia na posição dada sobrescrevendo um valor existente.
// Se o índice estiver fora dos limites, o valor precisa ser adicionado ao final.
func SetItem(slice []int, index, value int) []int {
	panic("Por favor, implemente a função SetItem")
}

// PrependItems adiciona um número arbitrário de valores ao início de uma fatia.
func PrependItems(slice []int, values ...int) []int {
	panic("Por favor, implemente a função PrependItems")
}

// RemoveItem remove um item de uma fatia modificando a fatia existente.
func RemoveItem(slice []int, index int) []int {
	panic("Por favor, implemente a função RemoveItem")
}
```

### Solução 1:

**Criar um slice com algumas cartas:**

Quando Elyse pratica com suas cartas, ela gosta de começar com suas três cartas favoritas do baralho: 2, 6 e 9. Escreva uma função `FavoriteCards` que retorne um slice com essas cartas na ordem especificada.

```go
cards := FavoriteCards()
fmt.Println(cards)
// Saída: [2 6 9]
```

Para criar um slice pré-preenchido com alguns dados, use a notação literal de slice: `s := []T{x1, x2, ..., xn}`

```go
func FavoriteCards() []int {
    cards := []int{2, 6, 9}
    return cards
}
```

### Solução 2:

**Retorne a carta na posição do índice da pilha fornecida.**

```go
card := GetItem([]int{1, 2, 4, 1}, 2) // card == 4
```

Se o índice estiver fora dos limites (ou seja, se for negativo ou estiver após o final da pilha), queremos retornar -1:

```go
card := GetItem([]int{1, 2, 4, 1}, 10) // card == -1
```

> Observação
> 
> 
> Por convenção em Go, um erro é retornado em vez de retornar um valor "fora dos limites". Aqui, o valor "fora dos limites" é -1 quando um número positivo é esperado. Retornar um erro com o valor zero será abordado em um exercício futuro.
> 

```go
func GetItem(slice []int, index int) int {
    if index >= 0 && index < len(slice) {
        return slice[index]
    }
    return -1
}
```

### Solução 3:

**Troque a carta na posição do índice pela nova carta fornecida e retorne a pilha ajustada. Note que isso modificará o slice de entrada, o que é o comportamento esperado.**

```go
index := 2
newCard := 6
cards := SetItem([]int{1, 2, 4, 1}, index, newCard)
fmt.Println(cards)
// Saída: [1 2 6 1]
```

Se o índice estiver fora dos limites (ou seja, se for negativo ou estiver após o final da pilha), queremos adicionar a nova carta ao final da pilha:

```go
index := -1
newCard := 6
cards := SetItem([]int{1, 2, 4, 1}, index, newCard)
fmt.Println(cards)
// Saída: [1 2 4 1 6]
```

- Para definir o item `n` em um slice, **use um índice** e atribua um novo valor a ele.
- Para adicionar um novo item ao final de um slice, use a função `append`.

```go
func SetItem(slice []int, index, value int) []int {
    if index >= 0 && index < len(slice) {
        slice[index] = value
    } else {
        slice = append(slice, value)
    }
    return slice
}
```

### Solução 4:

```go
slice := []int{3, 2, 6, 4, 8}
cards := PrependItems(slice, 5, 1)
fmt.Println(cards)
// Saída: [5 1 3 2 6 4 8]
```

Se nenhum argumento for dado para o parâmetro `values`, então o resultado será o slice original.

```go
slice := []int{3, 2, 6, 4, 8}
cards := PrependItems(slice)
fmt.Println(cards)
// Saída: [3 2 6 4 8]
```

- Adicionar itens ao início de um slice pode ser feito adicionando os elementos do slice original ao slice do argumento `values`.

```go
func PrependItems(slice []int, values ...int) []int {
    // Cria um novo slice com os valores a serem adicionados no início
    result := append(values, slice...)
    return result
}
```

### Solução 5:

```go
func RemoveItem(slice []int, index int) []int {
    if index >= 0 && index < len(slice) {
        return append(slice[:index], slice[index+1:]...)
    }
    return slice
}
```

### Explicação Detalhada:

1. **Verificação do Índice:**
    - A função `RemoveItem` começa verificando se o índice fornecido está dentro dos limites válidos do slice. O índice deve ser não-negativo e menor que o comprimento do slice. Se o índice estiver fora desses limites, a função simplesmente retorna o slice original sem modificações.
2. **Remoção do Item:**
    - Se o índice for válido, a função remove o item localizado na posição especificada. Isso é feito utilizando a função `append` para concatenar duas fatias do slice:
        - `slice[:index]` representa todos os elementos antes do item que deve ser removido.
        - `slice[index+1:]` representa todos os elementos após o item que deve ser removido.
    - A função `append` combina essas duas partes, efetivamente excluindo o item na posição `index` e retornando o slice atualizado.
3. **Retorno do Slice:**
    - Se o índice não for válido, a função retorna o slice original sem modificações. Isso garante que o comportamento da função seja seguro e não cause erros inesperados.