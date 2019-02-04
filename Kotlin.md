**Advantages of Kotlin**
 - **Compatibility**: Kotlin is fully compatible with JDK 6, ensuring that
   Kotlin applications can run on older Android devices with no issues.
   The Kotlin tooling is fully supported in Android Studio and
   compatible with the Android build system.
 - **Performance**: A Kotlin application runs as fast as an equivalent Java
   one, thanks to very similar bytecode structure. With Kotlin's support
   for inline functions, code using lambdas often runs even faster than
   the same code written in Java.   
 - **Interoperability**: Kotlin is 100% interoperable with Java, allowing to
   use all existing Android libraries in a Kotlin application. This
   includes annotation processing, so databinding and Dagger work too.   
 - **Footprint**: Kotlin has a very compact runtime library, which can be
   further reduced through the use of ProGuard. In a real application,
   the Kotlin runtime adds only a few hundred methods and less than 100K
   to the size of the .apk file.   
 - **Compilation Time**: Kotlin supports efficient incremental compilation, so while there's some additional overhead for clean
   builds, incremental builds are usually as fast or faster than with
   Java.   
 - **Learning Curve**: For a Java developer, getting started with Kotlin is
   very easy. The automated Java to Kotlin converter included in the
   Kotlin plugin helps with the first steps. Kotlin Koans offer a guide
   through the key features of the language with a series of interactive
   exercises.
   
**Defining functions**
 - Function having two Int parameters with Int return type:

		fun sum(a: Int, b: Int): Int {
    			return a + b
		}

> sum of 3 and 5 is 8

 - Function with an expression body and inferred return type:

		fun sum(a: Int, b: Int) = a + b

> sum of 19 and 23 is 42

 - Function returning no meaningful value:

		fun printSum(a: Int, b: Int): Unit {
    			println("sum of $a and $b is ${a + b}")
		}

> sum of -1 and 8 is 7
 - Unit return type can be omitted:

		fun printSum(a: Int, b: Int) {
   			 println("sum of $a and $b is ${a + b}")
		}
		

> sum of -1 and 8 is 7

**Defining variables**
 - Read-only local variables are defined using the keyword `val`. They
   can be assigned a value only once.

>     val a: Int = 1  // immediate assignment
>     val b = 2   // `Int` type is inferred
>     val c: Int  // Type required when no initializer is provided
>     c = 3       // deferred assignment
 - Variables that can be reassigned use the  `var`  keyword: 
>       var x = 5 // `Int` type is inferred
>       x += 1
 - Top-level variables:
>     val PI = 3.14
>     var x = 0
>     fun incrementX() { 
>         x += 1 
>     }

**Using string templates**

    var a = 1
    // simple name in template:
    val s1 = "a is $a" 
    a = 2
    // arbitrary expression in template:
    val s2 = "${s1.replace("is", "was")}, but now is $a"
**Using conditional expressions**

    fun maxOf(a: Int, b: Int): Int {
        if (a > b) {
            return a
        } else {
            return b
        }
    }

Using _if_ as an expression:

	fun maxOf(a: Int, b: Int) = if (a > b) a else b

**Using nullable values and checking for _null_**

    fun parseInt(str: String): Int? {
	    // ...
    }
    

> Return _null_ if `str` does not hold an integer:
> 
**Using type checks and automatic casts**
The _is_ operator checks if an expression is an instance of a type. If an immutable local variable or property is checked for a specific type, there's no need to cast it explicitly:

    fun getStringLength(obj: Any): Int? {
        if (obj is String) {
            // `obj` is automatically cast to `String` in this branch
            return obj.length
        }
    
        // `obj` is still of type `Any` outside of the type-checked branch
        return null
    }
**Using a  `for`  loop**

    val items = listOf("apple", "banana", "kiwifruit")
    for (item in items) {
        println(item)
    }
or

    val items = listOf("apple", "banana", "kiwifruit")
    for (index in items.indices) {
        println("item at $index is ${items[index]}")
    }
**Using a  `while`  loop**

    val items = listOf("apple", "banana", "kiwifruit")
    var index = 0
    while (index < items.size) {
        println("item at $index is ${items[index]}")
        index++
    }
**Using  `when`  expression**

    fun describe(obj: Any): String =
        when (obj) {
            1          -> "One"
            "Hello"    -> "Greeting"
            is Long    -> "Long"
            !is String -> "Not a string"
            else       -> "Unknown"
    }
   **Using ranges**
Check if a number is within a range using _in_ operator:

    val x = 10
    val y = 9
    if (x in 1..y+1) {
    	println("fits in range")
    }
Check if a number is out of range:

    val list = listOf("a", "b", "c")
    if (-1 !in 0..list.lastIndex) {
        println("-1 is out of range")
    }
    if (list.size !in list.indices) {
        println("list size is out of valid list indices range, too")
    }
Iterating over a range:

    for (x in 1..5) {
        print(x)
    }
or over a progression:

    for (x in 1..10 step 2) {
        print(x)
    }
    println()
    for (x in 9 downTo 0 step 3) {
        print(x)
    }
**Using collections**
Iterating over a collection:

    for (item in items) {
        println(item)
    }

Checking if a collection contains an object using _in_ operator:

    when {
        "orange" in items -> println("juicy")
        "apple" in items -> println("apple is fine too")
    }
Using lambda expressions to filter and map collections:

    val fruits = listOf("banana", "avocado", "apple", "kiwifruit")
    fruits
      .filter { it.startsWith("a") }
      .sortedBy { it }
      .map { it.toUpperCase() }
      .forEach { println(it) }
      
**Idioms**
A collection of random and frequently used idioms in Kotlin.
Creating DTOs (POJOs/POCOs)

    data class Customer(val name: String, val email: String)
