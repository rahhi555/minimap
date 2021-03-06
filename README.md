# minimap-portfolio
自作のポートフォリオアプリ「[ミニマップ](https://www.minimap.work)」のまとめリポジトリです。他のリポジトリは👇の３つ
- [NuxtJSのリポジトリ](https://github.com/rahhi555/portfolio-front/tree/master)
- [Railsのリポジトリ](https://github.com/rahhi555/portfolio-api/tree/master)
- [terraformのリポジトリ](https://github.com/rahhi555/portfolio-terraform/tree/master)

## ローカル起動手順
1. `git clone https://github.com/rahhi555/minimap.git`でこのリポジトリをローカルにクローンします
2. `git submodule update --init`でサブモジュールのapi,front及びterraformディレクトリの中身をダウンロードします。
3. このアプリケーションはgoogle maps apiを使用しているので、ご自身のapiキーを`.env`のYOUR_API_KEYの箇所に記述します。
4. `docker-compose up`でコンテナのビルド及びスタートを実行します(この処理には通常数分かかります)。
5. 起動し終えたら、localhostの80番ポートでブラウザからアクセスできます。
6. api側のコンソールは`docker exec -it portfolio-api ash`、front側のコンソールは`docker exec -it portfolio-front ash`でアクセスできます。

## サービス概要
現場で作業をする際に、離れた位置の人と仕事の進捗状況及び位置情報を共有できるサービスです。
長方形を組み合わせて作業地域の簡単な平面図を作成していただき、作業リストを図形と紐付けることで視覚的に進捗状況が分かるようになっています。またピン立てやマーカーを引くこともでき、リアルタイムに情報共有が可能です。

## 登場人物
エンドユーザー
- 清掃業や設営等の同時多発的に作業する人
- イベントのスタッフ
- イベントの来客者
- サバゲーマー

管理者
- 作業監督者
- イベント主催者

## ユーザーが抱える課題
作業を同時多発的に行う際にどこが終わっていてどこが終わっていないかわからない。それにより管理者は全体の把握が困難になり、人手不足の箇所に人員をアサインするといったことができなくなる。結果効率的に作業できなくなる。

## 解決方法
作業の進捗情報と位置情報を末端まで共有できるようにすることで、各々が次に何をやるべきかを認識でき、効率的に作業できるようになる。

## プロダクト
TODOリストと位置情報をリアルタイムに紐付ける。

## アプリを作ろうと思った経緯
前職で大規模イベントの作業員として招集されたことがありました。作業内容として会場の設営やお客様の誘導等があったのですが、トランシーバーで進捗状況や位置情報を正確に伝えるのは難しく、現場が混乱することもありました。そんな時にリアルタイムに連動する地図があればいいのにと思ったのがきっかけです。FPSのミニマップみたいな感じで、状態にあわせて建物図の色を変えたり、指定場所にピンを立てたりしたいなと思っています。

<hr>

## 使用技術
- フロントエンド
  - NuxtJS(2.15.8)
  - TypeScript(4.2.4)
- バックエンド
  - Rails(6.0.4.1)
  - Ruby(3.0.2)
- データベース
  - MySQL(8.0.23)
  - Redis(6.0.5)
- 認証
  - firebase Authentication
- 開発環境
  - docker-compose
- インフラ
  - AWS ECS(Fargate)
  - terraform
- CD/CI
  - Github Actions

## インフラ構成図
![インフラ構成図](./readme_images/インフラ構成図.jpg)

## 機能
|ログイン|
|-|
|![login](./readme_images/login.png)|
|簡単ログインとGoogleログインを実装|

|チュートリアル|
|-|
|![tutorial](./readme_images/チュートリアル.jpg)|
|実際に操作して体験できるチュートリアル|

|Todoリスト作成|
|-|
|![todo](./readme_images/todoリスト.jpg)|
|Todoリストを作成して作業を見える化|

|マップ作成|
|-|
|![map_edit](./readme_images/マップ編集.jpg)|
|googleマップ上に平面図を作成し、実際の作業場所と一致できる|

|作業実行|
|-|
|![map_show](./readme_images/マップ閲覧.jpg)|
|todoに応じて平面図の色が変化し、一目で作業進行度が確認できる。リアルタイムに共有され、マーカーやピンをマップに書くことも可能|

## ER図
![er](./readme_images/ER図.jpg)
