---
title: Setup JDK, maven, Java Spring Boot app with IntelliJ Idea on Ubuntu / Linux
date: 2023-01-21 16:00
categories: [Java]
tags: [java, jdk]
render_with_liquid: false
---

This article will help you to setup JDK, maven, IntelliJ idea &amp; create a new Java Spring Boot app on Ubuntu / Linux
- Java Spring Boot source code can be found at: <https://github.com/abhishek-pradhan/java-spring-boot-initializer-demo> 

## Setup Java
- Install OpenJDK from <https://adoptium.net/> &amp; Download Linux tar file
  - Check your architecture version by running:
    ```terminal
    lscpu
    ```
    > If Architecture: x86_64, this means you are on x64

- Untar / unzip the file which extracts to jdk-17.0.6+10 folder:
  ```terminal
  tar -zxvf OpenJDK17U-jdk_x64_linux_hotspot_17.0.6_10.tar.gz
  ```

  ```terminal
  chmod +x jdk-17.0.6+10 
  ```

- Set JAVA_HOME &amp; PATH variables: 
  ```terminal
  vim ~/.bashrc
  ```

  ```terminal
  export JAVA_HOME=/home/abhi/Downloads/jdk-17.0.6+10 
  export PATH=${PATH}:${JAVA_HOME}/bin 
  ```
  {: file='.bashrc'}

  > Append these variables to .bashrc file, save and now reboot terminal &amp; run below java cmd to test setup

  ```terminal
  java --version
  ```
  > successfull output: 
    ```console
    openjdk 17.0.6 2023-01-17
    OpenJDK Runtime Environment Temurin-17.0.6+10 (build 17.0.6+10)
    OpenJDK 64-Bit Server VM Temurin-17.0.6+10 (build 17.0.6+10, mixed mode, sharing)
    ```

## Setup Maven
- Download maven from <https://maven.apache.org/download.cgi> as Binary tar.gz archive file: apache-maven-3.8.7-bin.tar.gz 

- Untar / unzip the file which extracts to apache-maven-3.8.7 folder:
  ```terminal
  tar -zxvf apache-maven-3.8.7-bin.tar.gz 
  ```
  ```terminal
  chmod +x apache-maven-3.8.7 
  ```

- Set M2_HOME &amp; PATH variables: 
  ```terminal
  vim ~/.bashrc 
  ```
  ```terminal
  export M2_HOME=/home/abhi/Downloads/apache-maven-3.8.7 
  export PATH=${PATH}:${M2_HOME}/bin
  ```
  {: file='.bashrc'}

  > Append these variables to .bashrc file, save and now reboot terminal &amp; run below mvn cmd to test setup

  ```terminal
  mvn --version
  ```
  > successfull output: 
    ```console
    Apache Maven 3.8.7 (b89d5959fcde851dcb1c8946a785a163f14e1e29)
    Maven home: /home/abhi/Downloads/apache-maven-3.8.7
    Java version: 17.0.6, vendor: Eclipse Adoptium, runtime: /home/abhi/Downloads/jdk-17.0.6+10
    Default locale: en_IN, platform encoding: UTF-8
    OS name: "linux", version: "5.15.0-57-generic", arch: "amd64", family: "unix"
    ```

## Setup IntelliJ Idea
- Download Community edition (free) from <https://www.jetbrains.com/idea/download/#section=linux> as ideaIC-2022.3.1.tar.gz 

- Untar / unzip the file which extracts to idea-IC-223.8214.52 folder: 
  ```terminal
  tar -zxvf ideaIC-2022.3.1.tar.gz 
  ```

- Run IntelliJ installer, which will give you a wizard to install IntelliJ &amp; run it: 
  ```terminal
  cd idea-IC-223.8214.52/bin
  ./idea.sh
  ```

- Enable IntelliJ Idea to run from terminal or desktop: Open Intellij IDE: Open Intellij IDE
  - create command-line runner: 'Tools' menu> Create Command-line Launcher
  - create a desktop entry, 'Tools' menu > Create Desktop Entry

## Create Java spring boot app
- Goto spring initlalizer: <https://start.spring.io/> &amp; download maven/jar project (demo.zip) as shown in below screenshot:
![spring initializer](/assets/img/posts/2023-01-21-setup-java-spring-boot-with-intellij-idea/spring-initializer.png)

- Unzip zip file &amp; open it with IntelliJ idea: 
  ```terminal
  unzip demo.zip
  cd demo
  idea . 
  ```
- Tell IntelliJ about your JDK &amp; maven paths (1 time setup):
  - Set JDK path: IntelliJ -> 'File' menu -> Project Structure -> Project (as shown below):
    ![intellij jdk setup](/assets/img/posts/2023-01-21-setup-java-spring-boot-with-intellij-idea/intellij-jdk-setup.png)
  - Set Maven home: IntelliJ -> 'File' menu -> Settings -> Build, Execution, Deployment -> Build Tools -> Maven(as shown below):
    ![intellij maven setup](/assets/img/posts/2023-01-21-setup-java-spring-boot-with-intellij-idea/intellij-maven-setup.png)

- Now run your spring boot app from IntelliJ IDE's by right-clicking on DemoApplication file &amp; selecting Run or from IDE terminal:
  ```terminal
  mvn spring-boot:run 
  ```

- This will compile &amp; run our spring boot app. Now open browser &amp; navigate to <http://localhost:8080/actuator> (see below): 
![intellij spring boot run](/assets/img/posts/2023-01-21-setup-java-spring-boot-with-intellij-idea/intellij-spring-boot-run.png)

> Note: JDK/maven/Intellij IDE versions may vary in future or you might be using a different distro of Linux, but this guide would still be valid.
{: .prompt-info }