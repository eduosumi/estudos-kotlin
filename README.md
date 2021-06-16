# Kotlin

##Descricao
- permite misturar os conceitos de orientacao a objetos com funcional;
- Facil de aprender por ser conciso e pouco verboso, e principalmente para quem ja conhece o Java(isso nao significa que nao é necessario estudar a documentacao para fazer um bom uso);
- Disponivel em varios frameworks: Spring, Micronaut, Quarkus, Vert.x, Spark,...;
- Curiosidades: hoje é considerado a linguagem oficial(pela Google) para desenvolvimento nativo Android e a criacao da linguagem teve fortes influencias do livro Effective Java do <a href="https://pt.wikipedia.org/wiki/Joshua_Bloch">Joshua Bloch</a>.

##Algumas features bacanas

- Interoperabilidade com o Java:
```
public class Celular {
    private String marca;
    private String modelo;

    public Celular(String marca, String modelo) {
        this.marca = marca;
        this.modelo = modelo;
    }

    public String getModelo() {
        return modelo;
    }
}

fun main() {
    val samsungS10 = Celular("samsung", "s10")
    print("modelo: ${samsungS10.modelo}")
}
```

- Null Safety, ou seja, por padrao os atributos nao aceitam nulos evitando assim o famoso NullPointerException:
```
class Comida(
    //nao aceita null
    val nome: String,
    //aceita null
    val descricao: String?
)
```
- A imutabilidade é mais natural com o uso de val:
```
fun main() {
    val feijao = "Feijao"
    feijao = "Outra comida" //Erro de compilacao

    var comida = "Feijao"
    comida = "Arroz" //é mutavel por conta do "var"
}
```

- A classe com atributos primarios ja cria o construtor:
```
class Comida(
    val nome: String,
    val descricao: String
)

fun main() {
    val feijao = Comida("feijao", "combina com arroz")
    println("nome da comida: ${feijao.nome}")
}
```

- Funcionalidades padrao criada de forma automatica(equals/hashCode/toString/copy):
```
data class Comida(
    val nome: String,
    val descricao: String
)

fun main() {
    val feijao = Comida("feijao", "combina com arroz")
    println("comida: ${feijao.toString()}")
}
```

- uma funcao nao precisa estar atrelada a uma classe / um arquivo .kt pode ter varias classes e varias funcoes separadas:
```
data class Pedido(
    val id: Long,
    val cliente: Cliente
)

data class Cliente(
    val id: Long,
    val nome: String
)

fun soma(x: Int, y: Int) = x + y
```
- funcoes de extencao:
```
fun String.incluirImpressao() = println("segue impressao: $this")

fun main() {
    "impresso ok".incluirImpressao()
}
```
- Safe calls:
```
val a = "Kotlin"
val b: String? = null
println(b?.length)
println(a?.length) // Nao é necessario o "?" pois o atributo a concerteza nao é null
```
- operador elvis: evita condicoes de verificacao de null
```
val b: String? = null
val l = b?.length ?: -1
```
- Nao é necessario explicitar qual o tipo do atributo:
```
val descricao = "descricao do tipo String"
```
- funcoes sem um conjunto de operacoes nao precisam dos parenteses:
```
fun obtemDescrFeijao(feijao: Comida) = feijao.descricao
```
- metodo when():
```
when (x) {
    1 -> print("x == 1")
    in 2..5 -> print("x == 2 ou 3 ou 4 ou 5 ou 6")
    else -> { // Note the block
        print("x é diferente de 1 a 5")
    }
}

//caso seja uma String verifica se inicia com o prefixo inicio
fun hasPrefix(x: Any) = when(x) {
    is String -> x.startsWith("inicio")
    else -> false
}
```

# Api Rest
Ferramentas utilizadas:
 - Kotlin
 - Spring Boot
 - spring Data
 - Gradle
 - H2