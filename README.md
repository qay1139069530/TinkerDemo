# TinkerDemo


1.使用 gradle/app/tasks/build/assembleDebug 来build apk
2.将在项目app/build/bakApk中生成好的apk信息赋值到build.gradle 的ext文件的几个路径下
3.再使用 gradle/TinkerDemo/tasks/tinker/tinkerPatchDebug生成补丁包
4.在build/outputs/apk/tinkerPatch中可以查看到补丁包patch_signed_7zip.apk

5.在应用Load 补丁包后，需要kill进程，再重启才能加载
