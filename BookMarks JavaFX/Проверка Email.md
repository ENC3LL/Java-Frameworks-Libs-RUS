[[bookmarks]]

*Пункт 2 изменён Теперь код для проверки email вынесен в отдельный класс `EmailValidator`, который можно использовать в любом проекте.*
- **Как использовать**:
    - Вызовите метод `isValidEmail`, передав строку с email для проверки.

### 1. Регулярное выражение для email

Стандартное регулярное выражение для проверки email:

```java ignore
String emailRegex = "^(?=.{1,64}@)[A-Za-z0-9_-]+(\\.[A-Za-z0-9_-]+)*@"  
        + "[^-][A-Za-z0-9-]+(\\.[A-Za-z0-9-]+)*(\\.[A-Za-z]{2,})$";;
```

### 2. Проверка email с помощью regex

Используйте метод `matches` класса `String`, чтобы проверить, соответствует ли строка регулярному выражению:

```java ignore
import java.util.regex.Pattern;

public class EmailValidator {

    // Регулярное выражение для проверки email
    private static final String EMAIL_REGEX = "^(?=.{1,64}@)[A-Za-z0-9_-]+(\\.[A-Za-z0-9_-]+)*@"
            + "[^-][A-Za-z0-9-]+(\\.[A-Za-z0-9-]+)*(\\.[A-Za-z]{2,})$";

    // Метод для проверки email
    public static boolean isValidEmail(String email) {
        return Pattern.matches(EMAIL_REGEX, email);
    }

    // Пример использования
    public static void main(String[] args) {
        String email1 = "example@mail.com";
        String email2 = "invalid-email";

        System.out.println(email1 + " is valid: " + isValidEmail(email1)); // true
        System.out.println(email2 + " is valid: " + isValidEmail(email2)); // false
    }
}
```

### 3. Интеграция с JavaFX

Если вы используете JavaFX, можно добавить проверку email в обработчик события (например, при нажатии кнопки):

```java ignore
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Label;
import javafx.scene.control.TextField;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

import java.util.regex.Pattern;

public class EmailValidationApp extends Application {

    @Override
    public void start(Stage primaryStage) {
        TextField emailField = new TextField();
        Button submitButton = new Button("Submit");
        Label messageLabel = new Label();
        submitButton.setOnAction(e -> {
            String email = emailField.getText();
            if (isValidEmail(email)) {
                messageLabel.setText("Email is valid!");
            } else {
                messageLabel.setText("Invalid email!");
            }
        });
        VBox root = new VBox(10, emailField, submitButton, messageLabel);
        Scene scene = new Scene(root, 300, 200);
        primaryStage.setTitle("Email Validation");
        primaryStage.setScene(scene);
        primaryStage.show();
    }
    public static boolean isValidEmail(String email) {
        String emailRegex = "^(?=.{1,64}@)[A-Za-z0-9_-]+(\\.[A-Za-z0-9_-]+)*@"  
        + "[^-][A-Za-z0-9-]+(\\.[A-Za-z0-9-]+)*(\\.[A-Za-z]{2,})$";;
        return Pattern.matches(emailRegex, email);
    }
    public static void main(String[] args) {
        launch(args);
    }
}

```
### Что делает программа:

1. Пользователь вводит email в текстовое поле.
2. При нажатии кнопки проверяется, соответствует ли введенный email регулярному выражению.
3. Если email корректен, выводится сообщение "Email is valid!", иначе — "Invalid email!".

### Примечания:

- Регулярное выражение проверяет наличие символа `@`, домена (например, `mail.com`) и корректность символов.