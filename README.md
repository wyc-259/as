# Android 应用开发实验报告

## 实验一：创建第一个 Android 工程并同步至 GitHub

| 项目 | 内容 |
| --- | --- |
| 姓名 | 翁玉宸 |
| 学号 | 121052024030 |
| 班级 | 软工一班 |
| 实验日期 | 2026-09-14 |
| 仓库地址 | https://github.com/wyc-259/as |

---

## 一、实验目的

1. 掌握 Android Studio 的安装与基本配置，熟悉开发环境的搭建流程。
2. 学会使用 Android Studio 创建一个完整的 Android 工程，理解工程的基本目录结构。
3. 掌握使用 Git 进行版本管理，并能够将本地工程同步（推送）到 GitHub 远程仓库。

---

## 二、实验环境

| 类别 | 配置 |
| --- | --- |
| 操作系统 | Windows 11 |
| 开发工具 | Android Studio |
| 编程语言 | Kotlin |
| 构建工具 | Gradle 9.5.0（Kotlin DSL） |
| Android Gradle Plugin | 9.3.0 |
| 版本控制 | Git + GitHub |
| 远程仓库 | https://github.com/wyc-259/as.git |

---

## 三、实验内容

### 3.1 创建 Android 工程

在 Android Studio 中选择 **Empty Views Activity** 模板，创建一个全新的 Android 工程，主要配置如下：

- 工程名称：`My Application`
- 应用包名：`com.example.myapplication`
- 语言：Kotlin
- 最低支持版本：`minSdk = 24`（Android 7.0）
- 目标版本：`targetSdk = 37`
- 编译版本：`compileSdk = 37`
- Java 版本：Java 11

### 3.2 工程目录结构

```
as/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/com/example/myapplication/
│   │   │   │   └── MainActivity.kt          # 主活动
│   │   │   ├── res/
│   │   │   │   ├── layout/activity_main.xml  # 主布局
│   │   │   │   ├── values/                   # 字符串、颜色、主题等资源
│   │   │   │   └── ...
│   │   │   └── AndroidManifest.xml           # 应用清单文件
│   │   ├── test/                             # 单元测试
│   │   └── androidTest/                      # 仪器化测试
│   └── build.gradle.kts                      # 模块级构建脚本
├── gradle/
│   ├── wrapper/                              # Gradle Wrapper
│   └── libs.versions.toml                    # 版本目录（依赖管理）
├── build.gradle.kts                          # 工程级构建脚本
├── settings.gradle.kts                       # 工程设置
├── gradle.properties
└── .gitignore
```

### 3.3 主要代码

`MainActivity.kt` 继承自 `AppCompatActivity`，通过 `enableEdgeToEdge()` 实现边缘到边缘显示，并设置布局为 `activity_main`：

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main)) { v, insets ->
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)
            insets
        }
    }
}
```

`activity_main.xml` 使用 `ConstraintLayout` 布局，居中显示一个 "Hello World!" 的文本：

```xml
<androidx.constraintlayout.widget.ConstraintLayout ...>
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        ... />
</androidx.constraintlayout.widget.ConstraintLayout>
```

### 3.4 同步工程至 GitHub

1. 初始化本地 Git 仓库并提交代码。
2. 在 GitHub 上创建远程仓库 `as`。
3. 将本地仓库的远程地址指向 GitHub：

   ```bash
   git remote add origin https://github.com/wyc-259/as.git
   ```

4. 推送本地代码到远程仓库：

   ```bash
   git push -u origin main
   ```

---

## 四、实验结果

- 工程创建成功，可正常编译运行，界面显示 "Hello World!"。
- 本地工程成功推送至 GitHub 远程仓库，仓库地址：<https://github.com/wyc-259/as.git>。

---

## 五、实验总结

通过本次实验，完成了第一个 Android 工程的创建，熟悉了 Android Studio 的项目结构（`app` 模块、`res` 资源目录、`AndroidManifest.xml` 清单文件、Gradle 构建脚本等），并掌握了使用 Git 将本地工程同步到 GitHub 远程仓库的完整流程，为后续 Android 应用开发的学习打下了基础。
