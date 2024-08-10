<img src="https://socialify.git.ci/kagomen/git-tutorial/image?description=1&descriptionEditable=Git%E3%81%A8GitHub%E3%81%AE%E3%83%86%E3%82%B9%E3%83%88%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%E2%9C%8D%EF%B8%8F&logo=https%3A%2F%2Fkagome.dev%2Ficon.png&name=1&owner=1&pattern=Circuit%20Board&stargazers=1&theme=Light" alt="git-tutorial" width="640" height="320" />

## 基本的な流れ

#### 1. GitHub(Web)で新しいリポジトリを作る

- リポジトリ名を`<アカウント名>.github.io`とすると自動的に GitHub Pages が生成され、URL が`<アカウント名>.github.io`になる

#### 2. clone する

- `cd desktop`などとして任意のディレクトリに移動し、`git clone <リポジトリのURL>`を実行する

#### 3. branch を切る

1. `git branch <ブランチ名>`を実行してブランチを作成する
1. `git switch <ブランチ名>`を実行して作成したブランチに移動する
1. ソースコードを自由に編集する^. \_ . ^
   - ブランチ名の例
     - docs/#01_create_documents
     - feat: 新機能追加関連
     - docs: ドキュメント関連
     - fix: バグ修正関連

- 慣れたら`git switch -c <ブランチ名>`でブランチの作成と移動を同時に行なっても OK

#### 4. push する

- 以下を実行して GitHub に push する

```
git add .
git commit -m "コミットメッセージを記入"
git push origin <ブランチ名>もしくはHEAD
// コミットメッセージの例
// docs: README.mdの日本語訳を追加 #12
```

#### 5. プルリクエストを送る

- GitHub のページでプルリクエストを送り、`merge`を待つ！！！

---

## こんなときどうする？

### コミットメッセージを変更したい

```
git commit --amend
// i でインサートモードに
// esc でインサートモードから離脱
// :wq で保存
git push origin <ブランチ名>もしくはHEAD --force
// 他の開発者が同じブランチを使用している場合は要注意
```

### コミットをまとめたい

1. `git log --oneline`で戻りたいハッシュ番号をコピー
1. git reset <ハッシュ番号>
   // reset option のデフォルトは`--mixed`
1. 内容を確認し、改めて`add`と`commit`をする

- reset option のデフォルト値は`--mixed`なので、ワークツリーにソースコードは残る
- `git reset --hard`とするとソースコードは残らないので注意！

### ブランチ名を間違えたので修正したい

```
git branch -m <間違えたブランチ名> <希望のブランチ名>
```

### ブランチを編集内容ごと削除したい

```
git branch -D <削除したいブランチ名>
// git branch -d <ブランチ名>はマージ後のみ実行可能
```

### gitmoji を使用する場合

1. `git add .`
1. `gitmoji -c`
1. タイトルを入力（コミットメッセージではない）
1. コミットメッセージを入力
1. `git push origin <ブランチ名>もしくはHEAD`

---

## 知恵袋

### マージについて

マージには 2 種類ある

- fast-forward
- no fast-forward

マージされた履歴を明示的に残したい場合は、以下を実行する

```
git merge <マージしたいブランチ名> --no-ff -m "<ブランチ名>をマージしました"
```

マージが完了したら不要なブランチを削除する

```
git branch -d <ブランチ名>
```

---

## お役立ちリンク

[基本的な書き方とフォーマットの構文 -GitHub Docs](https://docs.github.com/ja/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
