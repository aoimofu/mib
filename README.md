# ■ UCD-SNMP-MIB
UCD-SNMP-MIBで取得できる値を下記に示す。
## CPU (全体)
CPU全体についての値を取得する。Counter32形式なので変換が必要。
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|ssCpuRawUser|.1.3.6.1.4.1.2021.11.50|Counter32|CPU Userの値のカウンタを取得する|
|ssCpuRawNice|.1.3.6.1.4.1.2021.11.51|Counter32|CPU Niceの値のカウンタを取得する|
|ssCpuRawSystem|.1.3.6.1.4.1.2021.11.52|Counter32|CPU Systemの値のカウンタを取得する|
|ssCpuRawWait|.1.3.6.1.4.1.2021.11.54|Counter32|CPU IOWaitの値のカウンタを取得する|
|ssCpuRawInterrupt|.1.3.6.1.4.1.2021.11.56|Counter32|CPU Interruptの値のカウンタを取得する|
|ssCpuRawSoftIRQ|.1.3.6.1.4.1.2021.11.61|Counter32|CPU SoftIRQの値のカウンタを取得する|
|ssCpuRawKernel|.1.3.6.1.4.1.2021.11.55|Counter32|CPU Kernelの値のカウンタを取得する|
|ssCpuRawIdle|.1.3.6.1.4.1.2021.11.53|Counter32|CPU Idleの値のカウンタを取得する|
|ssCpuRawSteal|.1.3.6.1.4.1.2021.11.64|Counter32|CPU Steelの値のカウンタを取得する|

## Memory
Memoryについての値を取得する。値はINTEGERでkBを表す。
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|memTotalReal|.1.3.6.1.4.1.2021.4.5|INTEGER|物理メモリ総量|
|memAvailReal|.1.3.6.1.4.1.2021.4.6|INTEGER|利用可能メモリ(cache, buffer含む)|
|memBuffer|.1.3.6.1.4.1.2021.4.14|INTEGER|割り当て済みBuffer|
|memCached|.1.3.6.1.4.1.2021.4.15|INTEGER|割り当て済みCache|
|memShared|.1.3.6.1.4.1.2021.4.13|INTEGER|利用中Shared|
|memUsedRealTXT|.1.3.6.1.4.1.2021.4.17|INTEGER|使用中メモリ|
|memTotalSwap|.1.3.6.1.4.1.2021.4.3|INTEGER|スワップメモリ総量|
|memAvailSwap|.1.3.6.1.4.1.2021.4.4|INTEGER|利用可能スワップメモリ量|
|memUsedSwapTXT|.1.3.6.1.4.1.2021.4.16|INTEGER|使用中スワップメモリ量|

## Swap I/O Activity (Storage)
スワップの発生回数を記録する。
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|ssSwapIn|.1.3.6.1.4.1.2021.11.3|Counter32|ページイン回数|
|ssSwapOut|.1.3.6.1.4.1.2021.11.4|Counter32|ページアウト回数|

## System I/O Activity (Storage)
全ディスクの合算値である点に注意。
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|ssIORawReceived|.1.3.6.1.4.1.2021.11.58|Counter32|ブロックリード回数|
|ssIORawSent|.1.3.6.1.4.1.2021.11.57|Counter32|ブロックライト回数|

## Load Average
値は小数点を表すため、型はOCTET STRINGとなっている。
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|laLoad.\<index\>|.1.3.6.1.4.1.2021.10.1.3.\<index\>|OCTET STRING|index 1, 2, 3がそれぞれ1分、5分、15分平均を表す|

## 物理Disk別 I/O
正確にはUCD-DISKIO-MIBに定義されているが、UCD-SNMP-MIBからインポートされている。
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|diskIOIndex|.1.3.6.1.4.1.2021.13.15.1.1.1|INTEGER|DISKのINDEXを取得する|
|diskIODevice|.1.3.6.1.4.1.2021.13.15.1.1.2.\<index\>|Display String|物理デバイス名(デバイス名本体、パーティション別なども取得可能)|
|diskIONRead|.1.3.6.1.4.1.2021.13.15.1.1.3.\<index\>|Counter32|読み込みI/O回数|
|diskIONWritten|.1.3.6.1.4.1.2021.13.15.1.1.4.\<index\>|Counter32|書き込みI/O回数|
|diskIOReads|.1.3.6.1.4.1.2021.13.15.1.1.5.\<index\>|Counter32|読み込みバイト数(kB)|
|diskIOWrites|.1.3.6.1.4.1.2021.13.15.1.1.6.\<index\>|Counter32|書き込みバイト数(kB)|

