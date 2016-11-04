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

####sublime的代码跳转
* 首先需要安装插件，下载地址<https://github.com/iTyran/quick-comminuty-dev/archive/master.zip>，这个是quick-community-dev是泰然网的quick社区版的sublime插件，通过简单的修改，我们一样可以使用；
* 打开 Sublime Text 中依次选择 Preferences ==> Browse Packages... ，此时将进入到Sublime Text的 Packages 目录下，将上面下载的插件解压到这个目录下；
* 在Sublime Text 中依次选择 Preferences ==> Package Settings ==> quick-community-dev ==> Setting-User，此时将自动创建一个文件，在文件中输入如下内容，并保存为 quick-comminuty-dev.sublime-settings：

		{
		    // must set the path
		    "quick_cocos2dx_root": "此处填入引擎所在路径",
		    // lua template attributes
		    "date_format": "%Y-%m-%d %H:%M:%S",
		    // i.e. peter or peter (peter@gmail.com)
		    "author": "此处填入你的名字",
		    // compile_scripts encrypt key,no encrypt when empty
		    "compile_scripts_key": ""
		} 
`quick_cocos2dx_root`该key对应的value需要填写，例如：`test/frameworks/cocos2d-x`;		
* 完成以上步骤，通过右键`Goto Definition`可以实现代码跳转；

####sublime启动模拟器
* 完成代码跳转后， 打开 Sublime Text 中依次选择 Preferences ==> Browse Packages... ，此时将进入到Sublime Text的 Packages 目录下，打开quick-comminuty-dev-master文件夹中的`quickx.py`；
* 跳转到方法`runWithPlayer`中，在`playerPath=""`下一行插入`arr=os.path.split(srcDir)`，然后将`elif sublime.platform()=="windows":`的下一行改为`playerPath=arr[0]+"/simulator/win32/test.exe"`，`test.exe`是新建工程通过visio studio生成的可执行文件；
* 另外还需要将`width=640`改成`width="640"`，`height=960`改成`height="960"`；
* 完成以上步骤，通过右键`Run With Player`可以启动模拟器，实现工程代码；

####sublime配置快捷键
* 在Sublime Text 中依次选择 Preferences ==> Package Settings ==> quick-community-dev ==> Key Bindings-User，此时将自动创建一个文件，在文件中输入如下内容，并保存：

		[
		    { "keys": ["ctrl+shift+g"], "command": "quickx_goto_definition" },
		    { "keys": ["ctrl+shift+r"], "command": "quickx_run_with_player_by_file" }
		]
* 完成上述配置，就可以通过快捷键，实现代码跳转和模拟器的启动；

####显示模拟器的log信息
* 通过vs2015打开工程，在`SimulatorWin.cpp`文件中，修改宏变量：

		#define SIMULATOR_WITH_CONSOLE_AND_MENU 1
		
* 运行工程，重新生成可执行文件，然后再启动模拟器，log文件也会同时弹出；






	
	