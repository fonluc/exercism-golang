### **Need For Speed**

**Instruções**

Neste exercício, você organizará corridas entre vários tipos de carros controlados remotamente. Cada carro possui características próprias de velocidade e consumo de bateria.

Os carros começam com a bateria totalmente carregada (100%). Cada vez que você dirige o carro usando o controle remoto, ele percorre a velocidade do carro em metros e diminui a porcentagem de bateria restante de acordo com o consumo de bateria.

Se a bateria do carro estiver abaixo da porcentagem de consumo da bateria, você não pode mais dirigir o carro.

Cada pista de corrida tem sua própria distância. Os carros são testados verificando se conseguem terminar a pista sem ficar sem bateria.

- **Tarefa 1: Criar um carro controlado remotamente**
    
    Defina um `struct` chamado `Car` com os seguintes campos do tipo `int`:
    
    - `battery`
    - `batteryDrain`
    - `speed`
    - `distance`
    
    Permita criar um carro controlado remotamente definindo uma função `NewCar` que recebe a velocidade do carro em metros e o consumo de bateria como seus dois parâmetros (ambos do tipo `int`) e retorna uma instância de `Car`:
    
    ```go
    speed := 5
    batteryDrain := 2
    car := NewCar(speed, batteryDrain)
    // => Car{speed: 5, batteryDrain: 2, battery: 100, distance: 0}
    ```
    
- **Tarefa 2: Criar uma pista de corrida**
    
    Defina outro `struct` chamado `Track` com o campo `distance` do tipo `int`. Permita criar uma pista de corrida definindo uma função `NewTrack` que recebe a distância da pista em metros como seu único parâmetro (do tipo `int`):
    
    ```go
    distance := 800
    track := NewTrack(distance)
    // => Track{distance: 800}
    ```
    
- **Tarefa 3: Dirigir o carro**
    
    Implemente a função `Drive` que atualiza o número de metros percorridos com base na velocidade do carro e reduz a bateria de acordo com o consumo de bateria. Se não houver bateria suficiente para dirigir mais uma vez, o carro não se moverá:
    
    ```go
    speed := 5
    batteryDrain := 2
    car := NewCar(speed, batteryDrain)
    car = Drive(car)
    // => Car{speed: 5, batteryDrain: 2, battery: 98, distance: 5}
    ```
    
- **Tarefa 4: Verificar se um carro controlado remotamente pode terminar uma corrida**
    
    Para terminar uma corrida, um carro deve ser capaz de percorrer a distância da corrida. Isso significa não drenar sua bateria antes de cruzar a linha de chegada. Implemente a função `CanFinish` que recebe uma instância de `Car` e uma de `Track` como parâmetros e retorna `true` se o carro puder terminar a corrida; caso contrário, retorna `false`.
    
    Presuma que você está atualmente na linha de partida da corrida e liga o motor do carro para a corrida. Considere que a bateria do carro pode não estar totalmente carregada ao iniciar a corrida:
    
    ```go
    speed := 5
    batteryDrain := 2
    car := NewCar(speed, batteryDrain)
    
    distance := 100
    track := NewTrack(distance)
    
    CanFinish(car, track)
    // => true
    ```
    

```go
package speed

// TODO: defina o tipo 'Car'

// NewCar cria um novo carro controlado remotamente com bateria cheia e especificações dadas.
func NewCar(speed, batteryDrain int) Car {
    panic("Por favor, implemente a função NewCar")
}

// TODO: defina o tipo 'Track'

// NewTrack cria uma nova pista de corrida
func NewTrack(distance int) Track {
    panic("Por favor, implemente a função NewTrack")
}

// Drive dirige o carro uma vez. Se não houver bateria suficiente para dirigir mais uma vez,
// o carro não se moverá.
func Drive(car Car) Car {
    panic("Por favor, implemente a função Drive")
}

// CanFinish verifica se um carro é capaz de terminar uma determinada pista.
func CanFinish(car Car, track Track) bool {
    panic("Por favor, implemente a função CanFinish")
}
```

### Solução 1:

