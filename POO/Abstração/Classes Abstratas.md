## Componentes de uma Classe Abstrata

### 1. O modificador `abstract`

Você define a classe com a palavra-chave **`abstract`**. Se um método também for **`abstract`**, ele não terá corpo (**`{ }`**) , ou seja, não existirá nada de lógica dentro das chaves. Terminará com um ponto e vírgula.

### 2. Métodos Concretos (Comuns)

Uma classe abstrata pode ter métodos normais que já possuem lógica. Todas as classes filhas herdarão essa lógica automaticamente.

### 3. Métodos Abstratos

São métodos sem implementação. Eles dizem à classe filha: "Eu não sei como fazer isso, você se vira para implementar!".

### 4. Atributos e Construtores

Diferente das interfaces, classes abstratas podem ter campos **`private`**, **`protected`**, etc., e podem ter construtores (que são chamados via `super()` pelas filhas).
- **`private`**: Você pode ter um atributo que só a classe abstrata consegue manipular. As filhas nem sabem que ele existe, mas usam os métodos públicos da classe pai que interagem com esse dado.
- **`protected`**: Este é o modificador favorito da herança. Ele permite que as **classes filhas** acessem o atributo diretamente, mas proíbe que qualquer outra classe de fora (que não seja do mesmo pacote) mexa nele.

```
abstract class Personagem {
    private String nome; // Ninguém fora desta classe muda o nome diretamente
    protected int vida;  // As classes filhas podem alterar a vida (ex: levar dano)

    // CONSTRUTOR DA CLASSE ABSTRATA
    public Personagem(String nome, int vida) {
        this.nome = nome;
        this.vida = vida;
        System.out.println("Base do personagem '" + nome + "' inicializada.");
    }

    public String getNome() { return nome; }
}

class Guerreiro extends Personagem {
    private int forca;

    public Guerreiro(String nome, int vida, int forca) {
        // OBRIGATÓRIO: Chamar o construtor do pai primeiro
        super(nome, vida); 
        this.forca = forca;
        System.out.println("Especialização 'Guerreiro' finalizada.");
    }
}
```

### 5. Exemplo Prático: 

Pense em um banco. Existe uma "Conta", mas você nunca abre uma "Conta" genérica. Você abre uma "Conta Corrente" ou uma "Conta Poupança". Ambas são contas, mas o cálculo de rendimento ou taxas é diferente.
```
// Passo 1: Definir a Classe Abstrata
abstract class Conta {
    protected double saldo;
    private String titular;

    public Conta(String titular) {
        this.titular = titular;
    }

    // Método CONCRETO: Todo tipo de conta deposita do mesmo jeito
    public void depositar(double valor) {
        this.saldo += valor;
        System.out.println(titular + " depositou: R$ " + valor);
    }

    // Método ABSTRATO: Cada conta tem sua regra de saque (taxas diferentes)
    public abstract void sacar(double valor);
    
    public void exibirSaldo() {
        System.out.println("Saldo de " + titular + ": R$ " + saldo);
    }
}
```

```
//Passo 2: Criar as Subclasses (Classes Concretas)
class ContaCorrente extends Conta {
    public ContaCorrente(String titular) {
        super(titular);
    }

    @Override
    public void sacar(double valor) {
        // Conta corrente cobra R$ 2,00 por saque
        double taxa = 2.00;
        if (saldo >= (valor + taxa)) {
            saldo -= (valor + taxa);
            System.out.println("Saque realizado com taxa de R$ 2,00.");
        }
    }
}

class ContaPoupanca extends Conta {
    public ContaPoupanca(String titular) {
        super(titular);
    }

    @Override
    public void sacar(double valor) {
        // Poupança não cobra taxa
        if (saldo >= valor) {
            saldo -= valor;
            System.out.println("Saque realizado sem taxas.");
        }
    }
}
```