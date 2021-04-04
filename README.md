# GcHwEmulator
[GameControllerizer](https://github.com/GameControllerizer/GameControllerizer) の中核をなすH/W ゲームパッドエミュレーターです．本製品をUSBケーブルでPCやゲーム機に接続するとUSB HID互換ゲームパッドとして振舞います．さらにこれを micro:bit や Raspberry Pi から操作することで，ディジタルゲームへの操作入力を自在にプログラミングすることが可能です．
用途に合わせて２種類を用意しています．

## (GC-GP) 汎用タイプ

各種RasPiにマウントできる他，Groveコネクタを通じて多種の基板に接続が可能です．

<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/gc-v1_1-features.png" width="540px">

## (GC-MB) micro:bit専用タイプ

micro:bit専用タイプです．micro:bit(v1/v2)にマウントできます．

<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/gc-mb-v1-features.png" width="540px">

## Connection

| Type |  GC-GP  |  GC-MB  |
| ---- | ---- | ---- |
|  to RasPi  |  ○ (40-pin) |  ☓ |
|  to micro:bit  |  ○ (grove)  |  ○ (ring)  |
|  to M5 |  ○ (grove) |  ☓  |

※1 RasPi互換の40-pin connectorを持つ製品(NVIDIA Jetson等)も，GC-GPへ接続することが可能です  
※2 基板の改造・配線の自作を行う場合はこの限りではありません

## Features
- Grove connector(GC-GP) : 本製品を micro:bit と接続するときに使用します．
- 40-pin connector(GC-GP) : 本製品を Raspberry Pi シリーズと接続するときに使います．
- Ring connector(GC-MB) : 本製品を micro:bit と接続するときに使います．
- Reset switch : 押し込みでリセットがかかります．
- Tact switch[0:3] : ライブラリと組み合わせることで外部ボタンとして利用できます．
- Status LED
    - PWR(green) : 電源が投入されると点灯します
    - CMD(orange) : micro:bit や RasPi からコマンドを受信すると点滅します
    - RESET(red) : リセットがかかると点灯します
- Solder jumpers(GC-GP) : ※回路図を参考に，くれぐれも自己責任でお使いください

## Spec
- NXP LPC11U35  Cortex-M0
- USB x 1, Grove con. x 1, 40-pin con.  x 1
- Status LED (Power, Command, Reset)
- Reset switch, Tactile switch[0:3]
- Size
    - (GC-GP) 65mm x 30mm 
    - (GC-MB) 52mm x 42mm 
- Schematics
    - (GC-GP) [gc-v1_1_schematics.pdf](https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/resources/gc-v1_1_schematics.pdf)
    - (GC-MB) [gc-mb-v1_schematics.pdf](https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/resources/gc-mb-v1_schematics.pdf)

## Buy now
[SwichScience様](https://www.switch-science.com/)にて委託販売中です（各税込 3,300円）．
- [(GC-GP) 汎用タイプ](https://www.switch-science.com/catalog/5457/)
- [(GC-BM) micro:bit専用タイプ](https://www.switch-science.com/catalog/5457/)

---

## Usage (GC-GP)
1. 本製品/ゲームコンソール / ホストマイコン（micro:bit / RasPi） と接続します（下図）
2. `Reset switch` を押します．初期化が正常になされるとされると `LED-CMD` が点滅します（3度）．
3. ホストマイコンから本製品を通じて，ゲームコンソールへと制御信号を送ります．

### with micro:bit

#### Requirements
- BBC micro:bit (v1/v2 で動作を確認しています)
- Grove Shield for micro:bit
- Grove 4-pin cable
- USB cable (microB)

#### Connection
<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/connection-microbit.png" width="540px">

制御方法については [Makcode package](https://github.com/GameControllerizer/pxt-gamecontrollerizer) を参照ください．

### with RasPi

#### Requirements
- Raspberry Pi (3B/3B+/ZeroW/ZeroWH で動作を確認しています)
- USB cable (microB)

#### Connection
<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/connection-raspi.png" width="540px">

制御方法については [Node-RED nodes](https://github.com/GameControllerizer/node-red-contrib-game_controllerizer) を参照ください．

---

## Usage (GC-MB)
1. 本製品/ゲームコンソール / ホストマイコン（micro:bit） と接続します（下図）
2. `Reset switch` を押します．初期化が正常になされるとされると `LED-CMD` が点滅します（3度）．
3. ホストマイコンから本製品を通じて，ゲームコンソールへと制御信号を送ります．

### with micro:bit

#### Requirements
- BBC micro:bit (v1/v2 で動作を確認しています)
- 六角スペーサー・ネジ・ナット (M3 x 4本)
- USB cable (microB)

#### Connection
<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/connection-gc-mb.png" width="540px">

制御方法については [Makcode package](https://github.com/GameControllerizer/pxt-gamecontrollerizer) を参照ください．

---

## FAQ
#### H/W gamepad emulator に接続可能なゲームコンソールは何ですか？
GameControllerizerのH/W gamepad emulatorは **"一般的に市販されている汎用USB HID互換ゲームパッド"** を模擬します．**USB HID互換ゲームパッドからの入力を受け付けるかどうかは各ゲームコンソール / 各ゲームソフトに依存します**．そのため "どの環境ならば動く" と言うことは困難です．本製品を購入前に，対象とするゲームコンソール / ゲームソフトにて事前に確認いただきますようお願いいたします．なお本件を理由とした返品・交換は致しかねます．  
また一部ゲームコンソールについてはコンバーターを利用することで動作したことはありますが，「どのコンバーターならば動くか？」といった情報も定かではありません．動作実績情報をお寄せいただければ幸いです．

#### 技術サポートはありますか？
技術サポートは致しかねます．免責事項にありますとおり，ご自分で問題に対処できる方への販売を前提としています．ただし，大学・企業・教育/研究機関等で多数ご利用の場合に限り対応させていただける可能性ございます．[津田塾大学 栗原研究室](http://www.unryu.org/) もしくは gamecontrollerizer(at)gmail.com までご相談ください．

## Notice
- 本製品は研究者・教育関係者・開発者向けの製品となっています．本WebサイトおよびGitHub上の技術情報を読んでいただいた上でご自身の責任でご使用下さい．
- 本製品または本製品向けライブラリ（Node-RED nodes, Makcode package) を使用して発生した直接的・間接的な損害に対するその種類，規模を問わず補償は致しかねます．
- 技術サポートは致しかねます．ただし，大学・企業・教育/研究機関等で多数ご利用の場合に限り対応させていただける可能性ございます．[津田塾大学 栗原研究室](http://www.unryu.org/) もしくは gamecontrollerizer(at)gmail.com までご相談ください．
- 製品の価格・外観・仕様等について予告なく変更される可能性がございます．
- 返品，キャンセル，返金等については各委託販売会社の規則に準じます．
- 初期不良品交換のみ対応いたします（到着後2週間以内）．それ以外の故障・相性問題等を理由とした交換・原因追及は致しかねます．
- 購入される方は，上記をご理解いただいたものとさせていただきます．

----

## History

### (GC-MB) ver. 1.0 (latest)
<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/history-mb-v1.jpg" width="480px">

- LPC11U35 Cortex-M0
- Ring connector (for micro:bit)
- 4 tactile switches
- HID gamepad emulation

### (GC-GP) ver. 1.1 (latest)
<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/history-v1_1.jpg" width="480px">

- LPC11U35 Cortex-M0
- Grove connector (for micro:bit)
- 40-pin connector (for RasPi)
- 4 tactile switches
- HID gamepad emulation

### (GC-GP) ver. 0.0 (prototype, DISCONTINUED)
<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/history-v0.jpg" width="480px">

- LPC11U35 Cortex-M0
- 40-pin connector (for RasPi)
- 4-pin connector (for general MCU)
- HID & PSX gamepad emulation

<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/history-v0_psx.jpg" width="320px">
