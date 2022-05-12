# 設定

## マージのNonFastForward

mergeをデフォルトでNonFastForwardが有効になるように変更  
ただしpullの場合は対象外

```bash
git config --add merge.ff false
git config --add pull.ff only
```

以降、
NonFastForward
```bash
git merge [src-branch-name] -m "[comment]"
```
FastForward
```bash
git merge --ff [src-branch-name] -m "[comment]"
```