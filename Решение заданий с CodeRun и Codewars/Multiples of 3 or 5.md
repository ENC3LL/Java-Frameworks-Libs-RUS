[[CodeRW]]

Если мы перечислим все натуральные числа меньше 10, кратные 3 или 5, мы получим 3, 5, 6 и 9. Сумма этих кратных равна 23.

Завершите решение так, чтобы оно вернуло сумму всех чисел, кратных 3 или 5 **ниже** переданного числа.

**Заметка:** Если число кратно **3** и 5, пересчитайте его _только один раз_.

# Решение

```java ignore
public class Solution {  
  
    public int solution(int number) {  
        int i = 0;  
        int a = 0;  
        while (i < number){  
            if (i%3==0 || i%5==0){  
                a+=i;  
                i++;  
            } else{  
                a+=0;  
                i++;  
            }  
        }  
        return a;  
    }  
}
```

# Варианты решения

```java ignore
public class Solution {

  public int solution(int number) {
  	int sum=0;
    
    for (int i=0; i < number; i++){
    	if (i%3==0 || i%5==0){sum+=i;}
    }
    return sum;
  }
}
```

```java ignore
import java.util.stream.IntStream;

public class Solution {
  public int solution(int number) {
    return IntStream.range(0, number)
                    .filter(n -> (n % 3 == 0) || (n % 5 == 0))
                    .sum();
  }
}
```

