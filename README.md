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

# 键位配置说明

## 层定义
- **DEF (0) - 默认层**：标准QWERTY布局，包含基础字母、数字和符号
- **GAM (1) - 游戏层**：数字键布局，适合游戏和数字输入
- **RSE (2) - 提升层**：功能键(F1-F12)和符号键
- **LWR (3) - 降低层**：特殊符号、媒体控制和导航键
- **ADJ (4) - 调整层**：RGB背光控制和系统功能
- **FN (5) - 功能层**：蓝牙连接管理和系统控制

## 主要功能
- **RGB背光控制**：支持WS2812 LED灯带，46个LED
- **蓝牙管理**：支持5个蓝牙设备切换
- **编码器支持**：EC11编码器，支持全局触发
- **电池监控**：电压分压器电池监控
- **外部电源控制**：支持外部电源管理
- **OLED显示**：可选OLED显示屏支持

## 详细键位配置

### 默认层 (DEF) - 标准QWERTY布局
```
ESC  Q  W  E  R  T     Y  U  I  O  P  BSPC
TAB  A  S  D  F  G     H  J  K  L  ENTER
LSHFT Z  X  C  V  B     N  M  .  ↑  RSHIFT
LCTRL LALT LWIN [LWR] [RSE] [LWR] ← [FN] ↓ →
```

**特殊键位说明：**
- **TAB键**：`&mt LCTRL TAB` - 点击是TAB，按住是左Ctrl
- **ESC键**：`&lt 3 ESC` - 点击是ESC，按住激活降低层(3)
- **空格键**：左空格激活降低层(3)，右空格激活提升层(2)
- **方向键**：左下角方向键需要按住FN层(6)激活
- **右Shift**：`&lt 4 RSHIFT` - 点击是右Shift，按住激活调整层(4)

### 游戏层 (GAM) - 数字键布局
```
`  1  2  3  4  5     6  7  8  9  0  DEL
CAPS 4  5  6  F  =     ←  ↑  ↓  →  ENTER
MO5  7  8  9  0  B     N  ,  .  /  RSHIFT
LCTRL [DEF]0 .  SPACE = [LWR] PRINT RCTRL
```

**特殊功能：**
- **数字键**：完整的数字键盘布局
- **方向键**：直接可用的方向键
- **MO5**：按住激活功能层(5)

### 提升层 (RSE) - 功能键和符号
```
`  F1 F2 F3 F4 F5     F6 =  -  [  ]  DEL
CAPS F4 F5 F6 F  [     ]  J  ;  '  ENTER
LSHFT F7 F8 F9 F10 F11 F12 ,  .  /  RSHFT
     [TO5] [ADJ]= RALT PRINT RCTRL
```

**功能说明：**
- **F1-F12**：完整的功能键
- **符号键**：方括号、分号、引号等
- **TO5**：切换到功能层(5)
- **ADJ**：激活调整层(4)

### 降低层 (LWR) - 特殊符号和媒体控制
```
    !  @  #  $  %  ^  &  *  {  }  MENU
    $  %  ^         -  =  ;  '  |
LSHFT &  *  (  )         VOL- VOL+ PGUP END
      _  -  HOME PGDN END
```

**媒体控制：**
- **VOL-/VOL+**：音量控制
- **PGUP/PGDN**：页面上下
- **HOME/END**：行首行尾
- **特殊符号**：!@#$%^&*()等

### 调整层 (ADJ) - RGB和系统控制
```
POWER !  @  #  $  %  ^  &  *  {  }
     RGB_HUI RGB_SAI RGB_BRI RGB_SPI RGB_EFF HOME   :  |
     RGB_HUD RGB_SAD RGB_BRD RGB_SPD RGB_EFR   <  >  ?
     RGB_TOG
```

**RGB控制：**
- **RGB_HUI/HUD**：色相增加/减少
- **RGB_SAI/SAD**：饱和度增加/减少
- **RGB_BRI/BRD**：亮度增加/减少
- **RGB_SPI/SPD**：速度增加/减少
- **RGB_EFF/EFR**：效果切换
- **RGB_TOG**：RGB开关

### 功能层 (FN) - 蓝牙和系统管理
```
BT_CLR BT0 BT1 BT2 BT3 BT4 F6 F7 F8 F9 F10 BOOT
BT_CLR BT_CLR BT_CLR BT_CLR BT_CLR BT_CLR     SYS_RESET
       HOME END PGUP PGDN        OUT_TOG BOOT
[DEF] OUT_USB     RGB_TOG RGB_TOG RALT
```

**蓝牙管理：**
- **BT_SEL 0-4**：选择蓝牙设备0-4
- **BT_CLR**：清除蓝牙连接
- **OUT_TOG**：输出切换
- **OUT_USB**：USB输出
- **SYS_RESET**：系统重置
- **BOOT**：进入引导模式

## 修饰键行为详解
- **&mt LCTRL TAB**：点击TAB，按住是左Ctrl
- **&lt 3 ESC**：点击ESC，按住激活降低层
- **&lt 4 RSHIFT**：点击右Shift，按住激活调整层
- **&mo 5**：按住激活功能层，松开返回
- **&to 0**：切换到默认层
- **&trans**：透明键，传递到下层

# 其他用户的使用方法

为了让keymap-editor正常工作，它需要对指向的github仓库具有写入权限。

如果你想为你的Bumon42键盘使用keymap-editor，但你不是此仓库的作者，请先fork此仓库，并将README中任何对`bumony`的引用替换为你自己的用户名。
