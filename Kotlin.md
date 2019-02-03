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
