---
title: "勉強会[RaspberryPiとBluetoothでスマホを検知してみた]"
date: 2018-07-27T18:30:57+09:00
tags: ["勉強会","会社紹介","raspberry pi", "ラズパイ", "bluetooth", "川崎"]
categories: ["里井 嘉真(yoshi-sato)"]
---


<br>

皆さんこんにちは。<br>
パーソルプロセス＆テクノロジー株式会社のyoshi-satoです。<br>
今週もテクテク部の勉強会の様子をお送りいたします。<br>
よろしくお願いします。<br>
<br>
※技術的なブログについてはQiitaでメンバーが各々に書き進めています。<br>
こちらもぜひご覧ください。<br>
<br>
[Qiita - パーソルプロセス&テクノロジー](https://qiita.com/organizations/persol-pt)<br>
<br>
今週の発表者はテクテクMGRの[川崎](https://persol-pt.github.io/categories/%E5%B7%9D%E5%B4%8E-%E5%8D%93%E6%BA%80/)さんです。<br>
発表テーマは、「RaspberryPiとBluetoothでスマホを検知してみた」でした。<br>
<br>

{{< figure src="/images/tech-workshop/20180727/tech-workshop0727.jpg" title="" >}}

<br>
## テーマ「RaspberryPiとBluetoothでスマホを検知してみた」
---
IoTの代名詞的な名声をほしいままにするRaspberryPi(以下ラズパイ)ですが、川崎さんはこのラズパイを使って<br>
毎日の勤怠時間の入力を自動化したいと考えました。<br>
弊社では毎日の勤務時間をTAManagerと呼ばれる勤怠システムに入力することになっているのですが、<br>
毎日のことということもあり若干微妙にほんの少しわずらわしく感じることもあります。<br>
怠慢・短気・傲慢を美徳とするエンジニアにとって、この煩わしさをそのままにして生きていくわけにはいきません。<br>
<br>
<br>

## 実現方法
---
川崎さんは、ラズパイをオフィスの自席に置いておき、<br>
Bluetoothで自分のスマホが接近したか離れたかを検知することで出勤・退勤時間の<br>
打刻を行うことを考えました。<br>
今回は勤怠入力の仕様（休み時間や一時離席はどうするか等）は後で考えるものとして、<br>
ラズパイでスマホを検知するところまでの発表でした。

<br>

### 使うもの
今回Bluetoothでラズパイとスマホの距離を定期的にチェックするために使うものです。

* hcitool
  * raspbianで利用できる、Bluetooth機器に接続するためのツール。
  * 機器のスキャン、強度計測、ペアリングができる。
* l2ping
  * ネットワークレイヤ2でpingするツール。
  * つまりMacアドレスに対してpingする。

<br>
### 仕組み
Railsで定期的にペアリングされたスマホにpingを送り、接近、離脱をチェックする。<br>
<br>
勉強会中のデモでは、あらかじめペアリングしたスマホを川崎さんが持ち会議室から離れると、<br>
Slackにメッセージが送信されました。<br>

{{< figure src="/images/tech-workshop/20180727/slack.png" title="" >}}

<br>
<br>
## 課題
---
### 簡単にペアリングする仕組みの構築
ペアリングを行わなくてもスマホが近くにあるかないか程度のpingはできるが、<br>
正確な距離を信号強度から測るにはペアリングが必要だそうです。<br>
現段階ではラズパイとスマホのペアリングは手動で行うため、より簡単にペアリングできる<br>
仕組みの構築が必要です。<br>
<br>

### 勤怠の自動入力の仕様設定
今回はラズパイでスマホの接近・離脱を検知することができましたが、<br>
勤怠システムへの自動入力となると、休み時間や一時離席などを考慮した仕組みを<br>
作らなければいけません。<br>
<br>
<br>

## ほかに何ができそうか
---
最後に、川崎さんはオフィス以外でラズパイでスマホを検知して何ができそうかを<br>
発表してくださりました。<br>

* 家に置いて子供の帰宅を通知する。
* 電気のオン・オフを自動で行う。
* 店頭に置いて特定の人の来店を店員に通知し、来店回数や購入履歴などを同期して接客対応を行う。

<br>
<br>

---

以上、[川崎](https://persol-pt.github.io/categories/%E5%B7%9D%E5%B4%8E-%E5%8D%93%E6%BA%80/)さんの発表でした。<br>
ラズパイは発想次第でいろいろなことに使えるので、今回のような<br>
夢の広がる発表はとても興味深く、自分だったら何を作ろうかと、わくわくしました。<br>
川崎さん、どうもありがとうございました。<br>
<br>
