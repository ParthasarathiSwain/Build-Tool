
# 🚀 Gradle Guide

Gradle is a powerful and flexible build automation tool used for Java, Android, and many other programming languages. 
It is designed to automate compiling, testing, packaging, deployment, and dependency management tasks. 
Gradle combines the best features of Apache Ant and Maven and adds its own flexibility with Groovy/Kotlin DSL scripts.

---

## ⚡ Features of Gradle
- **High Performance** → Uses incremental builds and caching to make builds faster.
- **Flexible** → Supports Java, Android, Scala, Kotlin, Groovy, and even C/C++ projects.
- **Dependency Management** → Works with Maven and Ivy repositories.
- **Build Scripts** → Uses Groovy or Kotlin DSL instead of XML (like Maven).
- **Multi-project builds** → Allows building multiple modules in one project easily.
- **Plugin System** → Rich ecosystem of plugins for Spring Boot, Android, Docker, etc.
- **Integration** → Works with IDEs like IntelliJ, Eclipse, and build servers like Jenkins, GitHub Actions, etc.

---

## 📂 Gradle Project Structure
A typical Gradle project contains:
```
my-project/
 ├── build.gradle       # Main build script
 ├── settings.gradle    # Multi-module project settings
 └── src/
     └── main/
         └── java/      # Java source files
     └── test/          # Unit test files
```

---

## ⚙️ build.gradle Example (Groovy DSL)
```groovy
plugins {
    id 'java'
    id 'application'
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter'
    testImplementation 'junit:junit:4.13.2'
}

application {
    mainClass = 'com.example.Main'
}
```

---

## 📌 Common Gradle Commands
- `gradle build` → Compiles, tests, and packages the project.
- `gradle clean` → Deletes build directory.
- `gradle test` → Runs tests.
- `gradle run` → Runs the application (if `application` plugin is used).
- `gradle dependencies` → Displays dependency tree.

---

## 🆚 Gradle vs Maven
| Feature            | Maven                          | Gradle                        |
|--------------------|--------------------------------|-------------------------------|
| **Configuration**  | XML (`pom.xml`)                | Groovy/Kotlin DSL (`build.gradle`) |
| **Performance**    | Slower (no caching by default) | Faster with incremental builds |
| **Flexibility**    | Convention-over-configuration  | Highly customizable           |
| **Popularity**     | Widely used in Java projects   | Popular in Java & Android     |

---

## 🌍 When to Use Gradle?
- Large projects with multiple modules.
- Android development (default build system).
- Projects requiring faster builds & flexibility.
- When you want both Maven’s dependency management and Ant’s flexibility.

---

## 📧 Contact
For any queries, feel free to reach out:  
**Email**: rajaswain6969@gmail.com  
