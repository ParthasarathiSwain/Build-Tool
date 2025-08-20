# 🚀 Build Tools & Maven Guide

## 📌 What are Build Tools?
Build tools are used to **automate the application build process**.  
They handle:
- ✅ Compile the source code  
- ✅ Download required dependencies (Ex: Spring Boot, Hibernate, JUnit, Log4j, Kafka...)  
- ✅ Execute Unit Test Cases (JUnit)  
- ✅ Package applications as **JAR** or **WAR**  

| Format | Full Form | Usage |
|--------|-----------|-------|
| **JAR** | Java Archive | Packaging for Java Standalone Applications |
| **WAR** | Web Archive  | Packaging for Java Web Applications |

👉 Instead of performing these steps manually, build tools **automate** the process.

---

## 🛠️ Popular Java Build Tools
1. 🟠 **Ant** (Outdated)  
2. 🔵 **Maven** (Widely used)  
3. 🟢 **Gradle** (Modern, flexible)

---

# 🏗️ Maven

### 📖 What is Maven?
- Free & Open Source software by **Apache Organization**  
- Developed in **Java**  
- Performs **Build Automation** for Java projects  
- Known as a **Java Build Tool**  

---

## 🔑 What We Can Do Using Maven
1. 📂 Create initial project structure  
2. 📦 Download **project dependencies** automatically  
   - Example: Spring Boot, Hibernate, Kafka, Redis, Email, Log4j, JUnit, Security  
   - Add them in **`pom.xml`**  
   - Maven will download dependencies from repositories  
3. ⚙️ Compile project source code  
4. 🎁 Package Java projects as **JAR** / **WAR**  

---

## ⚙️ Maven Installation (Windows)

