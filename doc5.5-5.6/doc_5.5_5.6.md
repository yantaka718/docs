<!-- $theme: gaia -->

# <div style="text-align: center;">チーム開発実践入門</div>

### <div style="text-align: center;">5.5-5.6 CIの運用</div>

#### <div style="text-align: center;">手島　史裕</div>

---
<div style="font-size: 24pt">

# 目次
</div>

* ビルドが壊れたらどうするか
* トレーサビリティの担保
* CIによって得られるもの

---
###### ビルドが壊れたらどうするか

<div style="font-size: 18pt">

* すべてのメンバーのコミットを禁止する
</div>

<div style="font-size: 14pt">

* 中央集権型バージョン管理の場合、別の人のコミットが重なり修正が困難になる
* 分散バージョン管理でも原則は同じだが、github-flowのように、メンバーが各々のリポジトリを持ち、Pull Requestを送る運用であれば、必ずしもコミットを禁止する必要はない。

</div>
<div style="font-size: 18pt">

* テストしてからマージする
</div>
<div style="font-size: 14pt">

* そもそもビルドが壊れた状態でcommitされない環境を作る
* JenkinsとGithubの連携の場合、PullRequestを送ると、自動的にビルドが実行され、結果が視覚的に確認できるようになる。
* Githubを使わなくても、検証済みの間違いないものだけをメインラインにマージする運用により、チーム開発の生産性が向上する。 
</div>

---
###### トレーサビリティの担保

<div style="font-size: 18pt">

* Jenkinsをチケット管理システムやバージョン管理システムと連携することで、プロジェクトを可視化する

![5.18](images/5_18.jpg)
</div>

---

<div style="font-size: 18pt">

* ビルドとコミットの関連付け
</div> 
<div style="font-size: 14pt">

* CI環境を構築すれば必然的にビルドとコミットが関連づく
* どのビルドとどのコミットが関連づくかわかるため、トラブルの対応が容易になる
![5.18](images/5_19.jpg)
</div>

---

<div style="font-size: 18pt">

* チケット管理との連携
</div> 
<div style="font-size: 14pt">

* チケット管理とバージョン管理を連携させることで、変更履歴からチケット番号のリンクをたどることができる。
* Jenkinsの場合、Backlog、Trac、Redmineといった様々なチケットツールと連携が可能
</div>

---

###### CIによって得られるもの
* CIサーバーで情報を一元管理することで、トレーサビリティを担保し、プロジェクトを可視化できる。
* 常に動作可能なアプリケーションを維持できる。
* CIの次は**即座に本番環境にリリース可能**な状態を維持するCD(継続的デリバリー)である。

