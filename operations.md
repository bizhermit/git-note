# Git操作

## リモートリポジトリ確認

```bash
git remote -v
```

## リモートリポジトリ追加

```bash
git remote add [remote-name] [url]
# e.g.
git remote add origin https://github.com/bizhermit/git-note.git
```

## リモートリポジトリ削除

```bash
git remote remove [remote-name]
# e.g.
git remote remove origin
```

## ブランチ確認

```bash
git branch
```

## ブランチ作成

```bash
git branch [new-branch-name]
# e.g.
git branch issue/#1
```

作成と切り替え

```bash
git switch -c [new-branch-name]
# e.g.
git switch -c issue/#1
```

## ブランチ切り替え

```bash
git switch [switch-branch-name]
# e.g.
git switch issue/#1
```

## ブランチのマージ

基本的にNonFastForwardを使用する
```bash
git switch [dest-branch-name]
git merge --no-ff [src-branch-name] -m "[comment]"
# e.g.
git switch main
git merge --no-ff issue/#1 -m "close #1"
```

デフォルトでNonFastForwardになるよう設定可。  
[マージのNonFastForward](settings.md/#マージのnonfastforward)

## ブランチのマージ取り消し

コンフリクト対応前
```bash
git merge --abort
```

コンフリクト対応後（マージ完了前）
```bash
git reset --hard HEAD
```

マージ完了後
```bash
git revert --hard ORIG_HEAD
```

## ブランチ削除（ローカルリポジトリ）

```bash
git branch -d [delete-branch-name]
# e.g.
git branch -d issue/#1
```

強制削除（未コミット有り？の場合等）
```bash
git branch -D [delete-branch-name]
```
## ブランチ削除（リモートリポジトリ）

```bash
git push origin :[delete-branch-name]
```

## ブランチの同期（リモートリポジトリからローカルリポジトリ）

```bash
git fetch -p
```

## ブランチ名変更

```bash
git branch -m [old-branch-name] [new-branch-name]
# e.g.
git branch -m master main
```

上書き変更
```bash
git branch -M [old-branch-name] [new-branch-name]
```

## 変更をステージ

```bash
git add [file-name]
```

変更全部
```bash
git add .
```

## ローカルリポジトリにコミット

```bash
git commit -m "[comment]"
```

## コミット取り消し

直前
```bash
git reset --soft HEAD
```

回数指定
```bash
git reset --soft HEAD~{n}
# e.g. ２つ前までのコミットを削除
git reset --soft HEAD~2
```

コミットID指定
```bash
git reset --soft [commit-id]
```

## リモートリポジトリに公開

```bash
git push [remote-name] [branch-name]
# e.g.
git push origin master
```

## ローカルリポジトリを更新（リモートリポジトリから）

```bash
git fetch [remote-name]
# e.g.
git fetch
git fetch origin
```

## ワークツリーを更新（ローカルリポジトリから）

```bash
git merge [remote-name]/[branch-name]
# e.g.
git merge
git merge origin/main
```

## ローカルリポジトリとワークツリーを更新（リモートリポジトリから）

```bash
git pull [remote-name] [branch-name]
# e.g.
git pull
git pull origin main
```

## タグ作成

```bash
git tag "[tag-name]"
git push [remote-name] tags/[tag-name]
# e.g.
git tag v1.0.0
git push origin tags/v1.0.0
```

## タグ削除

```bash
git tag -d [tag-name]
git push origin :[tag-name]
```

## タグ（リモートリポジトリ）確認

```bash
git ls-remote --tags
```