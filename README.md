# TinkerDemo

设置配置

	1.使用 gradle/app/tasks/build/assembleDebug 来build apk

	2.将在项目app/build/bakApk中生成好的apk信息赋值到build.gradle 的ext文件的几个路径下

	3.再使用 gradle/TinkerDemo/tasks/tinker/tinkerPatchDebug生成补丁包

	4.在build/outputs/apk/tinkerPatch中可以查看到补丁包patch_signed_7zip.apk

	5.在应用Load 补丁包后，需要kill进程，再重启才能加载


Error集合

	1.设置 TINKER_ID 错误

	解决方法一：

		在build.gradle的ext设置TINKER_ID 且TINKER_ID最好设置成versionCode值

	解决办法二：

		build.gradle中是通过

		def gitSha() {

				try {

						String gitRev = 'git rev-parse --short HEAD'.execute(null, project.rootDir).text.trim()

						if (gitRev == null) {

								throw new GradleException("can't get git rev, you should add git to system path or just input test value, such as 'testTinkerId'")

						}

						return gitRev

				} catch (Exception e) {

						throw new GradleException("can't get git rev, you should add git to system path or just input test value, such as 'testTinkerId'")

				}

		}

		来设置的，这个是需要建立git工程才能获取到值的，所以将工程放到github中，再clone下来，再运行就可以了
