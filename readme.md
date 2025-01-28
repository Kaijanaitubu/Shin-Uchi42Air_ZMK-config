# 真打42Air ZMK-CONFIG

## このリポジトリは何？

このリポジトリには、[ZMK firmware](https://zmk.dev)をビルドするために必要な設定ファイルが含まれています。  

「真打42Air」キーボード向けに最適化された設定がプリセットされています。

---

## キーマップ変更の方法

### 1. ZMK Studioを利用する

「真打42Air」のデフォルトファームウェアは、[リマップツール「ZMK Studio」](https://zmk.studio) に対応しています。  

ZMK Studioは、Webブラウザから、またはネイティブアプリとして利用可能なリアルタイムリマップツールです。

ただし、現在ZMK Studioは開発中であり、一部機能に制限があります。現在利用可能な機能については、[ZMK公式ドキュメント/ZMK Studio](https://zmk.dev/docs/features/studio)をご確認ください。

なお、デフォルトのファームウェアはZMK Studioで編集できない一部の機能を使用しています。以下の機能を変更する場合は、別の方法をご利用ください。

#### デフォルトキーマップに利用していて、ZMK Studioでは現在変更不可の機能（2025/1/28現在）

- **Combo(コンボ)**  
  Tabキー、Shift+Tab、Bluetoothプロファイルの削除操作に利用されています。
- **Conditional Layers(条件付きレイヤー)**  
  非テンキーモードの実装に利用されています。
  - 空のレイヤー（レイヤー4）と、記号・数字レイヤー（レイヤー1）が同時に有効化されると、非テンキー用のキーがマップされたレイヤー2が有効化されます。レイヤー4を有効化することで非テンキーモードに切り替わります。

---

### 2. ZMK Keymap Editorを利用する

ZMK Studioを使わずにキーマップを編集するには、あなたのGitHubアカウントにこのリポジトリをForkして編集する必要があります。

その際、[ZMK Keymap Editor](https://nickcoutsos.github.io/keymap-editor/)を使用することができます。

#### 手順

1. このリポジトリをForkします。
2. [ZMK Keymap Editor](https://nickcoutsos.github.io/keymap-editor/) にアクセスし、GitHubアカウントでログイン。
3. Forkしたリポジトリを選択してキーマップを編集します。
4. 編集内容を保存すると、変更が自動的にコミットされ、Pushされます。
5. ファームウェアが自動的にビルドされ、ダウンロード可能になります。

---

### 3. 設定ファイルを直接編集する

もちろん、[ZMK Keymap Editor](https://nickcoutsos.github.io/keymap-editor/) を使わずに、ForkしたリポジトリをローカルにCloneし、直接設定ファイルを編集することも可能です。  
設定ファイルの詳細については、[ZMK公式ドキュメント](https://zmk.dev/docs) を参照してください。

---

## ファームウェア書き込みについて

リモートにコミットをPushすると、GitHub Actionsによりファームウェアが自動でビルドされます。  
ビルドされたファームウェアは、GitHubリポジトリの「Actions」タブからダウンロード可能です。

### 書き込み手順

1. 真打42AirをPCと有線接続します。
2. 真打42Airのリセットボタンを**短く2回**押します。
3. 「XIAO-SENSE」という名前のストレージとしてPCに認識されます。
4. ダウンロードしたファームウェアをこのストレージにコピーしてください。

**注意**  
- ファームウェアは左右で別々になっています。キーマップの書き換え書き込み先を間違えないように確認してください。
- ファイル転送中にエラーが表示される場合がありますが、基本的に無視して問題ありません。このエラーが出ても書き込みは正常に終了します。

---

## 接続について

真打42Airは最大5台（ZMKの初期設定）の機器とのBluetooth接続が可能です。

真打42Airは左右分割型キーボードで、左側が親機（マスター）、**右側が子機（スレーブ）**として動作します。

右側の子機で入力されたキー情報は左側の親機に伝えられ、親機がその情報を端末に送信します。

親機が端末に接続されていない場合、右側の子機単体ではキー入力を送信できません。
有線接続をする際は、左側の親機に接続してください。

### キーボードをペアリングする
初めての使用時、Bluetoothプロファイルを選択した状態で、お使いのデバイスのBluetooth設定からキーボードをスキャンして接続してください。

### プロファイルの切り替え方法（デフォルトキーマップの場合）
- 右側の ③ボタン を押すと、次のBluetoothプロファイルに切り替わります。
- 右側の ④ボタン を押すと、前のBluetoothプロファイルに戻ります。
- ③ボタンと④ボタンを同時押しすると、該当のBluetoothプロファイルが削除されます。
**注意事項**
-   プロファイル切り替え後、未接続のプロファイルは再ペアリングが必要な場合があります。
-   プロファイルを削除した場合は、接続していたデバイス側のBluetooth設定からも「削除」または「接続解除」を行ってください。

初期状態では、USBで有線接続されている場合にUSBへの出力を優先します。
Bluetooth経由での出力を優先したい場合は、左側の②ボタン（デフォルトキーマップの場合）を押すことで、USBとBluetoothどちらを優先するかを切り替えられます。

## デフォルトキーマップについて

- 「記号と数字」レイヤーの右手側には、**テンキーとして**0~9の数字および `+ - * /` が割り当てられています。
- テンキーではなく、通常の数字・記号入力に切り替えたい場合は、**左側の小型スイッチ①** を押してください。

- デフォルトキーマップはWindowsで利用することを前提にしています。MacOSで利用する際に差異が気になる場合は、ご自身でキーマップを変更してください。
    - 例: CtrlとCommand(Windows)を入れ替え、PrintScreenをShift+Command+3に切り替える

デフォルトキーマップは、OS設定が真打42AirをUS配列キーボードとして扱うことを前提としています。

ただし、OS設定をJIS配列にしたい方向けのキーマップも用意しています。
また、QWERTY配列ではなく、colemak配列、eucalyn配列、大西配列、ツナ恋配列を使用したキーマップも用意しています。

これらを利用する場合は、`config/sample_keymap` フォルダ内の該当キーマップ定義ファイルを、 `config/shin_uchi42_air.keymap` に置き換えてください（ファイル名も変更してください）。