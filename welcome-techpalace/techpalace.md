### **Welcome To Tech Palace!**

### Instruções

Uma loja de eletrodomésticos chamada "Tech Palace" recentemente instalou uma grande tela para usar em mensagens de marketing e para mostrar uma saudação especial quando os clientes escaneiam seus cartões de fidelidade na entrada. A tela consiste em muitas pequenas luzes LED e pode exibir várias linhas de texto.

O proprietário da loja precisa de ajuda com o código usado para gerar o texto para a nova tela.

### 1. Mensagem de Boas-Vindas

Para a maioria dos clientes que escaneiam seus cartões de fidelidade, o proprietário deseja ver "Welcome to the Tech Palace", seguido pelo nome do cliente em letras maiúsculas na tela.

Implemente a função `WelcomeMessage` que aceita o nome do cliente como um argumento de string e retorna a mensagem desejada como uma string.

```go
WelcomeMessage("Judy")
// => Welcome to the Tech Palace, JUDY
```

### 2. Adicionar Borda

Para clientes leais que compram muito na loja, o proprietário deseja que a exibição de boas-vindas seja mais elegante, adicionando uma linha de estrelas antes e depois da mensagem de boas-vindas. Eles ainda não decidiram quantas estrelas devem estar nas linhas, então querem que isso seja configurável.

Escreva uma função `AddBorder` que aceita uma mensagem de boas-vindas (uma string) e o número de estrelas por linha (tipo `int`) como argumentos. Deve retornar uma string que consiste em 3 linhas: uma linha com o número desejado de estrelas, depois a mensagem de boas-vindas como foi passada e, em seguida, outra linha de estrelas.

```go
AddBorder("Welcome!", 10)
```

Deve retornar o seguinte:

```go
**********
Welcome!
**********
```

### 3. Limpar Mensagem

Antes de instalar essa nova exibição, a loja tinha uma exibição semelhante que só podia mostrar linhas estáticas não configuráveis. O proprietário gostaria de reutilizar algumas das mensagens de marketing antigas na nova exibição. No entanto, os dados já incluem uma borda de estrelas e alguns espaços em branco indesejados. Sua tarefa é limpar as mensagens para que possam ser reutilizadas.

Implemente uma função `CleanupMessage` que aceita a mensagem de marketing antiga como uma string. A função deve primeiro remover todas as estrelas do texto e depois remover os espaços em branco à esquerda e à direita do texto restante. A função deve então retornar a mensagem limpa.

```go
message := `
**************************
*    BUY NOW, SAVE 10%   *
**************************
`

CleanupMessage(message)
// => BUY NOW, SAVE 10%
```

### Código Inicial

```go
package techpalace

// WelcomeMessage returns a welcome message for the customer.
func WelcomeMessage(customer string) string {
	panic("Please implement the WelcomeMessage() function")
}

// AddBorder adds a border to a welcome message.
func AddBorder(welcomeMsg string, numStarsPerLine int) string {
	panic("Please implement the AddBorder() function")
}

// CleanupMessage cleans up an old marketing message.
func CleanupMessage(oldMsg string) string {
	panic("Please implement the CleanupMessage() function")
}
```

### **Solução 1:**

**Primeiro devemos importar o pacote “strings”:**

```go
import "strings"
```

**Mensagem de Boas-Vindas**

Para a maioria dos clientes que escaneiam seus cartões de fidelidade, o proprietário deseja ver "Welcome to the Tech Palace", seguido pelo nome do cliente em letras maiúsculas na tela.

Implemente a função `WelcomeMessage` que aceita o nome do cliente como um argumento de string e retorna a mensagem desejada como uma string.

```go
func WelcomeMessage(customer string) string {
    return "Welcome to the Tech Palace, " + strings.ToUpper(customer)
}
```

### Solução 2:

**Adicionar Borda**

Para clientes leais que compram muito na loja, o proprietário deseja que a exibição de boas-vindas seja mais elegante, adicionando uma linha de estrelas antes e depois da mensagem de boas-vindas. Eles ainda não decidiram quantas estrelas devem estar nas linhas, então querem que isso seja configurável.

Escreva uma função `AddBorder` que aceita uma mensagem de boas-vindas (uma string) e o número de estrelas por linha (tipo `int`) como argumentos. Deve retornar uma string que consiste em 3 linhas: uma linha com o número desejado de estrelas, depois a mensagem de boas-vindas como foi passada e, em seguida, outra linha de estrelas.

```go
func AddBorder(welcomeMsg string, numStarsPerLine int) string {
    return strings.Repeat("*", numStarsPerLine) + "\n" + welcomeMsg + "\n" + strings.Repeat("*", numStarsPerLine)
}
```

### Solução 3:

**Limpar Mensagem**

Antes de instalar essa nova exibição, a loja tinha uma exibição semelhante que só podia mostrar linhas estáticas não configuráveis. O proprietário gostaria de reutilizar algumas das mensagens de marketing antigas na nova exibição. No entanto, os dados já incluem uma borda de estrelas e alguns espaços em branco indesejados. Sua tarefa é limpar as mensagens para que possam ser reutilizadas.

Implemente uma função `CleanupMessage` que aceita a mensagem de marketing antiga como uma string. A função deve primeiro remover todas as estrelas do texto e depois remover os espaços em branco à esquerda e à direita do texto restante. A função deve então retornar a mensagem limpa.

```go
func CleanupMessage(oldMsg string) string {
    return strings.TrimSpace(strings.ReplaceAll(oldMsg, "*", ""))
}
```