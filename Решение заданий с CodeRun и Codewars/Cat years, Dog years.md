[[CodeRW]]

# Задание ката

У меня есть кошка и собака.

Я получил их одновременно с котенком/щенком. Это было много лет назад.`humanYears`

Верните их соответствующий возраст теперь как [,,`humanYears``catYears``dogYears`]

ПРИМЕЧАНИЯ:

- `humanYears` >= 1
- `humanYears` являются только целыми числами

## Кошачьи годы

- `15` кошачьи годы для первого года
- `+9` кошачьи годы на второй год
- `+4` лет cat за каждый последующий год

## Собачьи годы

- `15` собачьи годы для первого года
- `+9` собачьи годы на второй год
- `+5` собачьи годы за каждый последующий год

# Решение

```java ignore
public class Dinglemouse {  
  
    public static int[] humanYearsCatYearsDogYears(final int humanYears) {  
        int catyears = 15;  
        int dogyears = 15;  
  
        if (humanYears == 1) {  
            return new int[]{humanYears, catyears, dogyears};  
        } else if (humanYears == 2) {  
            return new int[]{humanYears, catyears +9, dogyears+9};  
        } else if (humanYears >= 3) {  
            return new int[]{humanYears, catyears+9 +(4*(humanYears-2)) , dogyears+9 +(5*(humanYears-2))};  
        }  
        return null;  
    }  
}
```

# Варианты решения

```java ignore
public class Dinglemouse {
  public static int[] humanYearsCatYearsDogYears(final int y) {
    return new int[]{y,y==1?15:16+4*y,y==1?15:14+5*y};
  }
}
```

```java ignore
public class Dinglemouse {

  public static int[] humanYearsCatYearsDogYears(final int humanYears) {
     int catYears =0, dogYears = 0;
        switch (humanYears) {
            default:
                catYears = 4 * (humanYears - 2);
                dogYears = 5 * (humanYears - 2);
            case 2:
                catYears += 9;
                dogYears += 9;
            case 1:
                catYears += 15;
                dogYears += 15;
        }
    return new int[]{humanYears, catYears, dogYears};
  }

}
```