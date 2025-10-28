# キーマップエディター - Bumon42

これはBumon42キーボード用にカスタマイズされたZMK設定で、@nickcoutsosの[keymap-editor](https://github.com/nickcoutsos/keymap-editor)ツールと連携して使用するための機械可読レイアウトとキーマップ定義を含んでいます。

![スクリーンショット](./Bumon42_keymap.png)

# 使用方法

* [keymap-editor](https://nickcoutsos.github.io/keymap-editor/)ウェブアプリケーションにアクセスします。
* `Source`ドロップダウンメニューでGitHubを選択します。
* リポジトリ入力ボックスに以下を入力：`bumony/zmk-config`
* ブランチ選択ボックスで`main`を選択します。
* 必要に応じてキーマップを変更します。
  * 各種[ビヘイビア](https://zmk.dev/docs/behaviors/key-press)と[コード](https://zmk.dev/docs/codes)の説明については[zmkドキュメント](https://zmk.dev/docs)を参照してください。
* 変更に満足したら、ページ右下の「Commit Changes」ボタンをクリックします。
* 新しいファームウェアのビルドを数分待ちます（通常10分未満）。ページ右下にファームウェアをダウンロードするボタンが表示されます。
* ファームウェアをダウンロードして解凍します。
* Bumon42をコンピューターに接続し、リセットボタンを素早く2回クリックします。
  * 左側のLEDが青色に点滅し、キーボードがブートローダーモードであることを示します。
  * キーボードが`U disk`という名前の新しいドライブとしてシステムに表示されるはずです。
* スーパーユーザー権限で、ダウンロードしたzipファイルから抽出した`Bumon42-Bumon42-zmk.uf2`ファイルを`U disk`ドライブのルートディレクトリにコピーします。
* Bumon42でいくつかの文字を入力してみてください。更新されたキーマップが使用されているはずです。

# キーマップ設定説明

## レイヤー定義
- **DEF (0) - デフォルトレイヤー**：標準QWERTYレイアウト、基本文字、数字、記号を含む
- **GAM (1) - ゲームレイヤー**：数字キーレイアウト、ゲームと数字入力に適している
- **RSE (2) - リフトレイヤー**：ファンクションキー(F1-F12)と記号キー
- **LWR (3) - ロワーレイヤー**：特殊記号、メディアコントロール、ナビゲーションキー
- **ADJ (4) - アジャストレイヤー**：RGBバックライトコントロールとシステム機能
- **FN (5) - ファンクションレイヤー**：Bluetooth接続管理とシステムコントロール

## 主要機能
- **RGBバックライトコントロール**：WS2812 LEDストリップ対応、46個のLED
- **Bluetooth管理**：5つのBluetoothデバイス切り替え対応
- **エンコーダー対応**：EC11エンコーダー、グローバルトリガー対応
- **バッテリー監視**：電圧分圧器バッテリー監視
- **外部電源コントロール**：外部電源管理対応
- **OLED表示**：オプションOLEDディスプレイ対応

## 詳細キーマップ設定

### デフォルトレイヤー (DEF) - 標準QWERTYレイアウト
```
ESC  Q  W  E  R  T     Y  U  I  O  P  BSPC
TAB  A  S  D  F  G     H  J  K  L  ENTER
LSHFT Z  X  C  V  B     N  M  .  ↑  RSHIFT
LCTRL LALT LWIN [LWR] [RSE] [LWR] ← [FN] ↓ →
```

**特殊キー説明：**
- **TABキー**：`&mt LCTRL TAB` - クリックはTAB、長押しは左Ctrl
- **ESCキー**：`&lt 3 ESC` - クリックはESC、長押しでロワーレイヤー(3)をアクティブ
- **スペースキー**：左スペースでロワーレイヤー(3)、右スペースでリフトレイヤー(2)をアクティブ
- **方向キー**：左下角の方向キーはFNレイヤー(6)を長押ししてアクティブ
- **右Shift**：`&lt 4 RSHIFT` - クリックは右Shift、長押しでアジャストレイヤー(4)をアクティブ

### ゲームレイヤー (GAM) - 数字キーレイアウト
```
`  1  2  3  4  5     6  7  8  9  0  DEL
CAPS 4  5  6  F  =     ←  ↑  ↓  →  ENTER
MO5  7  8  9  0  B     N  ,  .  /  RSHIFT
LCTRL [DEF]0 .  SPACE = [LWR] PRINT RCTRL
```

**特殊機能：**
- **数字キー**：完全な数字キーパッドレイアウト
- **方向キー**：直接使用可能な方向キー
- **MO5**：長押しでファンクションレイヤー(5)をアクティブ

### リフトレイヤー (RSE) - ファンクションキーと記号
```
`  F1 F2 F3 F4 F5     F6 =  -  [  ]  DEL
CAPS F4 F5 F6 F  [     ]  J  ;  '  ENTER
LSHFT F7 F8 F9 F10 F11 F12 ,  .  /  RSHFT
     [TO5] [ADJ]= RALT PRINT RCTRL
```

**機能説明：**
- **F1-F12**：完全なファンクションキー
- **記号キー**：角括弧、セミコロン、引用符など
- **TO5**：ファンクションレイヤー(5)に切り替え
- **ADJ**：アジャストレイヤー(4)をアクティブ

### ロワーレイヤー (LWR) - 特殊記号とメディアコントロール
```
    !  @  #  $  %  ^  &  *  {  }  MENU
    $  %  ^         -  =  ;  '  |
LSHFT &  *  (  )         VOL- VOL+ PGUP END
      _  -  HOME PGDN END
```

**メディアコントロール：**
- **VOL-/VOL+**：音量コントロール
- **PGUP/PGDN**：ページ上下
- **HOME/END**：行頭行末
- **特殊記号**：!@#$%^&*()など

### アジャストレイヤー (ADJ) - RGBとシステムコントロール
```
POWER !  @  #  $  %  ^  &  *  {  }
     RGB_HUI RGB_SAI RGB_BRI RGB_SPI RGB_EFF HOME   :  |
     RGB_HUD RGB_SAD RGB_BRD RGB_SPD RGB_EFR   <  >  ?
     RGB_TOG
```

**RGBコントロール：**
- **RGB_HUI/HUD**：色相増加/減少
- **RGB_SAI/SAD**：彩度増加/減少
- **RGB_BRI/BRD**：明度増加/減少
- **RGB_SPI/SPD**：速度増加/減少
- **RGB_EFF/EFR**：エフェクト切り替え
- **RGB_TOG**：RGBオン/オフ

### ファンクションレイヤー (FN) - Bluetoothとシステム管理
```
BT_CLR BT0 BT1 BT2 BT3 BT4 F6 F7 F8 F9 F10 BOOT
BT_CLR BT_CLR BT_CLR BT_CLR BT_CLR BT_CLR     SYS_RESET
       HOME END PGUP PGDN        OUT_TOG BOOT
[DEF] OUT_USB     RGB_TOG RGB_TOG RALT
```

**Bluetooth管理：**
- **BT_SEL 0-4**：Bluetoothデバイス0-4を選択
- **BT_CLR**：Bluetooth接続をクリア
- **OUT_TOG**：出力切り替え
- **OUT_USB**：USB出力
- **SYS_RESET**：システムリセット
- **BOOT**：ブートモードに入る

## 修飾キービヘイビア詳細
- **&mt LCTRL TAB**：クリックはTAB、長押しは左Ctrl
- **&lt 3 ESC**：クリックはESC、長押しでロワーレイヤーをアクティブ
- **&lt 4 RSHIFT**：右Shiftクリック、長押しでアジャストレイヤーをアクティブ
- **&mo 5**：長押しでファンクションレイヤーをアクティブ、離すと戻る
- **&to 0**：デフォルトレイヤーに切り替え
- **&trans**：透明キー、下層に渡す

# 他のユーザーの使用方法

keymap-editorが正常に動作するためには、指定されたGitHubリポジトリへの書き込み権限が必要です。

Bumon42キーボードでkeymap-editorを使用したいが、このリポジトリの作者ではない場合は、まずこのリポジトリをフォークし、README内の`bumony`への参照をすべて自分のユーザー名に置き換えてください。