# Kotlin

## Descricao
- permite misturar os conceitos de orientacao a objetos com funcional;
- Facil de aprender por ser conciso e pouco verboso, principalmente para quem ja conhece o Java(isso nao significa que nao é necessario estudar a documentacao para fazer um bom uso);
- Nao possui o conceito de tipos primitivos do Java como o int, float, double, boolean,... No kotlin eles sao classes.
- Disponivel em varios frameworks: Spring, Micronaut, Quarkus, Vert.x, Spark,...;
- Curiosidades: hoje é considerado a linguagem oficial(pela Google) para desenvolvimento nativo Android e a criacao da linguagem teve fortes influencias do livro Effective Java do <a href="https://pt.wikipedia.org/wiki/Joshua_Bloch">Joshua Bloch</a>. Mas esta sendo muito utilizado no backend, e um dos motivos é por ele tambem fazer uso da JVM.
- Possui um tutorial bem rico. Por exemplo: possui um passo a passo para criar um projeto utilizando Spring
- Possibilidade de testes online: https://kotlinlang.org/

## Algumas features bacanas

1 - Interoperabilidade com o Java:
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
2 - A imutabilidade é mais natural com o uso de val:
```
fun main() {
    val feijao = "Feijao"
    feijao = "Outra comida" //Erro de compilacao

    var comida = "Feijao"
    comida = "Arroz" //é mutavel por conta do "var"
}
```
3 - Null Safety, ou seja, por padrao os atributos nao aceitam nulos evitando assim o famoso NullPointerException:
```
class Comida(
    //nao aceita null
    val nome: String,
    //aceita null
    val descricao: String?
)
```
4.0 - Funcoes sem um conjunto de operacoes nao precisam dos parenteses:
```
fun soma(x: Int, y: Int): Int = x+y
```
4.1 - Funcoes sem um conjunto de operacoes nao precisam ter o tipo de retorno explicito(Inferencia de tipo):
```
fun soma(x: Int, y: Int) = x+y
```
4.2 - Nao é necessario explicitar qual o tipo do atributo(Inferencia de tipo):
```
val descricao1 = "descricao do tipo String"
val descricao2: String = "descricao do tipo String"

val comida1 = Comida("feijao", null)
val comida2: Comida = Comida("feijao", null)
```
6 - A classe com atributos primarios ja cria o construtor, getters e setters:
```
class Comida(
    val nome: String,
    val curiosidade: String
)

fun main() {
    val feijao = Comida("feijao", "combina com arroz")
    println("nome da comida: ${feijao.nome}")
}
```

7 - Funcionalidades padrao criada de forma automatica(equals/hashCode/toString/copy):
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

8 - uma funcao nao precisa estar atrelada a uma classe / um arquivo .kt pode ter varias classes e varias funcoes separadas:
```
Pedido.kt

data class Pedido(
    val id: Long,
    val detalhesPedido: DetalhesPedido
)

data class DetalhesPedido(
    val id: Long,
    val nome: String,
    val qtdProdutos: Short,
    val dataCriacao: LocalDate
)

```
9 - funcoes de extencao - pode ser usada em qualquer classe:
```
fun String.incluirImpressao() = println("segue impressao: $this")

fun main() {
    "impresso ok".incluirImpressao()
}

class Comida(
    val nome: String
)

fun Comida.nomeComposto() = this.nome+" composicao"
```
10.0 - Safe calls:
```
val a = "Kotlin"
val b: String? = null
println(b?.length)
println(a?.length) // Nao é necessario o "?" pois o atributo a concerteza nao é null
```
10.1 - operador !!(double bang):
```
class Comida(val nome: String)

fun main() {
    val c: Comida? = Comida("arroz")
    println(c!!.nome)
}
```
11 - operador elvis: evita condicoes de verificacao de null. Ele é equivalente ao if ternario verificando se nao é nulo
```
val bola: String? = null
val resultado = bola ?: -1
```

12 - metodo when() - parecido com o switch case do Java:
```
when (x) {
    1 -> print("x == 1")
    in 2..5 -> print("x == 2 ou 3 ou 4 ou 5")
    else -> {
        print("x é diferente de 1 a 5")
    }
}

//caso seja uma String verifica se inicia com o prefixo inicio
fun startPrefixC(atr: Any) = when(atr) {
    is String -> atr.startsWith("c")
    else -> false
}
```

13 - Lazy Initialization - atributos/objetos inicializados de forma lento, ou seja, é inicializado somente quando for necessario/utilizado
