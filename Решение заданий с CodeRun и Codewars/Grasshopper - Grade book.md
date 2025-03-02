[[CodeRW]]

## Зачетная книжка

Завершите функцию так, чтобы она нашла среднее значение из трех переданных ей баллов и вернула буквенное значение, связанное с этой оценкой.

| Числовой балл      | Буквенный разряд |
| ------------------ | ---------------- |
| 90 <= score <= 100 | «А»              |
| 80 <= score < 90   | «В»              |
| 70 <= score < 80   | «С»              |
| 60 <= score < 70   | «D»              |
| 0 <= score < 60    | «F»              |

Все проверенные значения находятся в диапазоне от 0 до 100. Нет необходимости проверять отрицательные значения или значения больше 100.

# Решение

```java ignore
public class GrassHopper {  
    public static char getGrade(int s1, int s2, int s3) {  
        int score = (s1 + s2 + s3)/3;  
        if (score >= 90 && score <= 100) {  
            return 'A';  
        } else if (score >= 80 && score < 90) {  
            return 'B';  
        } else if (score >= 70 && score < 80) {  
            return 'C';  
        }   else if (score >= 60 && score < 70) {  
            return 'D';  
        } else {  
            return 'F';  
        }  
    }  
}
```

# Варианты решения

```java ignore
public class GrassHopper {

    public static char getGrade(int s1, int s2, int s3) {
        int mean = (s1 + s2 + s3) / 3;
        if (mean >= 90) return 'A';
        if (mean >= 80) return 'B';
        if (mean >= 70) return 'C';
        if (mean >= 60) return 'D';
        return 'F';
    }
}
```

```java ignore
public class GrassHopper {

    public static char getGrade(int s1, int s2, int s3) {
        s1=(s1+s2+s3)/3;
        return s1 >= 90 ? 'A':s1 >= 80 ? 'B':s1 >= 70 ? 'C':s1 >= 60 ? 'D':'F';
    }
}
```