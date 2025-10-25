# 键位编辑器 - Bumon42

这是为Bumon42键盘定制的ZMK配置，包含机器可读的布局和键位定义，用于配合@nickcoutsos的[keymap-editor](https://github.com/nickcoutsos/keymap-editor)工具使用。

![截图](./Bumon42_keymap.png)

# 使用方法

* 访问[keymap-editor](https://nickcoutsos.github.io/keymap-editor/)网页应用。
* 在`Source`下拉菜单中选择GitHub。
* 在仓库输入框中输入：`bumony/zmk-config`
* 在分支选择框中选择`main`。
* 根据需要修改键位映射。
  * 参考[zmk文档](https://zmk.dev/docs)了解各种[行为](https://zmk.dev/docs/behaviors/key-press)和[代码](https://zmk.dev/docs/codes)的描述。
* 对修改满意后，点击页面右下角的"Commit Changes"按钮。
* 等待几分钟（通常少于10分钟）来构建新的固件。页面右下角会有一个按钮供你下载固件。
* 下载固件并解压到某个位置。
* 将Bumon42连接到电脑，快速双击复位按钮。
  * 左侧LED应该闪烁蓝色，表示键盘处于引导加载程序模式。
  * 键盘应该作为新驱动器出现在你的系统中，名称为：`U disk`
* 以超级用户身份，将你从下载的zip文件中提取的`Bumon42-Bumon42-zmk.uf2`文件复制到`U disk`驱动器的根目录。
* 用Bumon42输入几个字母。现在应该使用更新后的键位映射了。

# 其他用户的使用方法

为了让keymap-editor正常工作，它需要对指向的github仓库具有写入权限。

如果你想为你的Bumon42键盘使用keymap-editor，但你不是此仓库的作者，请先fork此仓库，并将README中任何对`bumony`的引用替换为你自己的用户名。
