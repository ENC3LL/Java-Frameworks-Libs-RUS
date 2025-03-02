[[bookmarks]]
```java ignore
private void setupUI(Stage stage) {
    AnchorPane root = new AnchorPane();

    // Создаем контейнер для кнопок
    HBox controlButtons = createControlButtons(stage);
    root.getChildren().add(controlButtons);
    AnchorPane.setTopAnchor(controlButtons, 10.0);
    AnchorPane.setRightAnchor(controlButtons, 10.0);

    // Размеры окна
    double windowWidth = 1200;
    double windowHeight = 800;

    // Создаем закругленный клип
    Rectangle clip = new Rectangle(windowWidth, windowHeight);
    clip.setArcWidth(50); // Радиус закругления
    clip.setArcHeight(50);

    // Применяем клип к корневому контейнеру
    root.setClip(clip);

    // Прозрачная сцена
    Scene scene = new Scene(root, windowWidth, windowHeight);
    scene.setFill(Color.TRANSPARENT);

    // Установка стиля окна
    stage.initStyle(StageStyle.TRANSPARENT);

    // Подключение CSS
    try {
        scene.getStylesheets().add(getClass().getResource("/styles.css").toExternalForm());
    } catch (NullPointerException e) {
        System.err.println("Файл styles.css не найден! Убедитесь, что он находится в правильной директории.");
    }

    stage.setScene(scene);
    stage.show();
}
```
