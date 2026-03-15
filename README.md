# Android TabLayout 标签页演示

## 简介

TabLayout 是 Material Design 标签页组件。

## 教程

```kotlin
tabLayout.addTab(tabLayout.newTab().setText("标签1"))
tabLayout.addOnTabSelectedListener(object : TabLayout.OnTabSelectedListener {
    override fun onTabSelected(tab: TabLayout.Tab?) { }
})
```
