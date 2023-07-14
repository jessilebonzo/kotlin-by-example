# Inheritance

open class Dog {                // 1
    open fun sayHello() {       // 2
        println("ruf ruf!")
    }
}

class Aspin : Dog() {       // 3
    override fun sayHello() {   // 4
        println("wof wof!")
    }
}

fun main() {
    val dog: Dog = Aspin()
    dog.sayHello()
}

### Inheritance with Parameterized Constructor

//sampleStart
open class Tiger(val origin: String) {
    fun sayHello() {
        println("A tiger from $origin says: roar!")
    }
}

class MalayanTiger : Tiger("Malayan")                  // 1

fun main() {
    val tiger: Tiger = MalayanTiger()
    tiger.sayHello()
}
//sampleEnd

### Passing Constructor Arguments to Superclass

//sampleStart
open class Lion(val name: String, val origin: String) {
    fun sayHello() {
        println("$name, the lion from $origin says: purrs!")
    }
}

class Asiatic(name: String) : Lion(name = name, origin = "Africa") // 1

fun main() {
    val lion: Lion = Asiatic("Zeus")                              // 2
    lion.sayHello()
}
//sampleEnd


