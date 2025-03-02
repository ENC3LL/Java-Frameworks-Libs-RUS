[[bookmarks]][[JavaBase]]
```java ignore
import java.util.ArrayList;
import java.util.List;

public class CollectionExample {

    // Метод для удаления элемента из коллекции
    public static <T> void removeElement(List<T> list, T element) {
        list.remove(element); // Удаляем элемент
    }

    // Метод для очистки коллекции
    public static <T> void clearCollection(List<T> list) {
        list.clear(); // Очищаем коллекцию
    }

    // Пример использования
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("Элемент 1");
        list.add("Элемент 2");

        // Удаляем элемент
        removeElement(list, "Элемент 1");
        System.out.println("После удаления: " + list);

        // Очищаем коллекцию
        clearCollection(list);
        System.out.println("После очистки: " + list);
    }
}
```

Теперь код для работы с коллекциями стал более универсальным.

- **Как использовать**:
    
    - Вызовите метод `removeElement` для удаления конкретного элемента или `clearCollection` для очистки всей коллекции.
        
- **Преимущества**:
    
    - Код стал более модульным и легко интегрируется с другими заметками.
    - Упрощено тестирование и отладка.

