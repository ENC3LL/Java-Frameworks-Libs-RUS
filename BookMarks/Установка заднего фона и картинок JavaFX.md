[[bookmarks]]
!Могут быть ошибки из-за не того импорта (нап. intellij может предложить java.awt а не Javafx)
```java ignore
package org.example;  
  
import javafx.application.Application;  
import javafx.scene.Scene;  
import javafx.scene.image.Image;  
import javafx.scene.layout.Background;  
import javafx.scene.layout.BackgroundImage;  
import javafx.scene.layout.BackgroundPosition;  
import javafx.scene.layout.BackgroundRepeat;  
import javafx.scene.layout.BackgroundSize;  
import javafx.scene.layout.Pane;  
import javafx.stage.Stage;  
  
public class Main extends Application {  
  
    @Override  
    public void start(Stage primaryStage) {  
        // Создаем корневой контейнер  
        Pane root = new Pane();  
  
        // Загружаем изображение для фона  
        Image image = new Image("C:/Users/image.jpg"); // Укажите путь к вашему изображению  
  
        // Создаем BackgroundImage        
        BackgroundImage backgroundImage = new BackgroundImage(  
                image,  
                BackgroundRepeat.NO_REPEAT, // Повторение по горизонтали  
                BackgroundRepeat.NO_REPEAT, // Повторение по вертикали  
                BackgroundPosition.CENTER,  // Позиция изображения  
                new BackgroundSize(BackgroundSize.AUTO, BackgroundSize.AUTO, false, false, true, true) // Размеры фона  
        );  
  
        // Создаем Background  
        Background background = new Background(backgroundImage);  
  
        // Устанавливаем фон для корневого контейнера  
        root.setBackground(background);  
  
        // Создаем сцену и устанавливаем корневой контейнер  
        Scene scene = new Scene(root, 800, 600);  
  
        // Устанавливаем сцену для Stage (окна)  
        primaryStage.setScene(scene);  
        primaryStage.setTitle("JavaFX Background Image Example");  
        primaryStage.show();  
    }  
  
    public static void main(String[] args) {  
        launch(args);  
    }  
}
```

### Пояснение:

- **`Image image = new Image("file:path/to/your/image.jpg");`**: Загружает изображение из файла. Убедитесь, что путь к изображению указан правильно.
- **`BackgroundImage`**: Используется для создания фонового изображения. Вы можете настроить повторение, позицию и размер изображения.
- **`Background`**: Создает фон на основе `BackgroundImage`.
- **`root.setBackground(background);`**: Устанавливает фон для корневого контейнера.

### Примечания:

- Если вы хотите, чтобы изображение растягивалось на весь контейнер, вы можете изменить параметры `BackgroundSize` на `new BackgroundSize(100, 100, true, true, false, true)`.
- Если изображение находится в ресурсах вашего проекта, вы можете загрузить его с помощью `getClass().getResource("/path/to/your/image.jpg")`.