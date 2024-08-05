### **Robô de Festa**

**Instruções**

Havia um programador excêntrico que morava em uma casa estranha com janelas gradeadas. Um dia, ele aceitou um trabalho de um quadro de empregos online para construir um robô de festa. O robô deve cumprimentar as pessoas e ajudá-las a encontrar seus lugares. A primeira edição foi muito técnica e mostrou a falta de interação humana do programador. Algumas dessas características também foram incluídas na edição seguinte.

- **Tarefa 1: Dar boas-vindas a um novo convidado da festa**
    
    Implemente a função `Welcome` para retornar uma mensagem de boas-vindas usando o nome fornecido:
    
    ```go
    Welcome("Christiane")
    // => Welcome to my party, Christiane!
    ```
    
- **Tarefa 2: Dar boas-vindas a um novo convidado cuja festa é hoje**
    
    Implemente a função `HappyBirthday` para retornar uma mensagem de aniversário usando o nome e a idade da pessoa. Infelizmente, o programador é um pouco exibicionista, então o robô deve demonstrar seu conhecimento sobre o aniversário de cada convidado.
    
    ```go
    HappyBirthday("Frank", 58)
    // => Happy birthday Frank! You are now 58 years old!
    ```
    
- **Tarefa 3: Dar direções**
    
    Implemente a função `AssignTable` para dar direções. Ela deve aceitar 5 parâmetros:
    
    - O nome do novo convidado a ser cumprimentado (`string`)
    - O número da mesa (`int`)
    - O nome do acompanhante de mesa (`string`)
    - A direção onde encontrar a mesa (`string`)
    - A distância até a mesa (`float64`)
    
    O formato exato do resultado pode ser visto no exemplo abaixo.
    
    O robô fornece o número da mesa em formato de 3 dígitos. Se o número tiver menos de 3 dígitos, ele recebe zeros à esquerda para completar 3 dígitos (por exemplo, 3 se torna 003). O robô também menciona a distância da mesa. Felizmente, apenas com uma precisão limitada a 1 dígito.
    
    ```go
    AssignTable("Christiane", 27, "Frank", "on the left", 23.7834298)
    // => Welcome to my party, Christiane! You have been assigned to table 027. Your table is on the left, exactly 23.8 meters from here. You will be sitting next to Frank.
    ```
    

```go
package partyrobot

// Welcome cumprimenta uma pessoa pelo nome.
func Welcome(name string) string {
    panic("Por favor, implemente a função Welcome")
}

// HappyBirthday deseja feliz aniversário à pessoa e exalta sua idade.
func HappyBirthday(name string, age int) string {
    panic("Por favor, implemente a função HappyBirthday")
}

// AssignTable atribui uma mesa a cada convidado.
func AssignTable(name string, table int, neighbor, direction string, distance float64) string {
    panic("Por favor, implemente a função AssignTable")
}

```

---

### Solução 1:

- **Dar boas-vindas a um novo convidado da festa**
    
    Implemente a função `Welcome` para retornar uma mensagem de boas-vindas usando o nome fornecido:
    
    ```go
    Welcome("Christiane")
    // => Welcome to my party, Christiane!
    ```
    
    **Código:**
    
    Primeiro, importamos o pacote `fmt`:
    
    ```go
    import "fmt"
    ```
    
    Em seguida, definimos a função `Welcome`:
    
    ```go
    // Welcome greets a person by name.
    func Welcome(name string) string {
        return fmt.Sprintf("Welcome to my party, %s!", name)
    }
    ```
    

### Solução 2:

- **Dar boas-vindas a um novo convidado cuja festa é hoje**
    
    Implemente a função `HappyBirthday` para retornar uma mensagem de aniversário usando o nome e a idade da pessoa. Infelizmente, o programador é um pouco exibicionista, então o robô deve demonstrar seu conhecimento sobre o aniversário de cada convidado.
    
    ```go
    HappyBirthday("Frank", 58)
    // => Happy birthday Frank! You are now 58 years old!
    ```
    
    **Código:**
    
    ```go
    import "fmt"
    
    // HappyBirthday deseja feliz aniversário à pessoa e exibe a idade dela.
    func HappyBirthday(name string, age int) string {
        return fmt.Sprintf("Happy birthday %s! You are now %d years old!", name, age)
    }
    ```
    

### Solução 3:

- **Dar direções**
    
    Implemente a função `AssignTable` para dar direções. Ela deve aceitar 5 parâmetros:
    
    - O nome do novo convidado a ser cumprimentado (`string`)
    - O número da mesa (`int`)
    - O nome do acompanhante de mesa (`string`)
    - A direção onde encontrar a mesa (`string`)
    - A distância até a mesa (`float64`)
    
    O formato exato do resultado pode ser visto no exemplo abaixo.
    
    O robô fornece o número da mesa em formato de 3 dígitos. Se o número tiver menos de 3 dígitos, ele recebe zeros à esquerda para completar 3 dígitos (por exemplo, 3 se torna 003). O robô também menciona a distância da mesa com uma precisão limitada a 1 dígito.
    
    ```go
    AssignTable("Christiane", 27, "Frank", "on the left", 23.7834298)
    // => Welcome to my party, Christiane! You have been assigned to table 027. Your table is on the left, exactly 23.8 meters from here. You will be sitting next to Frank.
    ```
    
    **Código:**
    
    ```go
    import "fmt"
    
    // AssignTable assigns a table to each guest.
    func AssignTable(name string, table int, neighbor, direction string, distance float64) string {
    	return fmt.Sprintf(
            "Welcome to my party, %s!\nYou have been assigned to table %03d. Your table is %s, exactly %.1f meters from here.\nYou will be sitting next to %s.",
            name, table, direction, distance, neighbor,
        ) 
    }
    ```