# 项目结构
|-- .gradle
|-- .idea               // 这两项都是 Android 自动生成的, 不需要去关系
|-- app                 // app 是比较重要的, 后续开发都在这个目录中进行
|-- gradle              // 这个目录包含了 gradle wrapper 的配置文件,使用 gradle wrapper 的方式不需要提前将gradle下载好， 而是会自动根据本地的缓存情况决定是需要联网下载 gradle. Android 默认是没有启动 gradle wrapper 的方式.
|-- .gitignore          // git相关的
|-- build.gradle        // 这是项目的全局构建脚本, 通常这个文件夹的内容不需要修改.
|-- gradle.properties   // 这是全局的 gradle 配置文件，在这里配置的属性将影响到项目中所有的 gradle 编译脚本.
|-- gradlew
|-- gradlew.bat         // 这项用来在命令行中执行 gradle 命令的,其中 gradlew 是在 Linux 或 Mac系统， 后者是 Window 上.
|-- HelloWorld.iml      // iml 文件是所有 Intellij IDEA 项目都会生产的一个文件（Android Studio 是基于 IntelliJ 开发的）， 用于标识这是一个 IntelliJ IDEA 项目，我们不需要去更改它
|-- local.properties   // 这个文件用于指定本地 SDK的路径，通常是自动生成的， 我们并不需要去修改，除非你本地的SDK位置发生改变，那么就要将这个文件中的路径更换成新的地址
|-- settings.gradle    // 这个文件用于指定项目中所有引入的模块， 由于HelloWorld项目只有一个 app 模块， 因此该文件中只引入 app 这一个模块。 通常情况下模块的引入是自动完成的，需要我们手动去修改这个文件的场景可能比较少.