Default values for function parameters

    fun foo(a: Int = 0, b: String = "") { ... }
Filtering a list

    val positives = list.filter { x -> x > 0 }
Instance Checks

    when (x) {
        is Foo -> ...
        is Bar -> ...
        else   -> ...
    }
Traversing a map/list of pairs

    for ((k, v) in map) {
        println("$k -> $v")
    }
Using ranges

    for (i in 1..100) { ... }  // closed range: includes 100
    for (i in 1 until 100) { ... } // half-open range: does not include 100
    for (x in 2..10 step 2) { ... } // x is 2 4 6 8 10
    for (x in 10 downTo 1) { ... } // x is 10 9 8 7 6 5 4 3 2 1
    if (x in 1..10) { ... } // x is 1 2 3 4 5 6 7 8 9 10
Read-only list

    val list = listOf("a", "b", "c")
Read-only map

    val map = mapOf("a" to 1, "b" to 2, "c" to 3)
Accessing a map

    println(map["key"])
    map["key"] = value
Lazy property

    val p: String by lazy {
        // compute the string
    }
Extension Functions

    fun String.spaceToCamelCase() { ... }    
    "Convert this to camelcase".spaceToCamelCase()    
Creating a singleton

    object Resource {
        val name = "Name"
    }
If not null shorthand

    val files = File("Test").listFiles()
    println(files?.size)
If not null and else shorthand

    val files = File("Test").listFiles()
    println(files?.size ?: "empty")
Executing a statement if null

    val values = ...
    val email = values["email"] ?: throw IllegalStateException("Email is missing!")
Get first item of a possibly empty collection

    val emails = ... // might be empty
    val mainEmail = emails.firstOrNull() ?: ""
Execute if not null

    val value = ...
    value?.let {
        ... // execute this block if not null
    }
Map nullable value if not null

    val value = ...
    val mapped = value?.let { transformValue(it) } ?: defaultValueIfValueIsNull
Return on when statement

    fun transform(color: String): Int {
        return when (color) {
            "Red" -> 0
            "Green" -> 1
            "Blue" -> 2
            else -> throw IllegalArgumentException("Invalid color param value")
        }
    }
'try/catch' expression

    fun test() {
        val result = try {
            count()
        } catch (e: ArithmeticException) {
            throw IllegalStateException(e)
        }
        // Working with result
    }
'if' expression

    fun foo(param: Int) {
        val result = if (param == 1) {
            "one"
        } else if (param == 2) {
            "two"
        } else {
            "three"
        }
    }
Builder-style usage of methods that return Unit

    fun arrayOfMinusOnes(size: Int): IntArray {
        return IntArray(size).apply { fill(-1) }
    }
Single-expression functions

    fun theAnswer() = 42
This is equivalent to

    fun theAnswer(): Int {
        return 42
    }
This can be effectively combined with other idioms, leading to shorter code. E.g. with the _when_-expression:

    fun transform(color: String): Int = when (color) {
        "Red" -> 0
        "Green" -> 1
        "Blue" -> 2
        else -> throw IllegalArgumentException("Invalid color param value")
    }
Calling multiple methods on an object instance ('with')

    class Turtle {
        fun penDown()
        fun penUp()
        fun turn(degrees: Double)
        fun forward(pixels: Double)
    }
    
    val myTurtle = Turtle()
    with(myTurtle) { //draw a 100 pix square
        penDown()
        for(i in 1..4) {
            forward(100.0)
            turn(90.0)
        }
        penUp()
    }
Java 7's try with resources

    val stream = Files.newInputStream(Paths.get("/some/file.txt"))
    stream.buffered().reader().use { reader ->
        println(reader.readText())
    }
Convenient form for a generic function that requires the generic type information

    //  public final class Gson {
    //     ...
    //     public <T> T fromJson(JsonElement json, Class<T> classOfT) throws JsonSyntaxException {
    //     ...
    
    inline fun <reified T: Any> Gson.fromJson(json: JsonElement): T = this.fromJson(json, T::class.java)
Consuming a nullable Boolean

    val b: Boolean? = ...
    if (b == true) {
        ...
    } else {
        // `b` is false or null
    }


**What’s the Target Platform of Kotlin? How is Kotlin-Java interoperability possible?**
Java Virtual Machine(JVM) is the Target Platform of Kotlin. Kotlin is 100% interoperable with Java since both, on compilation produce byte code. Hence Kotlin code can be called from Java and vice-versa.

**What’s a const? How does it differ from a val?**
By default val properties are set at runtime. Adding a const modifier on a val would make a compile-time constant. A const cannot be used with a var or on its own. A const is not applicable on a local variable.

**Is Kotlin asynchronous or synchronous?**
Kotlin is synchronous because it's execution is line by line.

**What’s the entry point of every Kotlin Program?**
The main function is the entry point of every Kotlin program. In Kotlin we can choose not to write the main function inside the class. On compiling the JVM implicitly encapsulates it in a class. The strings passed in the form of Array<String> are used to retrieve the command line arguments.

**How is !!different from ?. in unwrapping the nullable values? Is there any other way to unwrap nullable values safely?**
!! is used to force unwrap the nullable type to get the value. If the value returned is a null, it would lead to a runtime crash. Hence a !! operator should be only used when you’re absolutely sure that the value won’t be null at all. Otherwise, you’ll get the dreaded null pointer exception. On the other hand, a ?. is an Elvis Operator that does a safe call.

**List down the visibility modifiers available in Kotlin.**
 - private - means visible inside this class only (including all its

   members)
 - protected - same as private + visible in subclasses too
 - internal - any client inside this module who sees the declaring class
   sees its internal members
 - public - any client who sees the declaring class sees its public
   members

**What’s the default visibility modifier?**
public is the default    visibility modifier.