1. ☕ Install **Java (JDK + JRE)**  
   - [Download Java 8](https://www.oracle.com/in/java/technologies/javase/javase8-archive-downloads.html)  
   - Set `JAVA_HOME` → `C:\Program Files\Java\jdk1.8.0_202`  
   - Update `Path` → `C:\Program Files\Java\jdk1.8.0_202\bin`  
   - Verify:  
     ```bash
     java -version
     ```
2. 📥 Install **Maven**  
   - [Download Maven](https://maven.apache.org/download.cgi) → `apache-maven-3.8.5-bin.zip`  
   - Extract to `C:\apache-maven-3.8.5`  
   - Set `MAVEN_HOME` → `C:\apache-maven-3.8.5`  
   - Update `Path` → `C:\apache-maven-3.8.5\bin`  
   - Verify:  
     ```bash
     mvn -version
     ```

---

## 📘 Maven Terminology
- **📦 Archetype** → Project Type  
  - `maven-archetype-quickstart` → Standalone App  
  - `maven-archetype-webapp` → Web App  
- **🏢 groupId** → Company / Project Name  
- **📛 artifactId** → Project Module Name  
- **📂 packaging** → Output Type (`jar` / `war`)  
- **🔖 version** → Project Version (`SNAPSHOT` = Development, `RELEASE` = Completed)

---

## 📂 Creating Maven Standalone App
```bash
mvn archetype:generate   -DgroupId=in.codewithprth   -DartifactId=01-Maven-App   -DarchetypeArtifactId=maven-archetype-quickstart   -DinteractiveMode=false
```

**📁 Folder Structure**
```
01-Maven-App
 ├── src
 │   ├── main/java     # Application Source Code
 │   └── test/java     # Unit Test Code
 └── pom.xml           # Project Object Model
```

---

## 📦 Adding Dependencies
- 🔎 Find dependencies → [Maven Repository](https://mvnrepository.com)  
- Example: Spring Core  
```xml
<dependency>
  <groupId>org.springframework</groupId>
  <artifactId>spring-core</artifactId>
  <version>5.3.23</version>
</dependency>
```
- Compile project:
```bash
mvn compile
```

---

## 🌍 Maven Repositories
| Type | Description | Example |
|------|-------------|---------|
| 💻 **Local** | Stored in system (`C:\Users\<user>\.m2`) | Used first |
| 🌐 **Central** | Maintained by Apache | Default |
| 🏢 **Remote** | Maintained by companies | Nexus, JFrog |

🔹 If dependency not found in local, Maven checks **Central / Remote**.

---

## 🎯 Maven Goals
| Goal | Usage |
|------|-------|
| 🧹 `clean`   | Deletes `target` folder |
| ⚙️ `compile` | Compiles source code → `.class` files |
| 🧪 `test`    | Runs JUnit test cases |
| 📦 `package` | Creates JAR/WAR in `target` folder |
| 📥 `install` | Installs project as dependency in local repo |

👉 Syntax:
```bash
mvn <goal-name>
```

---

## 🌐 Creating Web App with Maven
```bash
mvn archetype:generate   -DarchetypeArtifactId=maven-archetype-webapp   -DgroupId=in.ashokit   -DartifactId=flipkart_app   -DinteractiveMode=false
```

---

## 🧩 Working with Maven in IDE (Eclipse/STS)
- IDEs have Maven plugin pre-installed  
- Create Standalone (Quickstart) or WebApp project directly  
- For Web Apps, add Servlet API dependency:
```xml
<dependency>
  <groupId>javax.servlet</groupId>
  <artifactId>javax.servlet-api</artifactId>
  <version>4.0.1</version>
  <scope>provided</scope>
</dependency>
```

---

## 🛑 Maven Exclusion Example
Remove unwanted child dependencies:
```xml
<dependency>
  <groupId>org.springframework</groupId>
  <artifactId>spring-context</artifactId>
  <version>5.3.23</version>
  <exclusions>
    <exclusion>
      <groupId>org.springframework</groupId>
      <artifactId>spring-aop</artifactId>
    </exclusion>
  </exclusions>
</dependency>
```

---

## 🏢 Maven Multi-Module Project
- Break project into modules (**Admin, Reports, Payments, Products...**)  
- Parent → **POM packaging**  
- Children → Modules  

**Parent `pom.xml`:**
```xml
<packaging>pom</packaging>
<modules>
  <module>ADMIN</module>
  <module>REPORTS</module>
</modules>
```

**Child `pom.xml`:**
```xml
<parent>
  <groupId>com.flipkart</groupId>
  <artifactId>Flipkart_App</artifactId>
  <version>0.0.1-SNAPSHOT</version>
</parent>
<artifactId>REPORTS</artifactId>
```

---

## 📌 Dependency Scopes
| Scope | Description |
|-------|-------------|
| ⚙️ **compile** | Default, available everywhere |
| 📦 **provided** | Provided by JDK/container (Ex: Servlet API) |
| ▶️ **runtime** | Needed only at runtime |
| 🧪 **test** | Used only for testing (JUnit, Mockito) |
| 💿 **system** | Similar to provided, but JAR must be supplied manually |
| 📋 **import** | Used in dependency management (type = pom) |

---

# ✅ Summary – What We Learned
1. 🔧 Build Tools & Why we need them  
2. 🏗️ Maven Overview  
3. ⚙️ Maven Installation (Windows)  
4. 📘 Maven Terminology  
5. 📂 Creating Standalone & Web Apps  
6. 📑 Working with `pom.xml`  
7. 📦 Adding Dependencies  
8. 🎯 Maven Goals  
9. 🌍 Maven Repositories  
10. 🏢 Remote Repository (Nexus, JFrog)  
11. 🛑 Exclusion in Maven  
12. 🏢 Multi-Module Project  
13. 📌 Dependency Scopes  

---
💡 With Maven, **Project Setup → Build → Dependency Management → Packaging** becomes **fully automated**!

---

# 🎤 Maven Interview Questions & Answers

## 1️⃣ What is Maven and why is it used?
**Answer:**  
Maven is a **build automation and dependency management tool** for Java projects.  
It simplifies project setup, builds, testing, and deployment by managing dependencies and providing a structured lifecycle.

---

## 2️⃣ What is `pom.xml` in Maven?
**Answer:**  
- **POM (Project Object Model)** is the heart of any Maven project.  
- It defines:  
  - Project details (groupId, artifactId, version)  
  - Dependencies  
  - Plugins  
  - Build configurations  

---

## 3️⃣ What are Maven Goals and Phases?
**Answer:**  
- **Goal** → A specific task (e.g., compile, test, package).  
- **Phase** → A sequence of goals in Maven lifecycle.  
- Example:  
  - `clean` → Removes previous build files  
  - `install` → Compiles, packages, and installs to local repo  

---

## 4️⃣ What is the difference between `compile`, `provided`, and `test` scope?
**Answer:**  
- **compile** → Available in all classpaths (default scope).  
- **provided** → Available at compile time but provided by container (e.g., Servlet API).  
- **test** → Only available in test classpath (JUnit, Mockito).  

---

## 5️⃣ What are Maven Repositories?
**Answer:**  
- **Local Repository** → Stored in user’s system (`.m2` folder).  
- **Central Repository** → Maintained by Apache, default for Maven.  
- **Remote Repository** → Maintained by organizations (e.g., Nexus, JFrog).  

---

## 6️⃣ What is the difference between Maven and Gradle?
**Answer:**  
| Feature        | Maven (XML) | Gradle (Groovy/Kotlin) |
|----------------|-------------|-------------------------|
| Configuration  | XML (pom.xml) | DSL scripts (build.gradle) |
| Performance    | Slower        | Faster with caching    |
| Flexibility    | Convention    | Highly customizable    |
| Usage          | Java projects | Java + Android         |

---

## 7️⃣ How does Maven handle transitive dependencies?
**Answer:**  
- If **A depends on B** and **B depends on C**, Maven automatically downloads C.  
- Developers don’t need to manage child dependencies manually.  

---

## 8️⃣ What is the difference between `snapshot` and `release` in Maven?
**Answer:**  
- **Snapshot** → Development version (`1.0-SNAPSHOT`) → Frequently updated.  
- **Release** → Stable version (`1.0-RELEASE`) → Fixed and not modified.  

---

## 9️⃣ What is the role of Maven Plugins?
**Answer:**  
Plugins extend Maven functionality. Example:  
- **Compiler Plugin** → Compiles Java code  
- **Surefire Plugin** → Runs unit tests  
- **Assembly Plugin** → Creates distributable formats (ZIP, TAR)  

---

## 🔟 How to skip test cases while building a Maven project?
**Answer:**  
Use:  
```bash
mvn install -DskipTests
```
👉 This compiles test classes but skips running them.

---

📌 **Pro Tip for Interviews:** Always highlight that Maven automates **dependency management + build lifecycle**, reducing manual efforts.


