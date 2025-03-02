[[CodeRW]]

Напишите функцию, которая принимает целое число в качестве входных данных и возвращает количество битов, равное единице в двоичном представлении этого числа. Вы можете гарантировать, что входные данные не являются отрицательными.

_Пример_: Двоичное представление равно , поэтому функция должна возвращать в этом случае`1234` `10011010010` `5`

# Решение

```java ignore
public class BitCounting {  
  
    public static int countBits(int n){  
        String binary = Integer.toBinaryString(n);  
  
        int count = 0;  
  
        for (char c : binary.toCharArray()) {  
            if (c == '1') {  
                count++;  
            }  
        }  
  
        return count;  
    }  
}
```

# Вариант решения

```java ignore
public class BitCounting {

	public static int countBits(int n){
		
    return Integer.bitCount(n);
	}
	
}
```

