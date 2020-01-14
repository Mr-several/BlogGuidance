# Push时出现的问题

1. Git 提示fatal: remote origin already exists 错误解决办法
这是因为我们之前绑定了一个不正确的远程库，应该首先取消之前的关联。
`$ git remote rm origin`
之后使用git remote add重新绑定就可以了

2. git 使用以及 部分错误 [rejected] master -> master (fetch first)(non-fast forward)
这是因为远程的服务端和我们的本地文件不匹配需要同步一下。
git pull --rebase https://XXXX.git master
git add.
git commit -m "test"
git push -u origin master