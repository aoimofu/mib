# mib
- 参考 [RedHat 21.7 Net-SNMPを使用したパフォーマンスのモニタリング](https://docs.redhat.com/ja/documentation/red_hat_enterprise_linux/7/html/system_administrators_guide/sect-system_monitoring_tools-net-snmp)

# 値の形式
- INTEGER: 符号付整数 (−2,147,483,648 ～ 2,147,483,647)
  - その瞬間の値を記録
- Counter32: 符号なしカウンタ(0 ~ 4,294,967,295)
  - トラフィック量をなど差分を取ってレートを計算する用途

## UCD-SNMP-MIB
### CPU
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
|ssCpuRawSteel|.1.3.6.1.4.1.2021.11.64|Counter32|CPU Steelの値のカウンタを取得する|

### Memory
Memoryについての値を取得する。値はINTEGERでkBを表す
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|memTotalReal|.1.3.6.1.4.1.2021.4.5|INTEGER|物理メモリ総量|
|memAvailReal|.1.3.6.1.4.1.2021.4.6|INTEGER|利用可能メモリ(cache, buffer含む)|
|memBuffer|.1.3.6.1.4.1.2021.4.14|INTEGER|割り当て済みBuffer|
|memCached|.1.3.6.1.4.1.2021.4.15|INTEGER|割り当て済みCache|
|memShared|.1.3.6.1.4.1.2021.4.13|INTEGER|利用中Shared|
|memUsedReal|.1.3.6.1.4.1.2021.4.7|INTEGER|使用中メモリ|
|memTotalSwap|.1.3.6.1.4.1.2021.4.3|INTEGER|スワップメモリ総量|
|memAvailSwap|.1.3.6.1.4.1.2021.4.4|INTEGER|利用可能スワップメモリ量|
|memUsedSwap|.1.3.6.1.4.1.2021.4.8|INTEGER|使用中スワップメモリ量|


## HOST-RESOURCES-MIB
個別CPUの使用率を取得する
|MIB|OID|Type|説明|
|:-|:-|:-|:-|
|hrDeviceDescr.\<index\>|.1.3.6.1.2.1.25.3.2.1.3.\<index\>|OCTET STRING|各論理CPUの名前を取得する|
|hrProcessorLoad.\<index\>|.1.3.6.1.2.1.25.3.2.1.2.\<index\>|INTEGER|各CPUの使用率(%)を取得する|