## Login
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|ssCpuUser|.1.3.6.1.4.1.2021.11.9|INTEGER|ログイン中のユーザを表す|

# ■ HOST-RESOURCES-MIB
主にシステムの全体的な情報を取得することが出来る。

## CPU (論理CPU別)
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|hrDeviceDescr.\<index\>|.1.3.6.1.2.1.25.3.2.1.3.\<index\>|OCTET STRING|各論理CPUの名前を取得する|
|hrProcessorLoad.\<index\>|.1.3.6.1.2.1.25.3.3.1.2.\<index\>|INTEGER|各CPUの使用率(%)を取得する|

## FileSystem Usage
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|hrStorageIndex|.1.3.6.1.2.1.25.2.3.1.1.\<index\>|INTEGER|ストレージの識別子|
|hrStorageType|.1.3.6.1.2.1.25.2.3.1.2.\<index\>|OBJECT IDENTIFIER|ストレージ種別。hrStorageFixedDiskとなっているものがブロックデバイス|
|hrStorageAllocationUnits|1.3.6.1.2.1.25.2.3.1.4.\<index\>|INTEGER|一単位当たりのバイト数。ディスクサイズ・使用量の計算で使う|
|hrStorageSize|.1.3.6.1.2.1.25.2.3.1.5.\<index\>|INTEGER|ディスクのサイズ(割り当て単位数換算)|
|hrStorageUsed|.1.3.6.1.2.1.25.2.3.1.6.\<index\>|INTEGER|ディスクの使用中サイズ(割り当て単位数換算)|

# IF-MIB
## 基本カウンタ
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|ifIndex|.1.3.6.1.2.1.2.2.1.1.\<index\>|INTEGER|後述の\<index\>に使用するキー|
|ifDescr|.1.3.6.1.2.1.2.2.1.2.\<index\>|OCTET STRING|IF名を表す|
|ifName|.1.3.6.1.2.1.31.1.1.1.1.\<index\>|OCTET STRING|IF名を表す(推奨)|
|ifInOctets|.1.3.6.1.2.1.2.2.1.10.\<index\>|Counter32|受信バイト|
|ifOutOctets|.1.3.6.1.2.1.2.2.1.16.\<index\>|Counter32|送信バイト|

## 1Gbps以上のNICで推奨のカウンタ
Counter32では4.29GBまでしいか表せないためそれよりも大きな値を扱うために必要。
対応するindexはifDescrと同じ。
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|ifHCInOctets|.1.3.6.1.2.1.31.1.1.1.6.\<index\>|Counter64|受信バイト|
|ifHCOutOctets|.1.3.6.1.2.1.31.1.1.1.10.\<index\>|Counter64|送信バイト|


## トラフィック計算
```
bps = (ΔOctets * 8) / ΔTime
```

# ■ 値の形式
- INTEGER: 符号付整数 (−2,147,483,648 ～ 2,147,483,647)
  - その瞬間の値を記録
- Counter32: 符号なしカウンタ(0 ~ 4,294,967,295)
  - トラフィック量をなど差分を取ってレートを計算する用途
 
# ■ snmpコマンドによるMIBとOIDの確認方法
本当にMIBとOIDの対応は正しいのか検証するための確認方法。
```bash
snmptranslate -On -m +UCD-SNMP-MIB -IR memTotalReal
```
- `-On`
  - `-O` ... 出力形式の指定
  - `n` ... numeric (OID)
- `-m +UCD-SNMP-MIB`
  - `-m` ... 使用するMIBを指定
  - `+UCD-SNMP-MIB` ... 追加ロードするMIBを明示。
- `-IR`
  - `-I` ... 入力のパースを制御するオプション
  - `R` ... OIDラベルへアクセスする。（つまりMIBへアクセスする）

### OIDからMIB名を解決する方法
```bash
snmptranslate -m +UCD-SNMP-MIB .1.3.6.1.4.1.2021.4.5
```

## MIBファイルの位置
- `/usr/share/snmp/mibs/UCD-SNMP-MIB.txt`

# 参考
- [RedHat 21.7 Net-SNMPを使用したパフォーマンスのモニタリング](https://docs.redhat.com/ja/documentation/red_hat_enterprise_linux/7/html/system_administrators_guide/sect-system_monitoring_tools-net-snmp)
