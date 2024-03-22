# Github

## git について

Gitとはソースコードや変更履歴を管理するために使われる、代表的な分散型バージョン管理システム。

- ローカルリポジトリ：自分の PC 環境下にあるリポジトリ
- リモートリポジトリ：ネットワーク上で他ユーザーとファイル・変更履歴を共有するリポジトリ

## コマンド一覧

PORCELAIN (82)

- 主要コマンド (add, commit, push, pull, ..）
- 操作 (config, reflog, replace, ..)
- 調査 (blame, fsck, rerere, ..)
- 連携 (send-email, p4, svn, ..)

PLUMBING (63)

- 操作 (apply, commit-tree, update-ref, ..)
- 調査 (cat-file, for-each-ref, ..)
- 同期 (fetch-pack, send-pack, ..)
- 内部 (check-attr, sh-i18n, ..)

TOTAL: 145

## 新機能
ブランチの順番を上から更新順にしてくれる
```
git config --global branch.sort -committerdate
```

安全フォースプッシュ
```
git push --force-with-lease
```

メンテナンス
```
git maintenance start
```

## 役に立つコマンド

コミットされていない、修正箇所を表示
```
git diff
```

### git stash

一時的に保存
```
git stash save
```

リストを表示
```
git stash list
```

git stash drop (stash number) で保存されているものを削除
```
git stash drop
```

### git grep
コード上にあるものを検索する

```
git grep <search terms>
```

### git reflog
ローカル上で、ログ(pull, commit, push, reset等)が確認できる

```
git reflog
```

### git clean
変更されたファイルの変更内容を全て削除する

```
git clean
```