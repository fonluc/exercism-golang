## **Annalyn's Infiltration**

### Instruções

Neste exercício, você implementará a lógica de uma missão para um novo jogo RPG que um amigo está desenvolvendo. O personagem principal do jogo é Annalyn, uma garota corajosa com um cachorro fiel. Infelizmente, o pior acontece: seu melhor amigo foi sequestrado enquanto procurava frutas na floresta. Annalyn tentará encontrá-lo e libertá-lo, podendo levar seu cachorro com ela na missão.

Após algum tempo seguindo a trilha do amigo sequestrado, Annalyn encontra o acampamento onde ele está preso. Descobre que há dois sequestradores: um cavaleiro poderoso e um arqueiro astuto.

Tendo encontrado os sequestradores, Annalyn considera quais das seguintes ações ela pode realizar:

1. **Ataque rápido**: Um ataque rápido pode ser feito se o cavaleiro estiver dormindo, pois leva tempo para ele colocar sua armadura e ele ficará vulnerável.
2. **Espionar**: O grupo pode ser espionado se pelo menos um deles estiver acordado. Caso contrário, espiar é uma perda de tempo.
3. **Sinalizar o prisioneiro**: O prisioneiro pode ser sinalizado usando sinais de pássaros se o prisioneiro estiver acordado e o arqueiro estiver dormindo, pois os arqueiros são treinados em sinais de pássaros e poderiam interceptar a mensagem.
4. **Libertar o prisioneiro**: Annalyn pode tentar se esgueirar para o acampamento e libertar o prisioneiro. Isso é arriscado e pode ter sucesso de duas maneiras:
    - Se Annalyn estiver com seu cachorro, ela pode resgatar o prisioneiro se o arqueiro estiver dormindo. O cavaleiro tem medo do cachorro e o arqueiro não terá tempo para se preparar antes que Annalyn e o prisioneiro possam escapar.
    - Se Annalyn não tiver seu cachorro, ela e o prisioneiro precisam ser muito discretos! Annalyn pode libertar o prisioneiro se o prisioneiro estiver acordado e o cavaleiro e o arqueiro estiverem ambos dormindo. Se o prisioneiro estiver dormindo, não pode ser resgatado: o prisioneiro se assustaria com a súbita aparição de Annalyn e acordaria o cavaleiro e o arqueiro.

Você tem quatro tarefas: implementar a lógica para determinar se as ações acima estão disponíveis com base no estado dos três personagens encontrados na floresta e na presença ou ausência do cachorro de Annalyn.

### Funções a Implementar

1. **CanFastAttack**: Define a função que recebe um valor booleano indicando se o cavaleiro está acordado. Esta função retorna `true` se um ataque rápido puder ser realizado com base no estado do cavaleiro. Caso contrário, retorna `false`.

```go
var knightIsAwake = true
fmt.Println(CanFastAttack(knightIsAwake))
// Saída: false
```

1. **CanSpy**: Define a função que recebe três valores booleanos, indicando se o cavaleiro, o arqueiro e o prisioneiro, respectivamente, estão acordados. A função retorna `true` se o grupo puder ser espionado, com base no estado dos três personagens. Caso contrário, retorna `false`.

```go
var knightIsAwake = false
var archerIsAwake = true
var prisonerIsAwake = false
fmt.Println(CanSpy(knightIsAwake, archerIsAwake, prisonerIsAwake))
// Saída: true
```

1. **CanSignalPrisoner**: Define a função que recebe dois valores booleanos, indicando se o arqueiro e o prisioneiro, respectivamente, estão acordados. A função retorna `true` se o prisioneiro puder ser sinalizado, com base no estado dos dois personagens. Caso contrário, retorna `false`.

```go
var archerIsAwake = false
var prisonerIsAwake = true
fmt.Println(CanSignalPrisoner(archerIsAwake, prisonerIsAwake))
// Saída: true
```

1. **CanFreePrisoner**: Define a função que recebe quatro valores booleanos. Os três primeiros parâmetros indicam se o cavaleiro, o arqueiro e o prisioneiro, respectivamente, estão acordados. O último parâmetro indica se o cachorro de Annalyn está presente. A função retorna `true` se o prisioneiro puder ser libertado com base no estado dos três personagens e na presença do cachorro de Annalyn. Caso contrário, retorna `false`.

```go
var knightIsAwake = false
var archerIsAwake = true
var prisonerIsAwake = false
var petDogIsPresent = false
fmt.Println(CanFreePrisoner(knightIsAwake, archerIsAwake, prisonerIsAwake, petDogIsPresent))
// Saída: false
```

