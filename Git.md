## リモートリポジトリの最新の状態を取得

```
git fetch
```

## リモートリポジトリの最新の状態を取得しマージする

```
git pull
```

## マージする

```
git merge
```

## 修正を行ったファイルの確認

```
git status
```

## 修正を行ったファイル全てステージング環境へ追加する

```
git add .
```

## コミットする

```
git commit -m "コミットメッセージ"
```

## ブランチの確認

```
git branch
```

## ブランチの切り替え

```
git switch ブランチ名
```

## ブランチを作成し切り替え

```
git switch -c ブランチ名
```

## 修正ファイルの退避

```
git stash -u
```

## 退避した作業を確認

```
git stash list
```

## 退避した作業を復元

```
git stash apply stash@{0}
```

## 退避した作業を削除

```
git stash drop stash@{0}
```

## 退避した作業を復元+削除

```
git stash pop stash@{0}
```

## 別ブランチでコミットされたものを取り込む

```
git cherry-pick -n コミット ID
```

## コミットを取り消す

```
git reset --soft HEAD^
```

## コミットメッセージを修正

```
git commit --amend -m "修正メッセージ"
```

## コミットメッセージはそのままでコミット

```
git commit --amend --no-edit
```
