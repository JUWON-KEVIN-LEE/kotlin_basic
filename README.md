# kotlin_basic

```kotlin
/*
        Class Name :(extends) Parent Object Constructor <<< Constructor 를 상속받는다 */
class MainActivity : AppCompatActivity() {
```

```kotlin
    // JavaScript 와 다르게 Type 호환성이 없다
    // final
    val PI = 3.14
    // should not null
    var a = ""
    // nullable type
    var b : String? = null;
```

```kotlin
    // 늦은 초기화 >>> null 을 사용해서 초기화 불필요
    // getter / setter 를 사용할 수 없고, 초기화 전에 사용하면 오류
    lateinit var l : String

    // kotlin String , Char 두 개의 문자 타입을 지원함
    var s : String = "string"
    var c : Char = 'c'
```

``` kotlin
    override fun onCreate(savedInstanceState: Bundle?) { // parameter : type 순서
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // array
        var array = intArrayOf(1,2,3,4,5)
        var arrayString = arrayOf<String>(/* resource */)

        var array_100 = Array(
                100, {i -> i}
        )

        var arrayString_100 = Array<String> (
                100, {i -> (i*i).toString()}
        )

        // Immutable Collection
        var list = List<String>(10, {i -> i.toString()})
        // list.set() <<< 없음

        // Mutable Collection
        var mutableArray = MutableList(
                100, {i -> (i*i).toString()}
        )
        mutableArray.set(1, "modified")

        Log.d("JUWONLEE", mutableArray.get(0) +" / "+ mutableArray.get(1) +" / "+ mutableArray.get(2));
    }
```

```kotlin
    // function
    fun basicFunction() {
        fun innerFunction() {

        }
        // call
        innerFunction()
    }

    fun nonReturnfunction(a : String, b : Int) {
        /* parameter always final
        c = a;
        c = "modified string"
         */
    }

    fun returnFunction() : Int { // function 도 마찬가지로 함수 : return type, 없을 경우 비워놓기
        return 1
    }
}
```

``` kotlin
class KotlinOne {
    constructor(param : String) {
        println("$param")
    }

    constructor(param1 : Int, param2 : String) {
        println("param 1 : $param1")
        println("param 2 : ${param2 + 200}")
    }
}

// open : 상속 가능 Class
// kotlin 은 class 가 기본적으로 final 선언되어있다. >>> open 해줘야한다.
open class Parent constructor(param : String) {
    fun one() {

    }

    open fun two() {

    }
}

class Child constructor(param : String) : Parent(param) {
    // open 된 것만 override 가능
    override fun two() {
    }
}

class AnotherChild : Parent {
    // 생성자가 여러 개면 동일한 갯수의 생성자를 만들어줘야 한다.
    constructor(param : String) : super(param) {

    }

    constructor() : super("") {

    }
}

abstract class AbstractChild : Parent {
    constructor(param : String) : super(param) {

    }
}
```

```kotlin
// 인터페이스
interface Interface {
    var variable : String
    fun get() : String
    fun set(param : String)
}

class InterfaceChild : Interface {
    override var variable: String = ""
    override fun get(): String {
        return variable
    }
    override fun set(param: String) {
        variable = param
    }
}

// private / protected / public / internal - 같은 모듈에 있는 파일만 접근할 수 있다

// Extension - 이미 컴파일된 Class 에 function 을 추가할 수 있다
fun String.funny():String {
    return "("+this+")"
}

var funnyThing = "smile"
fun test() {
    funnyThing.funny() // == (smile)
    var user = User("JUWON LEE",25,"010-4249-3646") // user 의 값들이 출력

    var anotherUser = AnotherUser("JUWON LEE",25,"010-4249-3646") // <<< memory address 가 출력
}

data class User( private var name : String, var age : Int, var tel : String)
class AnotherUser( private var name : String, var age : Int, var tel : String)

fun nullableTest(param : String?) { // <<< param nullable
    var nullable : String? // nullable
    var nonNull : String
    // nonNull = null <<< error
}

fun elvisExpression(param : String?) {
    var length : Int
    length = param?.length?:0
}
```