```go
package annalyn

// CanFastAttack pode ser executado apenas quando o cavaleiro está dormindo.
func CanFastAttack(knightIsAwake bool) bool {
	panic("Por favor, implemente a função CanFastAttack()")
}

// CanSpy pode ser executado se pelo menos um dos personagens estiver acordado.
func CanSpy(knightIsAwake, archerIsAwake, prisonerIsAwake bool) bool {
	panic("Por favor, implemente a função CanSpy()")
}

// CanSignalPrisoner pode ser executado se o prisioneiro estiver acordado e o arqueiro estiver dormindo.
func CanSignalPrisoner(archerIsAwake, prisonerIsAwake bool) bool {
	panic("Por favor, implemente a função CanSignalPrisoner()")
}

// CanFreePrisoner pode ser executado se o prisioneiro estiver acordado e os outros 2 personagens estiverem dormindo
// ou se o cachorro de Annalyn estiver presente e o arqueiro estiver dormindo.
func CanFreePrisoner(knightIsAwake, archerIsAwake, prisonerIsAwake, petDogIsPresent bool) bool {
	panic("Por favor, implemente a função CanFreePrisoner()")
}
```

---

### Solução 1:

```go
func CanFastAttack(knightIsAwake bool) bool {
    return !knightIsAwake
}
```

### Explicação Detalhada

A função `CanFastAttack` determina se um ataque rápido pode ser realizado com base no estado do cavaleiro.

- **Entrada**: A função recebe um parâmetro booleano `knightIsAwake`, que indica se o cavaleiro está acordado (`true`) ou não (`false`).
- **Lógica**: A função verifica se o cavaleiro está dormindo usando a negação lógica `!`.
    - Se `knightIsAwake` for `true`, significa que o cavaleiro está acordado e, portanto, um ataque rápido não é possível. A função retorna `false`.
    - Se `knightIsAwake` for `false`, o cavaleiro está dormindo e, portanto, um ataque rápido pode ser realizado. A função retorna `true`.

### Solução 2:

```go
func CanSpy(knightIsAwake, archerIsAwake, prisonerIsAwake bool) bool {
    return knightIsAwake || archerIsAwake || prisonerIsAwake
}
```

### Explicação

A função `CanSpy` determina se o grupo pode ser espionado com base no estado dos três personagens (cavaleiro, arqueiro e prisioneiro).

- **Entrada**: A função recebe três parâmetros booleanos:
    - `knightIsAwake` indica se o cavaleiro está acordado.
    - `archerIsAwake` indica se o arqueiro está acordado.
    - `prisonerIsAwake` indica se o prisioneiro está acordado.
- **Lógica**: A função retorna `true` se pelo menos um dos três personagens estiver acordado. Isso é verificado usando o operador lógico `||` (OR):
    - Se `knightIsAwake` for `true`, `archerIsAwake` for `true`, ou `prisonerIsAwake` for `true`, a função retorna `true`.
    - Se todos os três forem `false`, a função retorna `false`.

### Solução 3:

```go
func CanSignalPrisoner(archerIsAwake, prisonerIsAwake bool) bool {
    return !archerIsAwake && prisonerIsAwake
}
```

### Explicação

A função `CanSignalPrisoner` determina se o prisioneiro pode ser sinalizado com base no estado do arqueiro e do prisioneiro.

- **Entrada**: A função recebe dois parâmetros booleanos:
    - `archerIsAwake` indica se o arqueiro está acordado.
    - `prisonerIsAwake` indica se o prisioneiro está acordado.
- **Lógica**: A função retorna `true` se o prisioneiro puder ser sinalizado, o que ocorre se:
    - O arqueiro estiver **adormecido** (`!archerIsAwake` é `true`).
    - O prisioneiro estiver **acordado** (`prisonerIsAwake` é `true`).

Se ambos os critérios forem atendidos, a função retorna `true`. Caso contrário, retorna `false`.

### Solução 4:

```go
func CanFreePrisoner(knightIsAwake, archerIsAwake, prisonerIsAwake, petDogIsPresent bool) bool {
    return (!knightIsAwake && !archerIsAwake && prisonerIsAwake) || (!archerIsAwake && petDogIsPresent)
}
```

### Explicação

A função `CanFreePrisoner` verifica se o prisioneiro pode ser libertado com base no estado do cavaleiro, do arqueiro, do prisioneiro e na presença do cachorro de Annalyn. A função retorna `true` se qualquer uma das seguintes condições for verdadeira:

1. **Annalyn pode libertar o prisioneiro sem o cachorro**:
    - O cavaleiro está **adormecido** (`!knightIsAwake` é `true`).
    - O arqueiro está **adormecido** (`!archerIsAwake` é `true`).
    - O prisioneiro está **acordado** (`prisonerIsAwake` é `true`).
2. **Annalyn pode libertar o prisioneiro com o cachorro**:
    - O arqueiro está **adormecido** (`!archerIsAwake` é `true`).
    - O cachorro de Annalyn está **presente** (`petDogIsPresent` é `true`).

Se qualquer uma dessas condições for atendida, a função retorna `true`. Caso contrário, retorna `false`.