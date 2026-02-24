Source: [RocketSeat](https://www.rocketseat.com.br/blog/artigos/post/java-por-dentro-de-abstracao-em-poo)
Áreas: #area/poo
Subject: Abstração, POO, definição especifica de abstração 
Type: #type/abstraction
Related: encapsulamento, herança, composição e polimorfismo

Na abstração devemos isolar as propriedades e comportamentos essenciais de um objeto.
 - **Como a abstração é aplicada ?** 
	 Deve-se focar no que o objeto faz e não como ele faz, dito isso, ao criar um novo objeto ele deve cumprir somente a função necessária para o funcionamento do sistema criado.
	 
- **Abstração em Java: *Interfaces* e *Classes abstratas***
	Em JAVA temos duas formas principais de aplicar abstração, sendo elas: interfaces e classes abstratas. Saber a diferença e quando usar cada uma facilita o entendimento geral de POO e também responde questões como quando usar cada uma e se usar elas e a melhor opção. 
	
	Usando [[Interfaces]] estabelecemos contratos onde as classes que possuem **`extends interface`** devem seguir, independente  da regra de negocio por trás. Por exemplo, Imagine-se como o dono de uma obra que não precisa saber como o eletricista fez a fiação. Você só precisa garantir que ele faça uma coisa:
	**`instalarLuz()`**. Em POO, a interface define o que uma classe deve fazer, mas não **como** ela faz.
	
	Já quando usamos [[Classes Abstratas]] estamos criando uma classe "incompleta" ou um rascunho para outras classes. Essas classes não podem ser instanciadas, ou seja, usar o **`new`** para criar um objeto. Classes Abstratas devem ser necessariamente herdada por uma classe comum. Diferente da Interface uma classe abstrata permite o compartilhamento de **estado** (Variáveis) e **comportamentos reais** (Métodos prontos), fazendo classes comuns implementar somente seus métodos e atributos exclusivos.
	
- **Diferenciando:** ***Interfaces e Classes abstratas***
	Use uma [[Classes Abstratas]] quando você tem objetos que compartilham um "DNA" em comum (mesmos atributos e regras de negócio base), mas a ideia genérica desse objeto não deve existir por si só. Permite ter atributos (**`private`**, **`protected`**), construtores para inicializar esses atributos e métodos já prontos (concretos). Uma classe só pode herdar de **uma** classe abstrata. 
	No sistema de RH de uma empresa, existem **`Gerentes`** e **`Programadores`**. Ambos são **`Funcionarios`**. Não existe a contratação de um "Funcionário Genérico", você contrata um cargo específico. No entanto, todos têm nome, salário base e a mesma regra para bater ponto. Apenas o cálculo do bônus muda.
	
	Use uma [[Interfaces]] quando você precisa que objetos **totalmente diferentes** (sem nenhum parentesco) garantam que sabem executar uma mesma ação. Não possui estado (variáveis de instância não são permitidas, apenas constantes). Não tem construtor. Serve apenas para ditar regras. Uma classe pode assinar (implementar) **múltiplas** interfaces.
	Imagine um sistema de e-commerce. Você tem a classe **`Fatura`** e a classe **`Produto`**. Elas não têm absolutamente nada a ver uma com a outra (não compartilham o mesmo DNA). Porém, o usuário precisa poder exportar ambas para PDF. Como conectá-las? Criando um contrato (Interface) chamado **`Exportavel`**.

| Situação | Escolha Ideal | Motivo |
| :--- | :--- | :--- |
| Criar uma base comum para herdeiros íntimos (ex: Animal -> Cachorro). | **Classe Abstrata** | Você precisa compartilhar atributos (idade, peso) e métodos genéricos. |
| Forçar um comportamento em classes distantes (ex: Autenticavel em Usuario e Servidor). | **Interface** | Eles não têm relação familiar, só precisam da mesma habilidade. |
| Preciso de variáveis privadas e construtores. | **Classe Abstrata** | Interfaces não suportam estado ou construção de objetos. |
| A classe já herda de outra, mas precisa de uma nova habilidade. | **Interface** | O Java permite múltiplas interfaces, mas apenas uma herança de classe. |
-  **A Abstração vai além das palavras-chave**
	Muitas vezes, associamos abstração apenas à criação de **`interfaces`** ou **`abstract classes`**. No entanto, a abstração é o conceito fundamental de **gerenciar e esconder a complexidade**, e ela está presente em quase tudo no Java:
	1. **Métodos:** Quando usamos **`Math.sqrt(25)`** ou **`lista.add("Item")`**, estamos consumindo uma abstração. Focamos no "o que" o método faz (adiciona um item, calcula a raiz), ignorando a complexidade do algoritmo interno.
	2. **Classes Nativas (Estruturas de Dados):** O uso da classe **`String`** abstrai o gerenciamento complexo de memória e *arrays* de *bytes* que ocorre nos bastidores do computador.
	3. **Encapsulamento:** Ao usar modificadores de acesso (**`private`**) e expor apenas métodos públicos (**`public`**), criamos uma barreira de abstração, escondendo como os dados são armazenados internamente e mostrando apenas como interagir com eles.
	4. **APIs e Bibliotecas:** O comando **`System.out.println()`** abstrae toda a comunicação complexa entre a máquina virtual Java, o sistema operacional e o hardware do seu monitor.