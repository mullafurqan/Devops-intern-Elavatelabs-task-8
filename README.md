TASK 8: Run a Simple Java Maven Build Job in Jenkins



------------------------------------------------------------

🎯 OBJECTIVE

------------------------------------------------------------

Use Jenkins to build a simple Java application with Maven.  

Learn basic CI/CD concepts: compiling code, automating builds, and reading Jenkins output.



------------------------------------------------------------

🧰 TOOLS REQUIRED

------------------------------------------------------------

\- Jenkins (local or Docker)

\- Java JDK 8 or 11

\- Maven

\- Git (optional)



------------------------------------------------------------

📁 PROJECT STRUCTURE

------------------------------------------------------------

hello-java-maven/

&nbsp;├── pom.xml

&nbsp;└── src/

&nbsp;    └── main/

&nbsp;        └── java/

&nbsp;            └── HelloWorld.java



------------------------------------------------------------

💻 SOURCE CODE

------------------------------------------------------------

File: src/main/java/HelloWorld.java

------------------------------------------------------------

package com.example;

public class HelloWorld {

&nbsp;   public static void main(String\[] args) {

&nbsp;       System.out.println("Hello Jenkins + Maven Build Job!");

&nbsp;   }

}



------------------------------------------------------------

File: pom.xml

------------------------------------------------------------

<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0"

&nbsp;        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

&nbsp;        xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 

&nbsp;                            http://maven.apache.org/xsd/maven-4.0.0.xsd">

&nbsp;   <modelVersion>4.0.0</modelVersion>

&nbsp;   <groupId>com.example</groupId>

&nbsp;   <artifactId>hello</artifactId>

&nbsp;   <version>1.0-SNAPSHOT</version>

&nbsp;   <build>

&nbsp;       <plugins>

&nbsp;           <plugin>

&nbsp;               <groupId>org.apache.maven.plugins</groupId>

&nbsp;               <artifactId>maven-compiler-plugin</artifactId>

&nbsp;               <version>3.8.1</version>

&nbsp;               <configuration>

&nbsp;                   <source>1.8</source>

&nbsp;                   <target>1.8</target>

&nbsp;               </configuration>

&nbsp;           </plugin>

&nbsp;       </plugins>

&nbsp;   </build>

</project>



------------------------------------------------------------

⚙️ STEP-BY-STEP EXECUTION

------------------------------------------------------------



Step 1: Install Java and Maven

1\. Download and install JDK 8 or 11.

2\. Download and install Apache Maven.

3\. Add both to PATH.

4\. Verify installation:

&nbsp;  java -version

&nbsp;  mvn -version



Step 2: Create the Project

mkdir hello-java-maven

cd hello-java-maven

mkdir -p src/main/java

Create HelloWorld.java and pom.xml as above.



Step 3: Test the Build Locally

Run:

mvn clean package

Expected Output:

\[INFO] BUILD SUCCESS



Step 4: Start Jenkins

Option 1 — If installed locally:

Run Jenkins service and open http://localhost:8080



Option 2 — Using Docker:

docker run --name jenkins-lts -p 8080:8080 -p 50000:50000 -v jenkins\_home:/var/jenkins\_home jenkins/jenkins:lts



Wait for Jenkins to start and open http://localhost:8080



Step 5: Configure Jenkins Tools

1\. Go to Manage Jenkins → Global Tool Configuration

2\. Under Maven → Add Maven → Name: Maven-3.8.6

&nbsp;  Check “Install automatically”

3\. Under JDK → Add Java 11 if needed



Step 6: Create a Jenkins Job

1\. Click “New Item” → “Freestyle Project” → name it hello-java-maven → OK

2\. Source Code Management: None (local build)

3\. Build → Add build step → Invoke top-level Maven targets

4\. Goals: clean package

5\. Maven Version: Maven-3.8.6

6\. Save



Step 7: Run the Build

Click “Build Now”

Check “Console Output”

You should see:

\[INFO] Compiling 1 source file...

\[INFO] BUILD SUCCESS



Step 8: Verify the Output JAR

The compiled JAR will be in:

target/hello-1.0-SNAPSHOT.jar



Run it manually:

java -cp target/hello-1.0-SNAPSHOT.jar com.example.HelloWorld

Output:

Hello Jenkins + Maven Build Job!



Step 9: Deliverables

✅ Screenshot of Jenkins showing BUILD SUCCESS

✅ Project files (HelloWorld.java, pom.xml)

✅ README (this guide)



------------------------------------------------------------

📘 OUTCOME

------------------------------------------------------------

You learned:

\- How Jenkins automates Maven builds

\- How to configure Maven in Jenkins

\- How to run and verify Jenkins jobs

\- How to interpret Jenkins console logs



------------------------------------------------------------

👨‍💻 AUTHOR INFO

------------------------------------------------------------

Author: Your Name

Task: DevOps Task 08 — Jenkins + Maven

Date: 2025



