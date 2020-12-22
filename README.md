# アプリ概要

[GrassChords](https://grasschords.com "GrassChords")<br>
※スマートフォン向けサイト(PC でも閲覧可能)

"Bluegrass"という音楽の「初心者向けジャムセッション支援アプリ」 です。<br>
＊ジャムセッション・・・「みんなが知っている定番曲」を即興で演奏。奏者自身が楽しむもの。

このサービスでは

- 定番曲のコード譜面(曲で使われる音階がわかる譜面)を作成・共有
- 曲の難度や人気度合いを測定・表示

することでジャム曲の練習から参加までをサポート

[利用シーン例 動画(1:26)](https://www.youtube.com/watch?v=y3dYltsLgz0&list=PLFu1xCObsLPNi-TWiEcojQtsqfrSXi_1q&index=2&t=0s)
※音が出ます。イヤホンが無い方はミュートしてご覧ください。

■ テストユーザーログインも可能ですので、自由にお試しください

# 使用技術・言語

- フロントエンド(javascript, jQuery, HTML/CSS, HAML, Sass)
- バックエンド(Ruby on Rails6.0, API: ReCAPTCHA)
- テスト(RSpec, FactoryBot, Capybara)
- Web サーバ(nginx, unicorn)
- データベース(MySQL)
- コンテナ(Docker, docker-compose)
- AWS(VPC, EC2, Route53, ELB, ACM, ECS, SSM, KMS, S3, CloudWatch, CLI)
- 開発環境(MacOS, VScode, Git, GitHub, CircleCI, bash)

# インフラ構成

![environment](./public/images/GrassChords_Env.png)

# 機能要件

### 楽曲とコード譜の編集

- 楽曲の作成・編集・削除
- コード譜の作成・更新・削除
- コード譜の編集キーボード

### コード譜の閲覧

- コード譜面の閲覧機能(音楽記号対応済み)
- コード譜のキー(\*)切替機能
- コード譜の信頼度評価ボタン(ajax)
- 楽曲の練習をしていることの表明ボタン(ajax)
- コード譜の信頼度順ソート

\* 音楽用語。カラオケで操作するキーと同じものを指します

### 楽曲の検索

- 初心者向け曲などの属性表示
- 条件検索: キーワード + 属性検索
- 楽曲の練習人数ソート

### ユーザ機能

- ユーザ検索機能: 練習してる曲 + 活動地域 検索
- ユーザ情報 登録・編集・削除
- ユーザ認証機能(Devise)
- マイページ 練習曲、信頼したコード譜の管理機能
- テストユーザログイン機能

### チャット機能

- メッセージ送信機能
- メッセージ一覧機能

### UI

- グローバルメニュー(ハンバーガーメニュー)
- グローバルサーチ
- ページネーション(pagy) (楽曲検索、練習曲リストなど)
- パンくずナビ(gretel)

# 非機能要件

- レスポンシブ対応(モバイルファースト)
- CSS の flocss 対応
- エラーハンドリング
- ReCAPTCHA(API)を用いたセキュアなユーザ認証
- HTTPS 接続
- ローリングアップデート
- データベースの定期バックアップ(bash + S3)
- モデル/コントローラの単体テスト
- 統合テスト

# このアプリで解決したい課題

ジャムセッションは音楽を楽しむ上で、非常に重要だが、音楽初心者にとっての参加ハードルが高い。

## 詳細

### ジャムセッションに参加していくことで得られるメリット

0. 一緒に演奏する楽しさを気軽に味わえる ＝ Bluegrass 音楽の醍醐味
1. 合奏の回数が増えることで、上達スピードが向上
2. コミュニケーションのきっかけとなり、音楽仲間の輪が広がる

一方で、「やってみたい」「うまくなりたいからやる」と思っているものの、<br>
ハードルの高さから諦める方も多数いるのが現状の Bluegrass コミュニティの課題。

### 高いハードルの要因

- 曲を練習するために必要なコード進行(曲で使われている音階の流れ)の把握が困難
- １曲覚えるコストが高い上に初心者どうしだと知ってる曲が被らない…

### 解決する手法

- コード譜のデータを検索/閲覧できる機能
- 練習中/弾ける曲の集計により”超”メジャー曲を可視化
- コード譜の作成機能により最新トレンドにも対応

## リリース時の反響

![reaction](./public/images/GC_reaction.png)

# 使ってみよう

### コード譜を見つけよう

- トップページの検索窓に"Country Road"と入力し、Jam アイコンをクリックしてから、検索ボタンをクリック
- 検索結果に表示された"Country Road"をクリック。コード譜が表示されます
- ジャムしながら見たいときは"拡大して見る"をクリック
- コードを鳴らしながら歌ってみて、声の高さが合わないと思ったら、"key of ○○"と表示されているボタンをクリック
- 表示されるメニューを操作してみましょう。選択したキーに合わせてコード譜の表示が変化します

### 人気曲を調べよう

- トップページの検索機能に何も入力せず、検索ボタンをクリック
- "練習してる人順"を選択後、もう一度"検索ボタンを"クリック
- 練習しているユーザが多い曲順に楽曲が表示されます

### 楽曲を登録しよう

この曲がないな？と思ったら楽曲登録しましょう！

- ユーザログインします(テストユーザログインも可能です)
- 画面右上にあるボタンからメニューを開き、"データ登録"=>"楽曲を登録"の順にクリック
- 曲名と楽曲の特徴に該当する特徴をアイコンから選択して、"登録"をクリック

### コード譜を登録しよう

あなたが Bluegrass 上級者であれば、その知見を必要としている人がいます！

- ユーザログインします(テストユーザログインも可能です)
- 画面右上にあるボタンからメニューを開き、"データ登録"=>"コード譜"の順にクリック
- "曲名"に文字を入力すると楽曲が検索表示されます。コード譜を登録したい楽曲を選択しましょう！
- 画面右下の"Editor"ボタンをクリックすると、編集キーボードが表示されます
- コード譜を入力したいスペースをクリックすると、カーソル点滅が始まります
- カーソル点滅状態で編集キーボードをクリックすると選択箇所に入力されます
- 編集が完了したら編集キーボード右上の × ボタンをクリック
- スクロールして画面下部まで移動し、"登録"をクリック

ありがとうございます！これであなたの知見が共有されました。<br>
検索機能で先程登録された楽曲を検索すると、登録したコード譜が確認できます。

# 募集

管理者、開発者、テスター<br>
連絡先: Twitter @ShotaImoto1