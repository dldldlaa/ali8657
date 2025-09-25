## 9.24 kotlin语法



### 新的属性和方法

添加拓展属性

```kotlin
class Quiz{
    val question1=Question<String>("zhangsan","lisi",Difficulty.EASY)
        val question2=Question<Boolean>("zhangsan",true,Difficulty.EASY)
            val question3=Question<Int>("zhangsan",20,Difficulty.EASY)
            
 companion object StudentProgress{
    val total:Int =10
    val answered:Int =3
}
    //progressText就是拓展属性
    val Quiz.StudentProgress.progressText:String
    get()="${answered} of ${total} answered"
```

拓展函数

```kotlin
fun Quiz.StudentProgress.printProgressBar(){
    repeat(Quiz.answered) { print("▓") }
    repeat(Quiz.total- Quiz.answered) {print('▒')}
    println()
    print(Quiz.progressText)
    
}
```

### 接口

```kotlin
//定义一个接口
interface ProgressPrintable {
//属性
    val progressText:String
    //函数
        fun printProgressBar()

}

//继承该接口
class Quiz :ProgressPrintable{
    //重写接口的属性
    override val progressText:String  
     get() = "${answered} of ${total} answered"
    
    //重写函数
    override fun printProgressBar(){
    repeat(Quiz.answered) { print("▓") }
    repeat(Quiz.total- Quiz.answered) {print('▒')}
    println()
    print(progressText)
    }
    
    val question1=Question<String>("zhangsan","lisi",Difficulty.EASY)
        val question2=Question<Boolean>("zhangsan",true,Difficulty.EASY)
            val question3=Question<Int>("zhangsan",20,Difficulty.EASY)
            
 companion object StudentProgress{
    val total:Int =10
    val answered:Int =3
}
    
}
```

### 作用域函数

```kotlin
// 可以使用it代替名称过长的属性名    
fun printQuit(){
        question1.let{
            println(it.answer)
            println(it.questionText)
        }
        
    }
```

## 克隆项目

```
1 下载git
2 高级设置->bin目录
3 克隆到指定的位置
git clone https://github.com/google-developer-training/basic-android-kotlin-compose-training-dice-roller.git
```

### 使用阿里云仓库

```kotlin
/*
 * Copyright (C) 2023 The Android Open Source Project
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *      https://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */

pluginManagement {
    repositories {
        maven { url = uri("https://maven.aliyun.com/repository/gradle-plugin") }
        maven { url = uri("https://maven.aliyun.com/repository/google") }
        maven { url = uri("https://maven.aliyun.com/repository/public") }
        gradlePluginPortal()
        google()
        mavenCentral()
    }
}

dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        maven { url = uri("https://maven.aliyun.com/repository/google") }
        maven { url = uri("https://maven.aliyun.com/repository/public") }
        google()
        mavenCentral()
    }
}

rootProject.name = "basic-android-kotlin-compose-training-tip-calculator"
include(":app")

```



## Compose状态



