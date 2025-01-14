[[bookmarks]][[css]]
Чтобы сделать поле ввода email красным и добавить анимацию (например, тряску) при ошибке, можно использовать CSS для стилизации и JavaFX для анимации. Вот как это можно реализовать:

### 1. Добавление CSS для стилизации

Создайте CSS-файл (например, `styles.css`), чтобы задать стили для поля ввода при ошибке:

```css ignore
.error-field {  
    -fx-border-color: red;  
    -fx-border-width: 2px;  
    -fx-border-radius: 5px;  
    -fx-background-color: #ffe6e6; /* Светло-красный фон */  
}  
  
.error-message {  
    -fx-text-fill: red;  
    -fx-font-size: 12px;  
}
```

### 2. Анимация тряски

Для анимации тряски можно использовать `TranslateTransition` из JavaFX.

### 3. Интеграция в JavaFX

Вот пример кода, который объединяет всё:

```java ignore
import javafx.animation.TranslateTransition;  
import javafx.application.Application;  
import javafx.scene.Scene;  
import javafx.scene.control.Button;  
import javafx.scene.control.Label;  
import javafx.scene.control.TextField;  
import javafx.scene.layout.VBox;  
import javafx.stage.Stage;  
import javafx.util.Duration;  
  
public class EmailValidationApp extends Application {  
  
    @Override  
    public void start(Stage primaryStage) {  
        TextField emailField = new TextField();  
        Button submitButton = new Button("Submit");  
        Label errorMessage = new Label();  
  
        VBox root = new VBox(10, emailField, submitButton, errorMessage);  
        Scene scene = new Scene(root, 300, 200);  
  
        // Загрузка CSS-файла  
        String cssPath = getClass().getResource("/styles.css").toExternalForm();  
        if (cssPath != null) {  
            System.out.println("CSS file loaded: " + cssPath);  
            scene.getStylesheets().add(cssPath);  
        } else {  
            System.err.println("CSS file not found!");  
        }  
  
        // Обработчик кнопки  
        submitButton.setOnAction(e -> {  
            if (emailField.getText().isEmpty() || !emailField.getText().contains("@")) {  
                // Добавляем стиль ошибки  
                emailField.getStyleClass().add("error-field");  
                errorMessage.getStyleClass().add("error-message");  
                errorMessage.setText("Invalid email!");  
  
                // Запускаем анимацию тряски  
                shakeField(emailField);  
            } else {  
                // Убираем стиль ошибки  
                emailField.getStyleClass().remove("error-field");  
                errorMessage.getStyleClass().remove("error-message");  
                errorMessage.setText("Email is valid!");  
            }  
        });  
  
        primaryStage.setTitle("Email Validation");  
        primaryStage.setScene(scene);  
        primaryStage.show();  
    }  
  
    // Метод для анимации тряски  
    private void shakeField(TextField field) {  
        TranslateTransition tt = new TranslateTransition(Duration.millis(50), field);  
        tt.setFromX(0); // Начальное положение  
        tt.setToX(10);  // Сдвиг вправо  
        tt.setCycleCount(4); // Количество колебаний  
        tt.setAutoReverse(true); // Возврат в исходное положение  
        tt.play(); // Запуск анимации  
    }  
  
    public static void main(String[] args) {  
        launch(args);  
    }  
}
```

### Что происходит:

1. **CSS-стили**:
    - `.error-field` — добавляет красную рамку и светло-красный фон для поля ввода.
    - `.error-message` — задает красный цвет текста для сообщения об ошибке.
2. **Анимация тряски**:
    - Используется `TranslateTransition`, чтобы поле ввода немного двигалось влево и вправо.
3. **Логика проверки**:
    - Если email невалидный, к полю добавляется CSS-класс `error-field`, и запускается анимация тряски.
    - Если email валидный, CSS-класс удаляется.

### Как это выглядит:

- При вводе некорректного email:
    - Поле ввода становится красным.
    - Поле немного трясется.
    - Выводится сообщение об ошибке.
- При вводе корректного email:
    - Поле возвращается к обычному виду.
    - Выводится сообщение об успешной проверке.