- **Criar um carro controlado remotamente**
    
    Defina um `struct` chamado `Car` com os seguintes campos do tipo `int`:
    
    - `battery`
    - `batteryDrain`
    - `speed`
    - `distance`
    
    Permita criar um carro controlado remotamente definindo uma função `NewCar` que recebe a velocidade do carro em metros e o consumo de bateria como seus dois parâmetros (ambos do tipo `int`) e retorna uma instância de `Car` com a bateria cheia (100%) e a distância inicial igual a zero:
    
    ```go
    type Car struct {
        battery      int
        batteryDrain int
        speed        int
        distance     int
    }
    
    // NewCar creates a new remote controlled car with full battery and given specifications.
    func NewCar(speed, batteryDrain int) Car {
        return Car{
            speed:        speed,
            batteryDrain: batteryDrain,
            battery:      100,
            distance:     0,
        }
    }
    ```
    
    **Exemplo de uso:**
    
    ```go
    speed := 5
    batteryDrain := 2
    car := NewCar(speed, batteryDrain)
    // => Car{speed: 5, batteryDrain: 2, battery: 100, distance: 0}
    
    ```
    

### Solução 2:

- **Criar uma pista de corrida**
    
    Defina um `struct` chamado `Track` com um campo `distance` do tipo `int`. Permita criar uma pista de corrida definindo uma função `NewTrack` que recebe a distância da pista em metros como seu único parâmetro (do tipo `int`):
    
    ```go
    // Define the 'Track' type struct
    type Track struct {
        distance int
    }
    
    // NewTrack creates a new track with the given distance.
    func NewTrack(distance int) Track {
        return Track{
            distance: distance,
        }
    }
    ```
    
    **Exemplo de uso:**
    
    ```go
    distance := 800
    track := NewTrack(distance)
    // => Track{distance: 800}
    ```
    

### Solução 3:

- **Tarefa 3: Dirigir o carro**
    
    Implemente a função `Drive` que atualiza o número de metros percorridos com base na velocidade do carro e reduz a bateria de acordo com o consumo de bateria. Se não houver bateria suficiente para dirigir mais uma vez, o carro não se moverá:
    
    ```go
    // Define a função Drive que atualiza o estado do carro
    func Drive(car Car) Car {
        // Verifica se há bateria suficiente para dirigir
        if car.battery >= car.batteryDrain {
            car.distance += car.speed
            car.battery -= car.batteryDrain
        }
        return car
    }
    ```
    
    **Exemplo de uso:**
    
    ```go
    speed := 5
    batteryDrain := 2
    car := NewCar(speed, batteryDrain)
    car = Drive(car)
    // => Car{speed: 5, batteryDrain: 2, battery: 98, distance: 5}
    ```
    

### Solução 4:

- **Tarefa 4: Verificar se um carro controlado remotamente pode terminar uma corrida**
    
    Para que um carro termine uma corrida, ele deve ser capaz de percorrer toda a distância da pista sem drenar sua bateria completamente. Implemente a função `CanFinish` que verifica se o carro consegue completar a corrida dada a distância da pista e a quantidade de bateria restante.
    
    A função `CanFinish` deve simular o percurso do carro e verificar se a distância da corrida é alcançada sem que a bateria fique abaixo do nível necessário para continuar.
    
    - Assume the car is just starting the race
    - You need to calculate the maximum distance a car can drive with the current level of battery
    - The number of times a car can be driven can be calculated by `battery / batteryDrain`.
    - The maximum distance the car can cover is the product of the car's speed and the number of times it can be driven.
    - Knowing the maximum distance the car can drive, compare it with the distance of the race track
    
    **Implementação:**
    
    ```go
    // CanFinish checks if a car is able to finish a certain track.
    func CanFinish(car Car, track Track) bool {
        // Calcula o número máximo de metros que o carro pode percorrer com a bateria disponível
        maxDistance := (car.battery / car.batteryDrain) * car.speed
    
        // Verifica se a distância da pista é menor ou igual à distância máxima que o carro pode percorrer
        return maxDistance >= track.distance
    }
    ```
    
    **Exemplo de uso:**
    
    ```go
    speed := 5
    batteryDrain := 2
    car := NewCar(speed, batteryDrain)
    
    distance := 100
    track := NewTrack(distance)
    
    result := CanFinish(car, track)
    // => true ou false, dependendo da capacidade do carro
    ```