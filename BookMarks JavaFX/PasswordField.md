[[bookmarks]][[JavaFX]]

```java ignore
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.PasswordField;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class PasswordFieldExample extends Application {

    @Override
    public void start(Stage primaryStage) {
        // Создаем поле для ввода пароля
        PasswordField passwordField = new PasswordField();
        passwordField.setPromptText("Введите пароль");

        // Кнопка для проверки пароля
        Button submitButton = new Button("Проверить");
        submitButton.setOnAction(e -> {
            String password = passwordField.getText();
            System.out.println("Введенный пароль: " + password);
        });

        // Создаем корневой контейнер
        VBox root = new VBox(10, passwordField, submitButton);
        root.setPadding(new javafx.geometry.Insets(10));

        // Создаем сцену и отображаем окно
        Scene scene = new Scene(root, 300, 200);
        primaryStage.setTitle("PasswordField Example");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```

- **Как использовать**:
    
    - Добавьте `PasswordField` в интерфейс и настройте обработчик событий для кнопки проверки пароля.

- **Преимущества**:
    
    - Код стал более модульным и легко интегрируется с другими заметками, например, с заметкой про проверку email.