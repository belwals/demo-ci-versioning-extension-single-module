# demo-ci-versioning-extension-single-module
``` 
Demo project to demostrate use of "ci-versioning-extension" plugin
```
### Steps for configuring project
 * Create a folder i.e. `.mvn` on the project home directory
 * Add a file by name `extensions.xml` with the below content to hookup plugin 
    ```
     <extensions xmlns="http://maven.apache.org/EXTENSIONS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                 xsi:schemaLocation="http://maven.apache.org/EXTENSIONS/1.0.0 https://maven.apache.org/xsd/core-extensions-1.0.0.xsd">
         <extension>
             <groupId>com.sab.maven</groupId>
             <artifactId>ci-versioning-extension</artifactId>
             <version>1.0.0</version>
         </extension>
     </extensions>
   
  * Once we are done with that step then, we need to follow some conventions on the project's POM file
     * Project version should use a placeholder version, and placeholder version should be read from the properties file
       like
       ```
        <groupId>com.sab.demo.ci.version</groupId>
        <artifactId>demo-ci-versioning-extension-single-module</artifactId>
        <version>${revision}</version>
       
       <properties>
          <revision>SNAPSHOT</revision>
          <encoding>UTF-8</encoding>
       </properties>
       
       ```
  * We are almost there in terms of Project configuration we need to run just code and build the project as usual, and plugin will take care to generate CI friendly version
    ```
    ~ mvn clean install
    ```
   
 ##### Points to remember
  * In case of no git repo initialize for the project there won't be any Version generation, so it will rely on value supplied on the properties in the POM.
  * If there is no commit on the project than automated generated version  will be `0.00000`