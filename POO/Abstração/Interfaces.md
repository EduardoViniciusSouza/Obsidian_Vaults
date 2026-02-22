## Anatomia

Diferente de uma classe, a interface é "vazia" de lógica interna (na maioria das vezes).

### 1. Métodos Abstratos (O padrão)

Por padrão, todo método em uma interface é **`public`** e **`abstract`**. Você define apenas a assinatura (o nome, o que recebe e o que retorna).

### 2. Atributos (Constantes)

Você não pode ter variáveis que mudam de valor. Qualquer atributo declarado é automaticamente **`public static final`** (uma constante).

### 3. Contrato Obrigatório

Se uma classe diz que **`implements`** (implementa) uma interface, ela é **obrigada** a escrever o código de todos os métodos daquela interface, ou o código nem compila.

---
## Exemplo Prático

Imagine que seu sistema precisa enviar avisos para os usuários. Não importa se é por E-mail, SMS ou WhatsApp, todos são "Notificadores".

###  1. Criar a Interface (O Contrato)

```
public interface Notificador {
    // A interface diz: "Quem quiser ser um notificador, PRECISA ter esse método"
    void enviar(String mensagem);
}
```

### 2. Implementar o Contrato

Agora, classes diferentes assinam o contrato e resolvem o "como" fazer.

```
class NotificadorEmail implements Notificador {
    @Override
    public void enviar(String mensagem) {
        System.out.println("Enviando E-mail: " + mensagem);
    }
}

class NotificadorSMS implements Notificador {
    @Override
    public void enviar(String mensagem) {
        System.out.println("Enviando SMS: " + mensagem);
    }
}
```

### 3. Usar a Abstração

O segredo da interface é que você pode tratar objetos diferentes como se fossem o tipo da interface. Atente-se aos comentários.


```
public class SistemaNotificacao {
    public static void main(String[] args) {
        // Criamos uma variável do tipo da INTERFACE
        // Ela pode segurar qualquer classe que implemente Notificador
        Notificador meuAviso = new NotificadorEmail();
        
        meuAviso.enviar("Olá! Seu pedido chegou."); // Saída: Enviando E-mail...

        // Podemos trocar a implementação facilmente
        meuAviso = new NotificadorSMS();
        meuAviso.enviar("Olá! Seu pedido chegou."); // Saída: Enviando SMS...
    }
}
```

---

## Por que interfaces ?

### 1. Múltiplas Implementações

Diferente da Herança (onde você só pode ter um "pai"), uma classe pode implementar **várias** interfaces.

- _Exemplo:_ Uma classe **`Usuario`** pode implementar **`Autenticavel`**, **`Autorizavel`** e **`Imprimivel`**.

### 2. Flexibilidade (Desacoplamento)

Se amanhã você quiser adicionar notificações por **Telegram**, você só cria a classe **`NotificadorTelegram implements Notificador`**. Você **não precisa mudar nada** no seu código que já usa a interface **`Notificador`**.

### 3. Segurança de Contrato

Se você trabalha em equipe, você define a interface primeiro. Seus colegas podem começar a usar a interface no código deles enquanto você ainda está escrevendo a lógica interna da classe. O código deles vai compilar porque o "contrato" (a interface) já existe.

---

## ⚠️ Default Methods

Antigamente, interfaces eram 100% vazias. Desde o Java 8, você pode usar a palavra **`default`** para criar um método com corpo dentro da interface. Isso serve para adicionar funções novas sem quebrar as classes antigas que já usavam a interface.

```
public interface Notificador {
    void enviar(String mensagem);

    // Método opcional: classes não são obrigadas a sobrescrever
    default void logarEnvio() {
        System.out.println("Log: Notificação enviada com sucesso.");
    }
}
```