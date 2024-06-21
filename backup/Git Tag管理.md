删除本地 tag
```shell
git tag -d $(git tag -l)
```

删除远程 tag
```shell
git push origin --delete $(git tag -l)

git push origin --delete refs/tags/<tag_name>
```

```text
实际在删除所有远程tag的时候
需要先删除本地所有tag
然后拉最新的所有tag
然后根据本地tag的名字删除所有远程tag
```