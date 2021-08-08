# 고차함수
```
val multi = {x:Int , y:Iny -> x * y}
var result = multi(10,20)
```
- val multi : (Int, Int) -> Int = { x : Int, y: Int -> x * y }
- [변수처럼]   [ 람다식 자료형 선언 ]  [ 람다식 매개변수 ] [ 람다식 처리 내용 ]
-             [ 매개변수에 자료형 명시된 경우 생략 가능]

- 반환 자료형이 없거나, 매개변수가 하나만 있을경우
- val greet : () -> Unit = { println("Hello") }
- val square : (Int) -> Int = { x -> x * x }


- 람다식을 매개변수에 사용한 고차 함수
```
result = highOrder({ x, y -> x + y }, 10, 20 ) //람다식을 매개변수와 인자로 사용한 함수

fun highOrder(sum : (Int, Int) -> Int, a : Int, b : Int) : Int{
  return sum(a,b)
}
```

## 람다식과 고차 함수 호출
- 값에 의한 호출
  - 값에 의한 호출은 함수가 또 다른 함수의 인자로 전달될 경우 람다식 함수는 값으로 처리되어 그 즉시 함수가 수행된 후 값을 전달
```
fun main(){
  val result = callByValue(lambda())
  println(result)
}
fun callByValue(b : Boolean) : Boolean{
  println("callByValue function")
  return b
}
val lamda : () -> Boolean = {
  println("lambda
}

결과
lambda function
callByValue function
true
```
- 이름에 의한 람다식 호출
  - 매개변수 b가 람다식 자료형으로 선언됨
```
fun main() {
  val result = callByName(otherLambda)
  println(result)
}
fun callByName(b:() -> Boolean) : Boolean {
  println("callByName function")
  return b()
}
fun otherLambda:() -> Boolean = {
  prinltn("otherLambda function")
  true
}

결과
callByName function
otherLambda function
true
```

- 다른 함수의 참조에 의한 일반 함수 호출
```
val res1 = funcParam(3,2,::sum)
fun funcParam(a:Int, b:Int, c:(Int,Int) -> Int) : Int{
  return c(a,b)
}
```
