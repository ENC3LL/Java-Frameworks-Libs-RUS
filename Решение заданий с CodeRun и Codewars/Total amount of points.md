[[CodeRW]]

Наша футбольная команда завершила чемпионат.

Результаты матчей нашей команды записываются в коллекцию строк. Каждый матч представлен строкой в формате , где — счет нашей команды и счет наших соперников.`"x:y"``x``y`

Например: `["3:1", "2:2", "0:1", ...]`

Очки начисляются за каждый матч следующим образом:

- если x > y: 3 очка (победа)
- если x < y: 0 очков (проигрыш)
- если x = y: 1 балл (ничья)

Нам нужно написать функцию, которая принимает эту коллекцию и возвращает количество очков, набранных нашей командой () в чемпионате по правилам, приведенным выше.`x`

Примечания:

- Наша команда всегда играет 10 матчей в чемпионате
- 0 <= x <= 4
- 0 <= y <= 4

# Решение

```java ignore
public class TotalPoints {  
  
    public static int points(String[] games) {  
        int totalPoints = 0;  
  
        for (String result : games) {  
            String[] scores = result.split(":");  
            int ourScore = Integer.parseInt(scores[0]);  
            int opponentScore = Integer.parseInt(scores[1]);  
  
            if (ourScore > opponentScore) {  
                totalPoints += 3;   
            } else if (ourScore == opponentScore) {  
                totalPoints += 1;   
            }  
        }  
        return totalPoints;  
    }  
      
}
```

# Варианты решения

```java ignore
public class TotalPoints {
  
    public static int points(String[] games) {
        int sum = 0;
        
        for (String s : games) {
          char x = s.charAt(0),
               y = s.charAt(2);
          
          sum += x > y ? 3 : x == y ? 1 : 0;
        }
        
        return sum;
    }
}
```

```java ignore
import java.util.Arrays;
public class TotalPoints {
  
    public static int points(String[] games) {
       return Arrays.stream(games)
                     .mapToInt(score -> score.charAt(0) - score.charAt(2))
                     .map(match -> match > 0 ? 3 : match == 0 ? 1 : 0)
                     .sum();
    }
}
```

```java ignore
public class TotalPoints {
  
    public static int points(String[] games) {
        int points = 0;
        for (String game : games) {
            String[] scores = game.split(":");
            int x = Integer.parseInt(scores[0]);
            int y = Integer.parseInt(scores[1]);
            if (x > y) {
                points += 3;
            } else if (x == y) {
                points++;
            }
        }
        return points;
    }
}
```