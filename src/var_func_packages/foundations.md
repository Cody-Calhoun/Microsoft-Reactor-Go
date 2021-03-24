Microsoft: Understand how to use variables, functions, and packages.



Variables

Rules for Variable Declaration:

    1.) Var can be comprised of ONLY letters, numbers, and underscores. 
    2.) May not start wiht a number.
    3.) May not contain any special characters or spaces.
    4.) If you declare a variable BUT don't use it, it will generate an error.


Declaring vs Initializing

DECLARATION
    
    1.) var firstName string

    2.) var firstName, lastName string <---- declaring 2 variables of same type

    3.) var firstName, lastName string <---- declaring 3 variables, two of same type
        var age int

    4.) var (
            firstName, lastName string
            age int
        )

INITIALIZING

        var (
            firstName string = "John"
            lastName  string = "Doe"
            age       int    = 32
        )

<!-- If initializing, you don't need to specifiy the type as Go will infer for you -->
        var (
            firstName = "John"
            lastName  = "Doe"
            age       = 32
        )

        Short declaration: Expression Assignment Operator(Walrus Operator)
        func main() {
            firstName, lastName := "John", "Doe"
            age := 32
            println(firstName, lastName, age)
        }
<!-- IMPORTANT: Short declaration MUST be inside of a function and you MUST declare AND initialize in order to use this. Lastly, IF you put a type, your comiler will generate an error -->


CONSTANTS

    const HTTPStatusOK = 200 <----- single declaration

    const (                     
        StatusOK              = 0
        StatusConnectionReset = 1       <----- multiple declaration 
        StatusOtherError      = 2
    )

<!-- Constant names are typically written in MixedCased or all uppercase letters. -->

  DATE TYPES:

  <!-- Go is a strongly typed language. This means that every variable you declare is bound to a specific data type and will accept only values that match this type. -->

In Go, you have four categories of data types:

    Basic types: numbers, strings, and booleans <--- What we will be covering TODAY
    Aggregate types: arrays and structs <--- NEXT WEEK
    Reference types: pointers, slices, maps, functions, and channels <--- NEXT WEEK
    Interface types: interface


    Integers

        Unsigned & Signed Integers
        uint8 / int8
        uint16/int16
        uint32/int32(rune)
        uint64/int64

<!-- Walk through rune quickly -->

        3 Machine Dependant Types
        uint(32 or 64)
        int(32 or 64)
        uintptr(an unsigned integer to store the uninterpreted bits of a pointer value)

    Floating Point Numbers

        float32
        float64

    Boolean

        var featureFlag bool = true

    Strings

        var firstName string = "John"
        lastName := "Doe"
        println(firstName, lastName)

TYPE CONVERSIONS

    var integer16 int16 = 127
    var integer32 int32 = 32767
    println(int32(integer16) + integer32)


FUNCTIONS

    main()
    
    Entry point for our program
    <!-- If you are creating a package, you DON'T need a main() -->

    Exploring the main()
        <!-- As you might have noticed, the main() function doesn't have any parameters and returns nothing. But that doesn't mean it can't read values from the user, like command-line arguments. -->

        <!-- os package -->

            package main

            import (
                "os"
                "strconv"
            )

            func main() {
                number1, _ := strconv.Atoi(os.Args[1])
                number2, _ := strconv.Atoi(os.Args[2])
                println("Sum:", number1+number2)
            }

Custom Functions

    func name(parameters) (results) {
    body-content
    }

<!-- Refactor above code with Custom Function-->
    package main

    import (
        "os"
        "strconv"
    )

    func main() {
        sum := sum(os.Args[1], os.Args[2])
        println("Sum:", sum)
    }

    func sum(number1 string, number2 string) int {
        int1, _ := strconv.Atoi(number1)
        int2, _ := strconv.Atoi(number2)
        return int1 + int2
    }

Only "Return" at end:
<!-- Not necessarily suggested as it can be confusing as to what you are returning -->
    func sum(number1 string, number2 string) (result int) {
        int1, _ := strconv.Atoi(number1)
        int2, _ := strconv.Atoi(number2)
        result = int1 + int2
        return
    }

Returning multiple values:

    func main() {
        sum, mul := calc(os.Args[1], os.Args[2])
        println("Sum:", sum)
        println("Mul:", mul)
    }

    func calc(number1 string, number2 string) (sum int, mul int) {
        int1, _ := strconv.Atoi(number1)
        int2, _ := strconv.Atoi(number2)
        sum = int1 + int2
        mul = int1 * int2
        return
    }


POINTERS

    package main

    func main() {
        firstName := "John"
        updateName(firstName)
        println(firstName)
    }

    func updateName(name string) {
        name = "David"
    }

In Go, there are two operators for working with pointers:

    The & operator takes the address of the object that follows it.

    The * operator dereferences a pointer. That is, it gives you access to the object at the address contained in the pointer.

<!-- Written with pointers -->

    package main

    func main() {
        firstName := "John"
        updateName(&firstName)
        println(firstName)
    }

    func updateName(name *string) {
        *name = "David"
    }

PACKAGES
    
    Packages in Go are like libraries or modules in other programming languages. 





