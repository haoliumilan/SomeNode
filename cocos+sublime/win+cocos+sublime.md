在windows环境下，通过sublime text来开发cocos+lua工程；    

* 环境是win7；
* 编辑器使用的是sublime text 3，不破解也可使用；
* cocos引擎使用最新版本，cocos2d-x-3.13.1；
* 需要安装python，版本为2.7.10；
* 需要安装visio studio来生成模拟器，使用comunity 2015版本；

####使用sublime的原因
* 可以启动模拟器，直接查看效果；
* 可以实现方法跳转，查看函数方法的定义；
* 相比vs，编辑器更轻便，操作流畅，使用顺手；

####cocos引擎的配置
* cocos最新版本下载地址：<http://www.cocos.com/download>;
* 下载到本地后，通过cmd，运行setup.py

		$python cocos2d-x-3.13.1/setup.py
		
	会提示Android NDK、SDK等相关路径填写，可以先回车跳过，引擎就安装成功了；
* 通过cmd来创建cocos+lua工程：

		$cocos new -d [目标路径] -l lua [工程名称]
		
* 通过vs2015打开新创建的工程，编译运行，在工程目录下的`simulator/win32/`中生成.exe文件，项目开发的时候，sublime启动的就是这个可执行文件；

####sublime的插件安装
* 下载地址<https://github.com/haoliumilan/quick-comminuty-dev/archive/master.zip>，这个是泰然网的quick社区版的sublime插件，通过简单的修改，我们一样可以使用；
* 打开 Sublime Text 中依次选择`Sublime Text ==> Preferences ==> Browse Packages...`，此时将进入到Sublime Text的 Packages 目录下，将上面下载的插件解压到这个目录下；

####sublime启动模拟器
* 通过右键`Run With Player`可以启动模拟器，实现工程代码；

####sublime代码跳转
* 选中某个变量，通过右键`Goto Definition`可以启动模拟器，实现工程代码；
* 打开一个新的工程，必须要先使用`Run With Player`（这个方法可以确认工程目录路径）之后，才能使用` Goto Definition`；

####sublime配置快捷键
* 在Sublime Text 中依次选择`Sublime Text ==> Package Settings ==> quick-community-dev ==> Key Bindings-User`，此时将自动创建一个文件，在文件中输入如下内容，并保存：

		[
		    { "keys": ["ctrl+shift+g"], "command": "quickx_goto_definition" },
		    { "keys": ["ctrl+shift+r"], "command": "quickx_run_with_player_by_file" }
		]
* 完成上述配置，就可以通过快捷键，实现代码跳转和模拟器的启动；

####显示模拟器的log信息
* 通过vs2015打开工程，在`SimulatorWin.cpp`文件中，修改宏变量：

		#define SIMULATOR_WITH_CONSOLE_AND_MENU 1
		
* 运行工程，重新生成可执行文件，然后再启动模拟器，log文件也会同时弹出；






	
	