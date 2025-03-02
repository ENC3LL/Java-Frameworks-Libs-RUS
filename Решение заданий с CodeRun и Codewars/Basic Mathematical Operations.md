[[CodeRW]]
Ваша задача состоит в том, чтобы создать функцию, которая выполняет четыре основные математические операции.

Функция должна принимать три аргумента - operation(строка/char), value1(число), value2(число).  
Функция должна возвращать результат в виде чисел после применения выбранной операции.

### Примеры(Оператор, значение1, значение2) --> вывод

```
('+', 4, 7) --> 11
('-', 15, 18) --> -3
('*', 5, 5) --> 25
('/', 49, 7) --> 7
```

# Решение

```java ignore
public class BasicOperations
{
    public static Integer basicMath(String op, int v1, int v2)
    {
        if (op.equals("+")){
            return v1 + v2;
        } else if (op.equals("-")){
            return v1 - v2;
        } else if (op.equals("*")){
            return v1 * v2;
        }   else {
            return v1 / v2;
        }
    }
}
```

# Варианты решения

```java ignore
public class BasicOperations{
  public static Integer basicMath(String symbol, int x, int y){
    switch (symbol){
      case "+": return x+y;
      case "-": return x-y;
      case "*": return x*y;
      case "/": return x/y;
    }
    return 0;
  }
}
```

```java ignore
public class BasicOperations
{
  public static Integer basicMath(String op, int v1, int v2)
  {
    return (op=="+") ? (v1+v2) : (op=="-") ? (v1-v2) : (op=="*") ? (v1*v2) : (v2==0) ? null : (v1/v2);
    
  }
}
```