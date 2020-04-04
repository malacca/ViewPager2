这是一个 `androidx.viewpager2:viewpager2` 的拷贝版本，以供 react-native 正常使用。

# 起因

1. 这来源于 RN 的一个万年 Bug (feature)，RN 为了提高性能，在 UIManager 接管了 requestLayout 导致动态更新可能无法重新渲染，参考 [issues 17968](https://github.com/facebook/react-native/issues/17968)、[stackoverflow](https://stackoverflow.com/questions/49371866/recyclerview-wont-update-child-until-i-scroll)，该 “feature” 并没有提供开关或者说提供的开关无效，这对于大部分情况是没什么影响的，很不幸，`viewpager2` 受到影响。

2. 更不幸的是 `viewpager2` 为 `final class`，所以无法通过继承修改内部重写内部函数。

# 方案

所以这里拷贝了一份 `androidx.viewpager2:viewpager2` 的副本，为避免引起冲突，同时修改了命名空间，除命名空间外，仅修改了 [这里](https://github.com/malacca/ViewPager2/commit/8d85bc2513c5f6646fa2693ff0abd85a554a7624)，强制 requestLayout 


# 备注

与 `viewpager2` 保持版本同步，当前为 `androidx.viewpager2:viewpager2:1.0.0` 的副本，源码获取路径

[文档](https://developer.android.com/jetpack/androidx/releases/viewpager2#1.0.0) -> [提交记录](https://android.googlesource.com/platform/frameworks/support/+log/743e7f1c517cfe59c2e2e4149c655888670508d4..c4c5f5340c2250ff0b4709448ca82abc915ef6b4/viewpager2) -> [分支](https://android.googlesource.com/platform/frameworks/support/+/c4c5f5340c2250ff0b4709448ca82abc915ef6b4) -> [源码](https://android.googlesource.com/platform/frameworks/support/+/c4c5f5340c2250ff0b4709448ca82abc915ef6b4/viewpager2/)

# 使用

```
dependencies {
    implementation "com.github.malacca:ViewPager2:1.0.0"
}
```