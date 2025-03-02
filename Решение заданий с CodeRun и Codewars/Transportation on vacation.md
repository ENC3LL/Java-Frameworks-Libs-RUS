[[CodeRW]]

После тяжелого квартала в офисе вы решаете немного отдохнуть в отпуске. Так что вы забронируете перелет для себя и своей девушки и постараетесь оставить всю неразбериху позади.

Вам понадобится арендованный автомобиль для того, чтобы вы могли передвигаться во время отпуска. Менеджер по прокату автомобилей делает вам несколько выгодных предложений.

Каждый день аренды автомобиля стоит 40 долларов. Если вы арендуете автомобиль на 7 или более дней, вы получаете скидку 50 долларов. В качестве альтернативы, если вы арендуете автомобиль на 3 или более дней, вы получаете скидку 20 долларов от общей суммы.

Напишите код, который выдает общую сумму за разные дни(d).

# Решение

```java ignore
public class Kata {  
    public static int rentalCarCost(int d) {  
        int res = 0;  
        if (d >= 3 && d < 7) {  
            return res = (40*d)-20;  
        }  
        if (d >= 7) {  
            return res = (40*d)-50;  
        } else {  
            return res = 40 * d;  
        }  
    }  
}
```

# Варианты решения

```java ignore
public class Kata {
  private static final int COST_PER_DAY = 40;
  
  public static int rentalCarCost(int d) {
    if (d < 3)       return d * COST_PER_DAY;
    else if (d >= 7) return d * COST_PER_DAY - 50;
    else             return d * COST_PER_DAY - 20;
  }
}
```


```java ignore
public class Kata {
  public static int rentalCarCost(int d) {
    return d < 7 ? d < 3 ? 40 * d : 40 * d - 20 : 40 * d - 50;
  }
}
```

```java ignore
public class Kata {
  public static int rentalCarCost(int d) {
    final int COST_PER_DAY = 40;
    return d * COST_PER_DAY - (d >= 7 ? 50 : d >= 3 ? 20 : 0); 
  }
}
```