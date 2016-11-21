记录在使用smartsvn过程中解决的一些问题的方法。

####File has inconsistent newlines 解决方法
用SmartSVN提交代码的时候提示：svn: File has inconsistent newlines
这是由于要提交的文件编码时混合了windows和unix符号导致的。
解决方法是将其统一编码或者修改SmartSVN提交前的检查设置。
统一编码在这里就不介绍了，SmartSVN设置做如下修改可以解决问题：
点击 Project–>Setting，选择Working copy下的EOL-style，将Default EOL-style设置为 As is(no conversion)，并点击ok按钮，即可！
