使用该工具修改ro.属性的前提：
1. adb shell 拥有root权限，或者 adb shell su 以后可以拥有root权限;
2. 1中获取的shell 其 selinux domain为permissive domain，如 u:r:su:s0 或者 其他可以ptrace init进程且有设置ro.xx目标属性selinux权限的domain。

用法：
adb push .\libs\armeabi-v7a\mprop /data/local/tmp/
adb shell "chmod 755 /data/local/tmp/mprop"

# 修改init进程中的ro属性判断逻辑
adb shell "/data/local/tmp/mprop"

# 之后就可以修改任意ro属性了，如
adb shell "setprop ro.debuggable 1"

# 恢复init默认逻辑，之后就无法再修改ro属性了
adb shell "/data/local/tmp/mprop -r"


偶尔看到注册年份，07年，额... 感觉都老了，时不时得冒个泡，回来看看

21年小改了一行 （ perms[2] == '-'  ），当时仅仅为了测试Android新版本，老机器都扔了，不考虑兼容。



纯转载，记录一下。
