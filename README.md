1.将websocket库和go库中fock到自己github里，创建data库
2.修改websocket库中的go.mod为 
```
module github.com/xldyswa(此处替换为你的id)/websocket

go 1.20

retract (
    v1.5.3 // tag accidentally overwritten
)

require golang.org/x/net v0.26.0
```
3.创建新的标签并提交（如果后面拉取的还是老版本的go.mod多创建几个新标签试试）
```
git tag v1.5.4
git push origin v1.5.4
```

4.拉取创建的data库
5.在data库添加自己的go,websocket子模块后提交更改到到git仓库
```
git submodule add git@github.com:xldyswa/go.git go
git submodule add git@github.com:xldyswa/websocket.git pkg/mod/github.com/xldyswa/websocket@v1.5.4
git submodule init
```
6.使用时拉取data库并将mod位置改成自己data库里的mod位置
```
git clone --recurse-submodules git@github.com:xldyswa/data.git
export GOMODCACHE=/home/ubuntu/data/pkg/mod
```
