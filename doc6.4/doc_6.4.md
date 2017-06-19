<!-- $theme: gaia -->

# チーム開発実践入門
## 6.4
### Jun Kimura

---
<!-- page_number: true -->

# Overview

### 6.4 Configuration

* Chefを利用したアプリケーションインストール、設定の自動化
* Serverspecによるテスト

---
# 時代はChefよりAnsible
### Chef使ってるの小学生までだよね〜(AA略

---
# 今日の内容

1. 書籍の内容をさらりと
2. 6.4 Configurationで解説しているのと同等の内容をAnsibleでやってみる
   * VagrantでCentOSにApache入れてPort80でListen
3. Serverspecの部分は書籍と同じようにやります

---
## Configurationしない問題点

* 一台環境つくれても次に同じのが作れる保証がない
  * インストール手順書書いても伝わらない
  * 細かいバージョンが合っていないことも
* 手動なので時間がかかる
  * リリースの度にやる羽目になったら。。。
  * 1000台用意してってなったら。。。

---
# そこで ~~Chef~~ Ansible

---
### Ansibleで出来ること(書籍に倣うと)
* ブートストラッピングの一部(AWS, Azure上のVM構築)
* コンフィギュレーション
* オーケストレーション(もやりようによっては)

---
### 実行パターン
大きく分けて２つあり、状況に応じて使い分ける
1. Ansible実行サーバー(ホスト)からターゲット環境をコンフィギュレーション
   * ホストからターゲット環境にはSSHで入り、コンフィギュレーションする(エージェント不要) 
2. ターゲット環境自身にAnsibleをインストールして自律してコンフィギュレーション
   * ホスト側にAnsibleが不要

---
### 手順
* 基本は２つのファイルを作れば良い
  * playbookファイル:手順を管理
  * inventoryファイル:実行対象のサーバーを管理

---
### 注意事項
* Windowsはホストになれません。。。
* Windowsユーザーの人はvirtualboxでAnsbleのホスト環境を作って下さい
  * もしくは実行パターンの2を使う

---
## Ansible最高じゃん

---
## ちょっとまて、テストはどうした？
# ![notest](no-test.png)

---
# Serverspec

---
### Serverspecで出来ること
* Configurationした環境のテスト
  * インストールされているか。サービスが動いているか。ユーザーが作成されているか等々。。。
#### Ansibleもテスト出来るんだけど。。。
* 色々な考え方はありますが、受け入れテスト(検算)をする手段は別の方が安心感ありますよね

---
### 実行パターン
大きく分けて２つあり、状況に応じて使い分ける
1. Serverspec自身が動いている環境のテスト
   * Serverspecの設定を行う場合に利用するイメージ
2. SSHでアクセス可能なリモートサーバーのテスト
   * 実際の利用はこっちがメイン

---
### 手順
* 基本は２つのファイルを作れば良い
  * playbookファイル:手順を管理
  * inventory:実行対象のサーバーを管理

---
# 実演

---
## 今からやること
1. Ansibleの入ったコントローラ(CentOS)からAnsibleを使ってターゲット(CentOS)にApacheのインストール
2. コントローラからServerspecを使ってターゲットに作られた環境のテスト

---
## おわりに
* 実はConfiguration自体、考え方が結構古くなりつつあり。。。
  * Herokuを代表とするPaaSの世界では必要のない話
  * dockerだったらdockerfileで結構書けちゃうし。。。
* こんなのもあるんだなくらいの認識でも良いとおもいます
   * もちろん、VMやハードウェアが必要な環境なら役に立ちます 

---
### 参考になるリンク
* [Ansibleをはじめる人に。](http://qiita.com/t_nakayama0714/items/fe55ee56d6446f67113c)
* [AnsibleによるInfrastructure as code入門 ](https://www.slideshare.net/kk_Ataka/ansibleinfrastructure-as-code)
* [WikiPedia(Ansible)]( https://ja.wikipedia.org/wiki/%E3%82%A2%E3%83%B3%E3%82%B7%E3%83%96%E3%83%AB)
* [「Serverspec」入門 記事一覧](https://thinkit.co.jp/series/5166)

---
<!-- page_number: false -->

# 以上です。
## ご清聴ありがとうございました。