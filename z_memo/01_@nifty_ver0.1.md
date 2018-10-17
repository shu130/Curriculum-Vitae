
# ISP基幹ネットワークの監視

<!-- # 業務の箇条書き -->

## 監視

### トラフィック・帯域使用率

主にキャリア（ユーザ）向け、DC向け、対外向け（AS間）のトラフィック

- 通信量 （bps, pps）
- 品質 （packet discards, interface errors, packet loss, round trip time）
- 閾値

<!-- - キャリア向け（NTT地域網）・ユーザ向け -->
<!-- - キャリア向け（ユーザ向け）
- DC向け
- 対外向け（AS間） -->

### プロトコル・ハード状態監視

- ハード障害検知・障害予兆検知
- BGPセッションDown/Up（BGPピアのセッション異常）
- インターフェースLink Down/Up
- CPU・Memory使用率


---


## 申告対応

カスタマーサービスの２次窓口として技術問い合わせに対応
主に通信不安定、速度不満などの申告に対する対応

- 電話/メール受付
- バックボーンネットワークの正常性の確認
- 確認結果を１次窓口に回答


---


## 障害対応・復旧

主にハード障害の対応

### 障害報告・連絡

- お客様への障害報告メール
- 社内エスカレーション
- SLAの遵守
- トラフィック迂回オペレーション
- インシデントチケット作成


### 障害機器の交換

- ハード交換保守員の手配、遠隔での作業指示
- 交換の為のトラフィック迂回・交換・戻し作業
- 代替機の設置


### 各種管理台帳の更新

- NW機器、予備部材
- IPアドレス
- ラック搭載図

### 予防交換

検知した障害予兆の内容によって、モジュール・ユニットの交換対応
<!-- 検知した障害予兆の内容によって、光トランシーバ等の交換対応 -->
<!-- 障害予兆を検知した光モジュール等の交換対応 -->

- ラインカード
- XFP(10Gbps) 光トランシーバモジュール
- SFP+(10Gbps) 光トランシーバモジュール
- 電源ユニット
- ファンユニット


---



## オペレーション

### 定常作業

- トラフィック迂回
  - ハード交換に伴うトラフィック迂回・戻し
  - 支障移転工事に伴うトラフィック迂回・戻し

- ネットワーク変更
  - 他ASとのPeeringの為の設定変更
  - AS-PATH更新作業


### DDosアタック対処

#### NTT-COM トラフィック解析ツール（SAMURAI）にて監視

- リアルタイムDDos検知・対処
- 社内エスカレーション

- #### オペレーション
  ##### （ISPバックボーンの入り口にて対処）
  - 経路生成ルータに Next-Hop Null を設定（Blackhole Routing）
  - 全BGPルータに広報させてトラフィックを遮断
  - 収束後に設定解除（24時間様子見）


---

## 使用したNW機器、監視ツール等（主なもの）

### NW機器

Manufacturer  | OS | Model
--|---|--
Cisco  | IOS-XE  | Catalyst7604,3650
Cisco  | IOS-XR  | CiscoASR9001
Juniper | JUNOS | EX4600
Juniper | JUNOS | MX80
APRESIA Systems | AEOS | Apresia15000



### 監視ツール

<!--
用途 | ツール名 | Manufacturer
--|---|--
トラフィック流量  | MRTG  | aaaaaaaa
レイテンシ  | Smokeping  | aaaaaaaa
DDossアタック監視 | Samurai | NTTcommunications
 -->
<!--
ツール名  | 目的  | 主な用途
--|---|--
SNMPc  | TCP・死活・しきい値監視  |
MRTG  | トラフィック  | トラフィック・機器リソース（CPU・メモリ等）
Smokeping  | 異常遅延 | Ping応答のレイテンシ幅の確認
Systemwalker  | syslog | ???
Samurai  | DDossアタック | ???
Beckey  | メール
 -->

ツール名  | 主な用途
--|---
SNMPc  | TCP・BGP・死活・しきい値・Syslog等の監視
MRTG  | トラフィック・機器リソース（CPU・Memory等）
Smokeping  | 遅延監視・パケットロス
Systemwalker  | Syslog
Samurai  | DDossアタック検知
Becky!  | Syslogをメール通知

---
