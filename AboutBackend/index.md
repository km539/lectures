# バックエンド概要

## サーバーサイドのプログラミング言語

（例：Node.js、Python、Java など）

### next.js とは何か？

- React をベースとしたフロントエンドフレームワーク

### 特徴

- クライアントからのリクエスト時にレンダリングする SSR(Server Side Rendering)と呼ばれる機能　 → 　各ページ読み込み時のダウンロードファイルサイズを削減できる
- pages/ディレクトリに置いたフォルダ/ファイルの構成に従って、HTML を生成してページ遷移を実現　 → 　 react-router-dom ライブラリを使用しての、URL とコンポーネントの対応が必要ない

- ソースコードの変更を検知して、state を保持したまま変更があった箇所だけを更新　 → 　開発の向上

## サーバーの概要と役割

クライアントからの HTTP リクエストに応じて、サーバーはデータを HTTP レスポンスの形式でクライアントに送ります。　 HTTP (HyperText Transfer Protocol、ハイパーテキスト転送プロトコル) は、Web 上のハイパーメディア文書の転送を可能にする、基盤となるネットワークプロトコルです。一般にブラウザーとサーバーの間で用いられます。

例 1）クライアント-サーバー構造

## 主要な HTTP リクエスト

GET: サーバーからリソース（HTML ページ、画像、テキストファイルなど）を取得するために使用されます。リクエストボディを持たず、URL の末尾にクエリパラメーターを含めることができます。

GET 　/api/users 　//通常の GET リクエスト

GET 　/api/products?id=123&category=electronics 　//クエリパラメータを含む GET リクエスト

上記の使い方ができます。パラメータを直接含めた GET リクエストは直接表示されるため、機密情報(パスワード等)を含めると履歴が残りセキュリティーのリスクがあります。機密情報を含む場合は POST リクエストを使用した方がよいでしょう。

POST: サーバーにデータを送信し、新しいリソースを作成するために使用されます。リクエストボディにデータを含み、通常は HTML フォームの送信や API 呼び出しで使用されます。

## HTTP ステータスコードについて

サーバーがレスポンスで返す 3 桁の番号。頻度が高いコードは 200 で、正常に処理ができたことを意味しています。1XX,3XX,4XX,5XX のコードが存在します。

- 1XX 　情報レスポンス
- 2XX 　成功レスポンス
- 3XX 　リダイレクション
- 4XX 　クライアントエラー
- 5XX 　サーバーエラー

## 知っとくと得する

- HTTP プロトコルと RESTful API
- データベースの基礎（SQL と NoSQL）
- データベースの設計と操作（クエリ、インデックス、トランザクション）
- サーバーサイドフレームワーク（Express.js、Django、Spring など）
- セキュリティの基本（認証、認可、セッション管理）
- ログとエラーハンドリング
- テストの基礎（ユニットテスト、統合テスト）
- デプロイメントとホスティング（Heroku、AWS、Firebase など）

## バックエンド構築（node.js with express）

### nodejs デモ手順

node のバージョンチェック

```
node —version
```

package.json の作成

```
npm init -yes
```

必要なモジュールのインストール

```
npm i express nodemon
```

create app.js file

paste this codes

```
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("backend api");
});
app.listen(5000, () => {
  console.log(`running on port 5000`);
});
```

create post request

```
const users = [
  { username: "user1", password: "password1" },
  { username: "user2", password: "password2" },
];

app.use(express.json());

app.post("/login", (req, res) => {
  try {
    console.log(req.body);
    const { username, password } = req.body;

    const user = users.find(
      u => u.username === username && u.password === password
    );

    if (!user) throw new Error("Invalid username or password");
    res.status(200).json({ message: "Login successful" });
  } catch (error) {
    res.status(401).json({ error: error.message });
  }
});
```

create get request with params

```
app.get("/user/:username/:password", (req, res) => {
  try {
    const { username, password } = req.params;

    const user = users.find(
      u => u.username === username && u.password === password
    );

    if (!user) throw new Error("User not found");
    res.status(200).json({ message: "Login successful" });
  } catch (error) {
    res.status(401).json({ error: error.message });
  }
});
```

## 参考リンク

[MDN サーバーサイド概念](https://developer.mozilla.org/ja/docs/Learn/Server-side/First_steps/Introduction)

[MDN HTTP statsucode](https://developer.mozilla.org/ja/docs/Web/HTTP/Status)
