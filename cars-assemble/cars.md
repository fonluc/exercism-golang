## **Cars Assemble**

### Instruções

Neste exercício, você escreverá código para analisar a produção em uma fábrica de automóveis.

1. **Calcule o número de carros funcionando produzidos por hora**
    
    Os carros são produzidos em uma linha de montagem. A linha de montagem tem uma certa velocidade, que pode ser alterada. Quanto maior a velocidade da linha de montagem, mais carros são produzidos. No entanto, alterar a velocidade da linha de montagem também altera o número de carros produzidos com sucesso, ou seja, carros sem erros na produção.
    
    Implemente uma função que receba o número de carros produzidos por hora e a taxa de sucesso e calcule o número de carros bem-sucedidos produzidos por hora. A taxa de sucesso é dada como uma porcentagem, de 0 a 100:
    
    ```go
    CalculateWorkingCarsPerHour(1547, 90)
    // => 1392.3
    ```
    
    Nota: O valor retornado deve ser um `float64`.
    
2. **Calcule o número de carros funcionando produzidos por minuto**
    
    Implemente uma função que receba o número de carros produzidos por hora e a taxa de sucesso e calcule quantos carros são produzidos com sucesso a cada minuto:
    
    ```go
    CalculateWorkingCarsPerMinute(1105, 90)
    // => 16
    ```
    
    Nota: O valor retornado deve ser um `int`.
    
3. **Calcule o custo de produção**
    
    Cada carro normalmente custa $10.000 para ser produzido individualmente, independentemente de ser bem-sucedido ou não. Mas com um pouco de planejamento, 10 carros podem ser produzidos juntos por $95.000.
    
    Por exemplo, 37 carros podem ser produzidos da seguinte forma: 37 = 3 grupos de dez + 7 carros individuais
    
    Portanto, o custo para 37 carros é: 3 * 95.000 + 7 * 10.000 = 355.000
    
    Implemente a função `CalculateCost` que calcula o custo de produzir um número de carros, independentemente de serem bem-sucedidos ou não:
    
    ```go
    CalculateCost(37)
    // => 355000
    
    CalculateCost(21)
    // => 200000
    ```
    
    Nota: O valor retornado deve ser um `uint`.
    

### Solução 1:

```go
package cars

// CalculateWorkingCarsPerHour calculates how many working cars are
// produced by the assembly line every hour.
func CalculateWorkingCarsPerHour(productionRate int, successRate float64) float64 {
    successRate /= 100 // Convert percentage to a decimal
    return float64(productionRate) * successRate
}
```

1. **Objetivo da Função**:
A função `CalculateWorkingCarsPerHour` deve calcular o número de carros funcionais produzidos por hora com base na taxa de sucesso fornecida. A taxa de sucesso é dada como uma porcentagem, e precisamos converter isso para um valor decimal para realizar a multiplicação correta.
2. **Parâmetros da Função**:
    - `productionRate` (int): O número total de carros produzidos por hora.
    - `successRate` (float64): A taxa de sucesso em porcentagem (de 0 a 100).
3. **Processo de Cálculo**:
    - **Converter a Porcentagem para Decimal**: A taxa de sucesso é uma porcentagem, então para usá-la em cálculos, primeiro convertê-la em um valor decimal. Isso é feito dividindo a taxa de sucesso por 100. Por exemplo, uma taxa de sucesso de 90% é convertida para 0.90.
        
        ```go
        successRate /= 100
        ```
        
    - **Multiplicar para Obter o Número de Carros Funcionais**: Após converter a taxa de sucesso para decimal, multiplique-a pelo número total de carros produzidos. Lembre-se de que, para a multiplicação, ambos os valores precisam estar no mesmo tipo. No Go, o tipo `int` não pode ser diretamente multiplicado com `float64`, então convertemos o `productionRate` para `float64`.
        
        ```go
        return float64(productionRate) * successRate
        ```
        
4. **Retorno da Função**:
A função retorna o resultado da multiplicação, que representa o número de carros produzidos com sucesso por hora. O tipo de retorno é `float64` para acomodar valores decimais, como mostrado no exemplo de saída esperado (`1392.3`).

### Solução 2:

Claro! Vamos explicar a solução detalhadamente:

### Objetivo

```go
func CalculateWorkingCarsPerMinute(productionRate int, successRate float64) int {
    successRate /= 100
    return int(float64(productionRate) / 60 * successRate)
}
```

### Funcionamento

1. **`successRate /= 100`**:
    - Converte a taxa de sucesso de porcentagem para decimal.
2. **`float64(productionRate) / 60`**:
    - Converte `productionRate` para `float64` e calcula a produção por minuto.
3. **`successRate`**:
    - Multiplica a produção por minuto pela taxa de sucesso.
4. **`int(...)`**:
    - Converte o resultado final para um número inteiro.

### Solução 3:

```go
func CalculateCost(carsCount int) uint {
    return uint((carsCount/10)*95000 + (carsCount%10)*10000)
}
```

### Explicação:

1. **Divisão e Módulo**:
    - `carsCount / 10` calcula o número de grupos de 10 carros.
    - `carsCount % 10` calcula o número de carros restantes que não formam um grupo.
2. **Cálculo do Custo Total**:
    - `(carsCount / 10) * 95000` calcula o custo dos grupos de 10 carros.
    - `(carsCount % 10) * 10000` calcula o custo dos carros restantes.
    - A soma desses valores é o custo total.
3. **Conversão para `uint`**:
    - O resultado final é convertido para `uint` diretamente no retorno da função.