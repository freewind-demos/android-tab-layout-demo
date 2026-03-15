# Android TabLayout 标签页演示

## 简介

本 Demo 演示 TabLayout 的基本用法，展示如何创建标签页导航。

## 基本原理

TabLayout 是 Material Design 提供的标签页组件，通常与 ViewPager 配合使用，实现页面切换效果。

核心功能：
- 水平标签页显示
- 支持图标和文字组合
- 与 ViewPager 联动
- 点击和滑动切换

## 启动和使用

### 环境要求
- Android Studio
- JDK 17
- Gradle 8.x
- Material Components 库

### 安装和运行

1. 用 Android Studio 打开项目
2. 连接 Android 设备或模拟器
3. 点击 Run 运行

### 使用方法
- 左右滑动或点击标签切换

## 教程

### 什么是 TabLayout？

TabLayout 是 Material Design 组件，提供了水平标签页的展示和交互功能。它通常用于实现顶部导航，如新闻客户端的分类切换。

### 基本用法

1. 添加 TabLayout：

```xml
<com.google.android.material.tabs.TabLayout
    android:id="@+id/tabLayout"
    android:layout_width="match_parent"
    android:layout_height="wrap_content" />
```

2. 动态添加标签：

```kotlin
val tabLayout = findViewById<TabLayout>(R.id.tabLayout)
tabLayout.addTab(tabLayout.newTab().setText("标签1"))
tabLayout.addTab(tabLayout.newTab().setText("标签2"))
```

3. 设置监听器：

```kotlin
tabLayout.addOnTabSelectedListener(object : TabLayout.OnTabSelectedListener {
    override fun onTabSelected(tab: TabLayout.Tab?) {
        // 选中时
    }
    override fun onTabUnselected(tab: TabLayout.Tab?) {
        // 取消选中时
    }
    override fun onTabReselected(tab: TabLayout.Tab?) {
        // 再次点击时
    }
})
```

### 与 ViewPager 配合

```kotlin
val viewPager = findViewById<ViewPager>(R.id.viewPager)
viewPager.adapter = PagerAdapter()

// 使用 TabLayoutMediator 连接
TabLayoutMediator(tabLayout, viewPager) { tab, position ->
    tab.text = "标签${position + 1}"
}.attach()
```

## 关键代码详解

### MainActivity.kt

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // 1. 获取 TabLayout 组件
        val tabLayout = findViewById<TabLayout>(R.id.tabLayout)

        // 2. 动态添加标签
        // newTab() 创建新标签，setText() 设置显示文本
        tabLayout.addTab(tabLayout.newTab().setText("标签1"))
        tabLayout.addTab(tabLayout.newTab().setText("标签2"))
        tabLayout.addTab(tabLayout.newTab().setText("标签3"))

        // 3. 设置标签选择监听器
        tabLayout.addOnTabSelectedListener(object : TabLayout.OnTabSelectedListener {
            // 选中标签时调用
            override fun onTabSelected(tab: TabLayout.Tab?) {
                // 处理标签选中
            }

            // 取消选中时调用
            override fun onTabUnselected(tab: TabLayout.Tab?) {
                // 处理标签取消选中
            }

            // 再次点击已选中标签时调用
            override fun onTabReselected(tab: TabLayout.Tab?) {
                // 处理标签重新选中
            }
        })
    }
}
```

### activity_main.xml

```xml
<!-- 根布局：垂直线性布局 -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <!-- TabLayout 标签页组件 -->
    <com.google.android.material.tabs.TabLayout
        android:id="@+id/tabLayout"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />

    <!-- 内容区域 -->
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="TabLayout 标签页演示"
        android:gravity="center"
        android:padding="32dp" />
</LinearLayout>
```
