# Git

## ssh免密登录

``` tex
ssh-keygen -t rsa -C "xxxx@xxx.com" // 连续三次回车
```

 在命令中找到秘钥路径下id_rsa和id_rsa.pub文件，或者输入

``` tex
cat ~/.ssh/id_rsa.pub
```

登录gitee，将.pub文件的内容粘贴进去，输入代码测试：

``` tex
ssh -T git@gitee.com // 测试是否成功即可
```

## 删除历史提交记录

``` tex
git pull
git checkout --orphan latest_branch
git add -A
git commit -am "init"
git branch -D master
git branch -m master
git push -f origin master
git branch --set-upstream-to=origin/master master
```

