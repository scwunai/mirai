# Mirai
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/7d0ec3ea244b424f93a6f59038a9deeb)](https://www.codacy.com/manual/Him188/mirai?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=mamoe/mirai&amp;utm_campaign=Badge_Grade)  

Coroutine-based open-source multiplatform library of QQ protocol.  
Some of the protocol came from the other open-source projects.  

**The development is only for learning, DO NOT use it for illegal purposes.**

## UpdateLog
You can inspect supported protocols at [Project](https://github.com/mamoe/mirai/projects/1)  
and logs of updates at [UpdateLog](https://github.com/mamoe/mirai/blob/master/UpdateLog.md)

## Use as a library
You can install mirai as a library into your project.

Mirai is only published on `jcenter`, therefore please ensure you have the `jcenter()` repository in your `build.gradle`, like:
```kotlin
repositories{
  jcenter()
}
```

If your project is a multiplatform project, you should add dependencies for each platform respectively.  
If your project is not a multiplatform project, you just need to add the platform-specific dependency.  

`VERSION` should be replaced with the newest version, say [![Download](https://api.bintray.com/packages/him188moe/mirai/mirai-core/images/download.svg)](https://bintray.com/him188moe/mirai/mirai-core/)  
Mirai is still under experimental stage, it is suggested to keep the version newest.

**common**
```kotlin
implementation("net.mamoe:mirai-core-common:VERSION")
```
**jvm**
```kotlin
implementation("net.mamoe:mirai-core-jvm:VERSION")
```
**android**
```kotlin
implementation("net.mamoe:mirai-core-android:VERSION")
```

## Try

### On JVM or Android

Mirai is now available to work.

```kotlin
val bot = Bot(qqId, password).alsoLogin()
bot.subscribeMessages {
  "Hello" reply "World!"
  "profile" reply { sender.queryProfile() }
  contains("img"){ File(imagePath).send() }
}
bot.subscribeAlways<MemberPermissionChangedEvent> {
  if (it.kind == BECOME_OPERATOR)
    reply("${it.member.id} has become a operator")
}
```

1. Clone this GitHub project
2. Import as Gradle project
3. Run demo main functions: [mirai-demo](#mirai-demo)

## Contribution
Any kinds of contribution is welcomed. If you hold a interest in helping us implementing Mirai on JS, iOS or Native platforms, please email me `Him188@mamoe.net`
If you meet any problem or have any questions, be free to open a issue. Our goal is to make Mirai easy to use.

## Requirements

Kotlin 1.3.61  

On JVM: Java 6  
On Android: SDK 15

### Using java
Q: Can I use Mirai without Kotlin?  
A: Calling from java is not yet supported. Coroutines, extensions and inlines, which are difficult to use from Java, are generally used in Mirai. Therefore you should have the skill of Kotlin before you use Mirai.

#### Libraries used
Mirai uses these open-source libraries.

- [kotlin-stdlib](https://github.com/JetBrains/kotlin)
- [kotlinx-coroutines](https://github.com/Kotlin/kotlinx.coroutines)
- [kotlinx-io](https://github.com/Kotlin/kotlinx-io)
- [kotlin-reflect](https://github.com/JetBrains/kotlin)
- [pcap4j](https://github.com/kaitoy/pcap4j)
- [atomicfu](https://github.com/Kotlin/kotlinx.atomicfu)
- [ktor](https://github.com/ktorio/ktor)
- [klock](https://github.com/korlibs/klock)
- [tornadofx](https://github.com/edvin/tornadofx)
- [javafx](https://github.com/openjdk/jfx)
- [kotlinx-serialization](https://github.com/Kotlin/kotlinx.serialization)