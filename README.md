1.从websocket和go中fock到自己仓库，创建data库
2.修改websocket的go.mod为 
```
module github.com/xldyswa(此处替换为你的id)/websocket

go 1.20

retract (
    v1.5.3 // tag accidentally overwritten
)

require golang.org/x/net v0.26.0
```
3.创建新的标签并提交
```
git tag v1.5.4
git push origin v1.5.4
```

4.拉取创建的data库
5.添加go,websocket子模块
```
git submodule add git@github.com:xldyswa/go.git go
git submodule add git@github.com:xldyswa/websocket.git pkg/mod/github.com/xldyswa/websocket@v1.5.4
git submodule init
```
6.将mod指向自己data库里的mod
```
git clone --recurse-submodules git@github.com:xldyswa/data.git
export GOMODCACHE=/home/ubuntu/data/pkg/mod
```
