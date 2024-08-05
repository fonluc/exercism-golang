### **Blackjack**

**Instruções**

Neste exercício, vamos simular o primeiro turno de um jogo de Blackjack.

Você receberá duas cartas e poderá ver a carta virada para cima do dealer. Todas as cartas são representadas por uma string como "ace", "king", "three", "two", etc. Os valores de cada carta são:

| Carta | Valor |
| --- | --- |
| ace | 11 |
| two | 2 |
| three | 3 |
| four | 4 |
| five | 5 |
| six | 6 |
| seven | 7 |
| eight | 8 |
| nine | 9 |
| ten | 10 |
| jack | 10 |
| queen | 10 |
| king | 10 |
| other | 0 |

Nota: Comumente, ases podem ter o valor de 1 ou 11, mas para simplificar, assumiremos que eles têm apenas o valor de 11.

Dependendo das suas duas cartas e da carta do dealer, há uma estratégia para o primeiro turno do jogo, com as seguintes opções:

- Stand (S)
- Hit (H)
- Split (P)
- Automatically win (W)

Embora ainda não seja otimizado, você seguirá a estratégia que seu amigo Alex desenvolveu, que é a seguinte:

- Se você tiver um par de ases, você deve sempre dividi-los (split).
- Se você tiver um Blackjack (duas cartas que somam 21) e o dealer não tiver um ás, uma figura ou um dez, você ganha automaticamente. Se o dealer tiver qualquer uma dessas cartas, você deve ficar (stand) e esperar a revelação da outra carta.
- Se a soma das suas cartas estiver no intervalo [17, 20], você deve sempre ficar (stand).
- Se a soma das suas cartas estiver no intervalo [12, 16], você deve sempre ficar (stand), a menos que o dealer tenha uma carta 7 ou maior, caso em que você deve sempre pedir uma carta (hit).
- Se a soma das suas cartas for 11 ou menor, você deve sempre pedir uma carta (hit).

1. Implemente uma função para calcular o valor numérico de uma carta:

```go
// ParseCard retorna o valor inteiro de uma carta seguindo as regras do Blackjack.
func ParseCard(card string) int {
    panic("Por favor, implemente a função ParseCard")
}
```

```go
value := ParseCard("ace")
fmt.Println(value)
// Saída: 11
```

1. Escreva uma função que implemente a lógica de decisão conforme descrito acima:

```go
// FirstTurn retorna a decisão para o primeiro turno, dadas duas cartas do jogador e uma carta do dealer.
func FirstTurn(card1, card2, dealerCard string) string {
    panic("Por favor, implemente a função FirstTurn")
```

**Exemplos de Resultados Esperados**

Aqui estão alguns exemplos dos resultados esperados:

- `FirstTurn("ace", "ace", "jack")` deve retornar `"P"`
- `FirstTurn("ace", "king", "ace")` deve retornar `"S"`
- `FirstTurn("five", "queen", "ace")` deve retornar `"H"`

---

### Solução 1:

**Implemente uma função para calcular o valor numérico de uma carta**

A função `ParseCard` deve receber a string `card` (por exemplo, `"ace"`) e retornar o seu valor correspondente (por exemplo, `11`). Utilize um `switch` para mapear as cartas para seus valores.

**Código:**

```go
// ParseCard retorna o valor inteiro de uma carta seguindo as regras do Blackjack.
func ParseCard(card string) int {
    switch card {
    case "ace":
        return 11
    case "two":
        return 2
    case "three":
        return 3
    case "four":
        return 4
    case "five":
        return 5
    case "six":
        return 6
    case "seven":
        return 7
    case "eight":
        return 8
    case "nine":
        return 9
    case "ten", "jack", "queen", "king":
        return 10
    default:
        return 0
    }
}
```

### Explicação das alterações:

1. **Agrupamento de casos**: Combinei os casos de "ten", "jack", "queen", e "king" em um único caso no `switch` para reduzir o número de linhas. Eles têm o mesmo valor, então não há necessidade de tratá-los separadamente.
2. **Retorno direto**: O valor é retornado diretamente a partir de cada caso no `switch`, o que mantém o código claro e compacto.

Essa versão reduz o número total de linhas sem comprometer a clareza do código.

### Solução 2:

Implemente a função `FirstTurn` para decidir a ação no primeiro turno de um jogo de Blackjack com base nas cartas do jogador e na carta do dealer.

1. **Utilize a função `ParseCard` para determinar o valor de cada carta.**
2. **Calcule a pontuação do jogador somando os valores das duas cartas do jogador.**
3. **Decida a ação a ser tomada com base na pontuação do jogador e na carta do dealer.**

```go
// FirstTurn retorna a decisão para o primeiro turno, dadas duas cartas do jogador e uma carta do dealer.
func FirstTurn(card1, card2, dealerCard string) string {
    playerScore, dealerScore := ParseCard(card1)+ParseCard(card2), ParseCard(dealerCard)

    switch {
    case card1 == "ace" && card2 == "ace":
        return "P"
    case playerScore == 21 && dealerScore < 10:
        return "W"
    case playerScore >= 17:
        return "S"
    case playerScore >= 12 && dealerScore >= 7:
        return "H"
    case playerScore <= 11:
        return "H"
    default:
        return "S"
    }
}
```

### Explicação das alterações:

1. **Combinei a declaração de `playerScore` e `dealerScore`** em uma única linha.
2. **Utilizei um `switch` com condições booleanas** para simplificar a lógica, o que reduz a quantidade de linhas.
3. **Mantenha a verificação de Blackjack** diretamente no `switch` com `playerScore == 21 && dealerScore < 10`.
4. **Verifique a soma das cartas do jogador** com `playerScore >= 17` para retorno `"S"` e `playerScore >= 12 && dealerScore >= 7` para retorno `"H"`.
5. **O caso `default`** cobre o cenário em que `playerScore` é 11 ou menor, retornando `"H"`.

Esta versão compacta mantém a clareza e a eficiência, ao mesmo tempo em que reduz a quantidade de linhas e melhora a legibilidade.

**Exemplos de Resultados Esperados**

- `FirstTurn("ace", "ace", "jack")` deve retornar `"P"`
- `FirstTurn("ace", "king", "ace")` deve retornar `"S"`
- `FirstTurn("five", "queen", "ace")` deve retornar `"H"`

**Lógica da Função:**

1. **Verificar se o jogador tem um par de ases:**
    - Se sim, retorna `"P"` (dividir).
2. **Verificar se o jogador tem um Blackjack:**
    - Se a pontuação do jogador for 21 e o dealer não tiver um ás, figura ou dez, o jogador ganha automaticamente (`"W"`).
    - Caso contrário, se o dealer tiver um ás, figura ou dez, o jogador deve ficar (`"S"`).
3. **Verificar a soma das cartas do jogador:**
    - Se estiver no intervalo [17, 20], retorna `"S"` (ficar).
    - Se estiver no intervalo [12, 16], retorna `"H"` (pedir uma carta) se o dealer tiver 7 ou mais; caso contrário, retorna `"S"` (ficar).
4. **Se a soma das cartas do jogador for 11 ou menor, retorna `"H"` (pedir uma carta).**