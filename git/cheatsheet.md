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
```

## Delete Untracked files

```bash
# commit & add されてないローカルファイルを削除
git clean -df
```


