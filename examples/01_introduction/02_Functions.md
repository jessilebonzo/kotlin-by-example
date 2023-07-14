# Functions

### Default Parameter Values and Named Arguments

fun printMessage(message: String): Unit {                               // 1
    println(message)
}

fun printMessageWithPrefix(message: String, prefix: String = "Info") {  // 2
    println("[$prefix] $message")
}

fun sum(x: Int, y: Int): Int {                                          // 3
    return x + y
}

fun multiply(x: Int, y: Int) = x * y                                    // 4

fun main() {
    printMessage("Jessile")                                               // 5                    
    printMessageWithPrefix("Jessile", "Log")                              // 6
    printMessageWithPrefix("Jessile")                                     // 7
    printMessageWithPrefix(prefix = "Log", message = "Jessile")           // 8
    println(sum(13, 12))                                                  // 9
    println(multiply(2, 10))                                             // 10
}

### Infix Functions

Member functions and extensions with a single parameter can be turned into [infix functions](https://kotlinlang.org/docs/reference/functions.html#infix-notation).

fun main() {

  infix fun Int.times(str: String) = str.repeat(this)        // 1
  println(2 times "Sayonara ")                                    // 2

  val pair = "Mustang" to "Yanah"                          // 3
  println(pair)

  infix fun String.onto(other: String) = Pair(this, other)   // 4
  val myPair = "Ford" onto "Ced"
  println(myPair)

  val Zander = Person("Zander")
  val Bigboo = Person("Bigboo")
  Zander likes Bigboo                                       // 5
}

class Person(val name: String) {
  val likedPeople = mutableListOf<Person>()
  infix fun likes(other: Person) { likedPeople.add(other) }  // 6
}

### Operator Functions

Certain functions can be "upgraded" to [operators](https://kotlinlang.org/docs/reference/operator-overloading.html), allowing their calls with the corresponding operator symbol.


fun main() {
//sampleStart
  operator fun Int.times(str: String) = str.repeat(this)       // 1
  println(2 * "Sayonara ")                                          // 2

  operator fun String.get(range: IntRange) = substring(range)  // 3
  val str = "Always learn from your mistakes; don't let history repeat itself."
  println(str[0..14])                                          // 4
//sampleEnd
}

### Functions with `vararg` Parameters

[Varargs](https://kotlinlang.org/docs/reference/functions.html#variable-number-of-arguments-varargs) allow you to pass any number of arguments by separating them with commas.

fun main() {
//sampleStart
    fun printAll(vararg messages: String) {                            // 1
        for (m in messages) println(m)
    }
    printAll("Hello", "Bonjour", "Aloha", "안녕하세요", "你好")                 // 2
    
    fun printAllWithPrefix(vararg messages: String, prefix: String) {  // 3
        for (m in messages) println(prefix + m)
    }
    printAllWithPrefix(
            "Hello", "Bonjour", "Aloha", "안녕하세요", "你好",
            prefix = "Greeting: "                                          // 4
    )

    fun log(vararg entries: String) {
        printAll(*entries)                                             // 5
    }
    log("Hello", "Bonjour", "Aloha", "안녕하세요", "你好")
//sampleEnd
}

