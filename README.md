# GcHwEmulator
[GameControllerizer](https://github.com/GameControllerizer/GameControllerizer) の中核をなすH/W ゲームパッドエミュレーターです．

本製品をUSBケーブルでPCやゲーム機に接続するとUSB互換ゲームパッドとして振舞います．さらにこれを micro:bit や Raspberry Pi から操作することで，ゲームコンソールへの入力を自在にプログラミングすることが可能です．

## Buy now
2019年3月中の一般頒布開始を予定しています．

## Features
<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/gc-v1_features.png" width="540px">

- Grove connector : 本製品を micro:bit と接続するときに使用します．
- 40-pin connector : 本製品を Raspberry Pi シリーズと接続するときに使います．
- Reset switch : 押し込みでリセットがかかります．
- Tact switch[0:3] : ライブラリと組み合わせることで外部ボタンとして利用できます．
- Status LED
    - PWR(green) : 電源が投入されると点灯します
    - CMD(orange) : micro:bit や RasPi からコマンドを受信すると点滅します
    - RESET(red) : リセットがかかると点灯します
- Solder jumpers : ※回路図を参考に，くれぐれも自己責任でお使いください

## Usage
1. 本製品/ゲームコンソール / ホストマイコン（micro:bit / RasPi） と接続します（下図）
2. `Reset switch` を押します．初期化が正常になされるとされると `LED-CMD` が点滅します（3度）．
3. ホストマイコンから本製品を通じて，ゲームコンソールへと制御信号を送ります．

### with micro:bit

#### Requirements
- BBC micro:bit
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

## Resources
- [Schematics (ver. 1.1)](https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/resources/gc-v1_1_schematics.pdf)

## Notice
- 本製品は研究者・教育者・開発者向けの製品となっています．GitHub上の技術情報を読んでいただいた上でご自身の責任でご使用下さい．
- 本製品または本製品向けライブラリ（Node-RED nodes, Makcode package) を使用して発生した直接的・間接的な損害に対する補償は致しかねます． 
- 技術サポートは致しかねます．ただし，大学・企業・教育/研究機関等で多数ご利用の場合に限り対応させていただける可能性ございます．[津田塾大学 栗原研究室](http://www.unryu.org/home) もしくは gamecontrollerizer(at)gmail.com までご相談ください．
- 運送上のトラブルに関し，運送会社の補償以上の対応は致しかねます．
- 初期不良品交換のみ対応いたします（到着後1週間以内）．

## !!! Caution !!!
本製品が模擬するのはあくまで **"USB互換ゲームパッド"** になります．**USB互換ゲームパッドからの入力を受け付けるかどうかは，ゲームコンソール / ゲームソフトによりまちまち**ですので，**購入前に必ずご確認ください**．本件を理由とした返品・交換は致しかねます．

----

## History

### ver. 1.x (latest)
<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/history-v1.jpg" width="480px">

- LPC11U35 Cortex-M0
- Grove connector (for micro:bit)
- 40-pin connector (for RasPi)
- 4 tactile switches
- HID gamepad emulation

### ver. 0.0 (prototype, DISCONTINUED)
<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/history-v0.jpg" width="480px">

- LPC11U35 Cortex-M0
- 40-pin connector (for RasPi)
- 4-pin connector (for general MCU)
- HID & PSX gamepad emulation

<img src="https://raw.githubusercontent.com/wiki/GameControllerizer/GcHwEmulator/images/history-v0_psx.jpg" width="320px">
