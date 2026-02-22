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
