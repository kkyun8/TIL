# git cheatsheet

## pull request

```bash
# pull request commitをローカルにpullする
# PRブランチのことはリモートの「refs/pull/{PR NUMBER}/head」で管理してある。
git pull origin pull/{PR NUMBER}/head:{BRANCH NAME}
```


## branch & checkout

```bash
# Remote Branchをそのままローカルに配置
git checkout -t origin/BRANCH_NAME
# Remote Branch名を変更してローカルに配置
git checkout -b local_branch_name origin/remote_branch_name
```

## Delete Untracked files

```bash
# commit & add されてないローカルファイルを削除
git clean -df
```

## stash

```bash
# 保存された Stash 確認
git stash list
# 名前なしで現在の変更点を保存
git stash
# 名前を指定して変更点を保存
git stash save "default"
# 保存された Stash を workspace に戻して、stash 一覧から削除、一時保存したstashに使う
git stash pop //最近のもの対象
git stash pop stash@{N}
# Apply
git stash apply //最近のもの対象
git stash apply stash@{N}
stash@{N} 
# Delete
git stash drop //最近のもの対象
git stash drop stash@{N}
```

