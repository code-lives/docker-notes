# 生成证书

```
ssh-keygen -t rsa -C "18734351007@163.com"
```

# 操作规范

### 拉取分支代码

```
    git clone xxx -b string
```

### 创建本地分支，开发&修复...

```
    git checkout -b feat/xxxx
```

### 开发完成后

```
    git add .
    git commit -m "feat: do something" --all
    git log //查看CommitID
```

### 切换测试分支，把改动代码合并

```
    git checkout staging
    git cherry-pick {CommitID}
    git push
```

### 创建 PR

```
    git checkout feat/xxxx
    git push
    # push完成之后会看见，合并链接。
```

### commit

```
    feat：新功能（feature）
    fix：修补bug
    docs：文档（documentation）
    style： 格式（不影响代码运行的变动）
    refactor：重构（即不是新增功能，也不是修改bug的代码变动）
    test：增加测试
    chore：构建过程或辅助工具的变动
```
