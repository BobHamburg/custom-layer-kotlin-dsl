This repository showcases how the `includeProjectDependencies()` clause does not exist for Spring Boot Gradle plugin
using the Kotlin DSL for Gradle in the `bootJar/layered/dependencies`

[According to Spring Boot Gradle plugin documentation on Custom Layers configuration](https://docs.spring.io/spring-boot/docs/current/gradle-plugin/reference/htmlsingle/#packaging-executable.configuring.layered-archives.configuration),

> The intoLayer closure claims content using nested include and exclude calls. The application closure uses Ant-style path matching for include/exclude parameters. The dependencies section uses group:artifact[:version] patterns. It also provides includeProjectDependencies() and excludeProjectDependencies() methods that can be used to include or exclude project dependencies.

However, when you try to use it in this repository `build.gradle.kts` file, you get the following error
> build.gradle.kts:28:17: Unresolved reference: includeProjectDependencies

Looking at the source code of the Spring Boot Gradle plugin, it seems that the `includeProjectDependencies()` is [present 
in the provided examples for Groovy build.gradle](https://github.com/spring-projects/spring-boot/blob/main/spring-boot-project/spring-boot-tools/spring-boot-gradle-plugin/src/docs/gradle/packaging/boot-jar-layered-custom.gradle) 
and [absent in provided examples for Kotlin DSL build.gradle.kts](https://github.com/spring-projects/spring-boot/blob/main/spring-boot-project/spring-boot-tools/spring-boot-gradle-plugin/src/docs/gradle/packaging/boot-jar-layered-custom.gradle.kts).

Would it be possible to support this property in Kotlin DSL as well as it is now [the new standard for Gradle](https://blog.gradle.org/kotlin-dsl-is-now-the-default-for-new-gradle-builds)?