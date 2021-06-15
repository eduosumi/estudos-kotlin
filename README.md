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
data class(
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

```

- funcoes de extencao:
```

```

- operador elvis:
```

```

- coroutines:
```

```

- Nao é necessario explicitar qual o tipo do atributo:
```
val descricao = "descricao do tipo String"
```

- funcoes sem um conjunto de operacoes nao precisam dos parenteses:
```
fun obtemDescrFeijao(feijao: Comida) = feijao.descricao
```

- metodo whe():
```

```