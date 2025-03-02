[[bookmarks]]
!Могут быть ошибки из-за не того импорта (нап. intellij может предложить java.awt а не Javafx)
```java ignore
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.image.Image;
import javafx.scene.layout.*;
import javafx.stage.Stage;

public class BackgroundExample extends Application {

    // Метод для установки фона
    public static void setBackground(Pane root, String imagePath) {
        // Загружаем изображение
        Image image = new Image(BackgroundExample.class.getResourceAsStream(imagePath));

        // Создаем BackgroundImage
        BackgroundImage backgroundImage = new BackgroundImage(
                image,
                BackgroundRepeat.NO_REPEAT, // Не повторять изображение
                BackgroundRepeat.NO_REPEAT,
                BackgroundPosition.CENTER,  // Позиция изображения
                new BackgroundSize(100, 100, true, true, false, true) // Размеры фона
        );

        // Устанавливаем фон для корневого контейнера
        root.setBackground(new Background(backgroundImage));
    }

    @Override
    public void start(Stage primaryStage) {
        // Создаем корневой контейнер
        Pane root = new Pane();

        // Устанавливаем фон
        setBackground(root, "/images/back.png");

        // Создаем сцену и отображаем окно
        Scene scene = new Scene(root, 800, 600);
        primaryStage.setTitle("Пример фона");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}```

*Изменено Теперь код для установки фона вынесен в отдельный метод `setBackground`, который можно использовать в любом проекте. *

- **Как использовать**:
    - Вызовите метод `setBackground`, передав корневой контейнер и путь к изображению.

### Пояснение:

- **`Image image = new Image("file:path/to/your/image.jpg");`**: Загружает изображение из файла. Убедитесь, что путь к изображению указан правильно.
- **`BackgroundImage`**: Используется для создания фонового изображения. Вы можете настроить повторение, позицию и размер изображения.
- **`Background`**: Создает фон на основе `BackgroundImage`.
- **`root.setBackground(background);`**: Устанавливает фон для корневого контейнера.

### Примечания:

- Если вы хотите, чтобы изображение растягивалось на весь контейнер, вы можете изменить параметры `BackgroundSize` на `new BackgroundSize(100, 100, true, true, false, true)`.
- Если изображение находится в ресурсах вашего проекта, вы можете загрузить его с помощью `getClass().getResource("/path/to/your/image.jpg")`.