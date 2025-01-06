# Spring Boot Demonstration Project

## Overview

This project demonstrates the basics of creating a simple web application using Spring Boot and Thymeleaf. The goal is to showcase how to set up controllers, handle HTTP requests, and use templates for rendering dynamic content.

### Features
- **Homepage:** Displays a simple greeting message.
- **Greeting Page:** Allows dynamic personalization by passing a parameter in the URL.

### Technologies Used
- **Java 17**
- **Spring Boot**
- **Thymeleaf**
- **Maven**

---

## Installation

### Prerequisites
Ensure you have the following installed on your system:
- JDK 17 or higher
- Apache Maven

### Steps
1. Clone the repository:
   ```bash
   git clone https://github.com/Puravistula/Zadanie1_SpringProject.git
   cd Zadanie1_SpringProject
   ```
2. Build the project:
   ```bash
   mvn clean install
   ```
3. Run the application:
   ```bash
   mvn spring-boot:run
   ```
4. Open your browser and navigate to:
   - [http://localhost:8080](http://localhost:8080): Homepage
   - [http://localhost:8080/greeting?name=YourName](http://localhost:8080/greeting?name=YourName): Greeting page

---

## Usage

### Homepage
Access the homepage at `http://localhost:8080` to see the following message:
```
Hello Vistula, in my first spring controller
```

### Greeting Page
Access the greeting page at `http://localhost:8080/greeting?name=Mikolaj` to see a personalized greeting:
```
Welcome, Mikolaj!
```
If the `name` parameter is not provided, it defaults to "World."

---

## Code Structure

### Main Application Class
The entry point for the application:
```java
@SpringBootApplication
public class PuraApplication {
    public static void main(String[] args) {
        SpringApplication.run(PuraApplication.class, args);
    }
}
```

### Controller
Defines two routes: `/` for the homepage and `/greeting` for the greeting page:
```java
@Controller
public class HelloController {

    @GetMapping(value = "/")
    @ResponseBody
    public String hello() {
        return "Hello Vistula, in my first spring controller";
    }

    @GetMapping(value = "/greeting")
    public String greeting(@RequestParam(name="name", required = false, defaultValue = "World") String name, Model model) {
        model.addAttribute("name", name);
        return "greeting";
    }
}
```

### Thymeleaf Template
The `greeting.html` template located in `src/main/resources/templates`:
```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Greeting</title>
</head>
<body>
    <h1>Welcome, <span th:text="${name}">Guest</span>!</h1>
</body>
</html>
```

---

## Future Improvements
- Add additional endpoints for more functionality.
- Integrate a database using Spring Data JPA.
- Write unit and integration tests to ensure code reliability.

---

## License
This project is open-source and available under the MIT License.
