### Compra de Veículo

**Instruções**

Neste exercício, você vai escrever algum código para ajudar a se preparar para a compra de um veículo.

Você tem três tarefas: uma para determinar se você precisa de uma licença, outra para ajudar a escolher entre dois veículos e uma para estimar o preço aceitável para um veículo usado.

---

### **Tarefa 1: Determinar se você precisará de uma licença de motorista**

Alguns tipos de veículos requerem uma licença de motorista para serem conduzidos. Assuma que apenas os tipos `"car"` e `"truck"` exigem uma licença, todos os outros podem ser conduzidos sem licença.

Implemente a função `NeedsLicense(kind)` que recebe o tipo de veículo e retorna um booleano indicando se você precisa de uma licença para esse tipo de veículo.

```go
needLicense := NeedsLicense("car")
// => true

needLicense = NeedsLicense("bike")
// => false

needLicense = NeedsLicense("truck")
// => true
```

---

### **Tarefa 2: Escolher entre dois veículos potenciais**

Você avaliou suas opções de veículos disponíveis e conseguiu reduzi-las a duas opções, mas precisa de ajuda para tomar a decisão final. Para isso, implemente a função `ChooseVehicle(option1, option2)` que recebe dois veículos como argumentos e retorna uma decisão que inclui a opção que vem primeiro em ordem lexicográfica.

```go
vehicle := ChooseVehicle("Wuling Hongguang", "Toyota Corolla")
// => "Toyota Corolla is clearly the better choice."

ChooseVehicle("Volkswagen Beetle", "Volkswagen Golf")
// => "Volkswagen Beetle is clearly the better choice."
```

---

### **Tarefa 3: Calcular uma estimativa para o preço de um veículo usado**

Agora que você tomou uma decisão, deseja garantir que obtenha um preço justo na concessionária. Como você está interessado em comprar um veículo usado, o preço depende da idade do veículo. Para uma estimativa aproximada, assume-se que, se o veículo tiver menos de 3 anos, custa 80% do preço original que tinha quando era novo. Se tiver pelo menos 10 anos, custa 50%. Se o veículo tiver pelo menos 3 anos, mas menos de 10 anos, custa 70% do preço original.

Implemente a função `CalculateResellPrice(originalPrice, age)` que aplica essa lógica usando `if`, `else if` e `else` (existem outras formas se você quiser praticar). Ela recebe o preço original e a idade do veículo como argumentos e retorna o preço estimado na concessionária.

```go
CalculateResellPrice(1000, 1)
// => 800

CalculateResellPrice(1000, 5)
// => 700

CalculateResellPrice(1000, 15)
// => 500
```

**Nota:** O valor de retorno é um `float64`.

---

### Código inicial:

```go
package purchase

// NeedsLicense determines whether a license is needed to drive a type of vehicle. Only "car" and "truck" require a license.
func NeedsLicense(kind string) bool {
    panic("NeedsLicense not implemented")
}

// ChooseVehicle recommends a vehicle for selection. It always recommends the vehicle that comes first in lexicographical order.
func ChooseVehicle(option1, option2 string) string {
    panic("ChooseVehicle not implemented")
}

// CalculateResellPrice calculates how much a vehicle can resell for at a certain age.
func CalculateResellPrice(originalPrice, age float64) float64 {
    panic("CalculateResellPrice not implemented")
}
```

### Solução 1:

**Tarefa 1: Determinar se você precisará de uma licença de motorista**

Alguns tipos de veículos requerem uma licença de motorista para serem conduzidos. Assuma que apenas os tipos `"car"` e `"truck"` exigem uma licença, todos os outros podem ser conduzidos sem licença.

Implemente a função `NeedsLicense(kind)` que recebe o tipo de veículo e retorna um booleano indicando se você precisa de uma licença para esse tipo de veículo.

```go
func NeedsLicense(kind string) bool {
    return kind == "car" || kind == "truck"
}
```

### Solução 2:

**Escolher entre dois veículos potenciais**

Você avaliou suas opções de veículos disponíveis e conseguiu reduzi-las a duas opções, mas precisa de ajuda para tomar a decisão final. Para isso, implemente a função `ChooseVehicle(option1, option2)` que recebe dois veículos como argumentos e retorna uma decisão que inclui a opção que vem primeiro em ordem alfabética.

```go
func ChooseVehicle(option1, option2 string) string {
    if option1 < option2 {
        return option1 + " is clearly the better choice."
    }
    return option2 + " is clearly the better choice."
}
```

Exemplos de uso:

```go
vehicle := ChooseVehicle("Wuling Hongguang", "Toyota Corolla")
// => "Toyota Corolla is clearly the better choice."

ChooseVehicle("Volkswagen Beetle", "Volkswagen Golf")
// => "Volkswagen Beetle is clearly the better choice."
```

### Solução 3:

**Calcular uma estimativa para o preço de um veículo usado**

Agora que você tomou uma decisão, deseja garantir que obtenha um preço justo na concessionária. Como você está interessado em comprar um veículo usado, o preço depende da idade do veículo. Para uma estimativa aproximada, assume-se que:

- Se o veículo tiver menos de 3 anos, custa 80% do preço original.
- Se tiver pelo menos 10 anos, custa 50%.
- Se o veículo tiver pelo menos 3 anos, mas menos de 10 anos, custa 70% do preço original.

Implemente a função `CalculateResellPrice(originalPrice, age)` que aplica essa lógica usando `if`, `else if` e `else`. Ela recebe o preço original e a idade do veículo como argumentos e retorna o preço estimado na concessionária.

```go
func CalculateResellPrice(originalPrice, age float64) float64 {
    if age < 3 {
        return originalPrice * 0.8
    } else if age < 10 {
        return originalPrice * 0.7
    } else {
        return originalPrice * 0.5
    }
}
```

Exemplos de uso:

```go
CalculateResellPrice(1000, 1)
// => 800

CalculateResellPrice(1000, 5)
// => 700

CalculateResellPrice(1000, 15)
// => 500
```