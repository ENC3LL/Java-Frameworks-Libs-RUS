[[Spring]][[Spring1]]
Если нет HTML и/или JS сайта, то можно использовать Java в качестве Backend и Frontend сразу

### Шаг 1: Добавление Thymeleaf

#### 1.1. Добавьте зависимость Thymeleaf в `pom.xml`:
```xml ignore
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```

### Шаг 2: Создание HTML-страниц

#### 2.1. `register.html` (страница регистрации)

Создайте файл `register.html` в папке `src/main/resources/templates`:
```html ignore
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Регистрация</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .registration-form {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .registration-form h2 {
            margin-bottom: 20px;
        }
        .registration-form input {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        .registration-form button {
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        .registration-form button:hover {
            background-color: #218838;
        }
        .registration-form a {
            display: block;
            text-align: center;
            margin-top: 10px;
            color: #28a745;
            text-decoration: none;
        }
        .registration-form a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="registration-form">
        <h2>Регистрация</h2>
        <form th:action="@{/users/register}" method="post">
            <input type="text" name="username" placeholder="Имя пользователя" required>
            <input type="password" name="password" placeholder="Пароль" required>
            <button type="submit">Зарегистрироваться</button>
        </form>
        <a th:href="@{/users/login}">Уже есть аккаунт? Войдите!</a>
        <p th:if="${error}" style="color: red;" th:text="${error}"></p>
    </div>
</body>
</html>
```

#### 2.2. `login.html` (страница логина)

Создайте файл `login.html` в папке `src/main/resources/templates`:
```html ignore
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Вход</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .login-form {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .login-form h2 {
            margin-bottom: 20px;
        }
        .login-form input {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        .login-form button {
            width: 100%;
            padding: 10px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }
        .login-form button:hover {
            background-color: #218838;
        }
        .login-form a {
            display: block;
            text-align: center;
            margin-top: 10px;
            color: #28a745;
            text-decoration: none;
        }
        .login-form a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="login-form">
        <h2>Вход</h2>
        <form th:action="@{/users/login}" method="post">
            <input type="text" name="username" placeholder="Имя пользователя" required>
            <input type="password" name="password" placeholder="Пароль" required>
            <button type="submit">Войти</button>
        </form>
        <a th:href="@{/users/register}">Нет аккаунта? Зарегистрируйтесь!</a>
        <p th:if="${error}" style="color: red;" th:text="${error}"></p>
    </div>
</body>
</html>
```

### Шаг 3: Обновление контроллера

#### 3.1. Добавление методов для отображения страниц

Обновим `UserController`:

```java ignore
import com.example.WebRegTest.model.User;
import com.example.WebRegTest.service.UserService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;

@Controller // Изменили @RestController на @Controller
@RequestMapping("/users")
public class UserController {

    @Autowired
    private UserService userService;

    // Отображение страницы регистрации
    @GetMapping("/register")
    public String showRegistrationForm(Model model) {
        model.addAttribute("user", new User());
        return "register";
    }

    // Обработка регистрации
    @PostMapping("/register")
    public String registerUser(@ModelAttribute User user, Model model) {
        try {
            userService.registerUser(user);
            return "redirect:/users/login"; // Перенаправляем на страницу логина
        } catch (RuntimeException e) {
            model.addAttribute("error", e.getMessage());
            return "register";
        }
    }

    // Отображение страницы логина
    @GetMapping("/login")
    public String showLoginForm(Model model) {
        model.addAttribute("user", new User());
        return "login";
    }

    // Обработка логина
    @PostMapping("/login")
    public String loginUser(@ModelAttribute User user, Model model) {
        try {
            userService.loginUser(user.getUsername(), user.getPassword());
            return "redirect:/users/success"; // Перенаправляем на страницу успеха
        } catch (RuntimeException e) {
            model.addAttribute("error", e.getMessage());
            return "login";
        }
    }

    // Страница успеха
    @GetMapping("/success")
    public String showSuccessPage() {
        return "success";
    }
}
```

### Шаг 4: Создание страницы успеха

#### 4.1. `success.html`

Создайте файл `success.html` в папке `src/main/resources/templates`:
```html ignore
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Успех</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
        }
        .success-message {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .success-message h2 {
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <div class="success-message">
        <h2>Успешный вход!</h2>
        <p>Добро пожаловать в систему.</p>
    </div>
</body>
</html>
```

### Шаг 5: Запуск приложения

1. Запустите приложение:
```bash ignore
mvn spring-boot:run
```
2. Откройте браузер и перейдите по адресу:
http://localhost:8080/users/register
3. Зарегистрируйтесь, затем войдите в систему.

### Итог

#### Что мы добавили:

1. **Thymeleaf**:
    - Для отображения HTML-страниц.
2. **HTML-страницы**:
    - `register.html` — форма регистрации.
    - `login.html` — форма входа.
    - `success.html` — страница успешного входа.
3. **Контроллер**:
    - Обрабатывает регистрацию, вход и отображает страницы.