
# xifengblog
edit my github.io blog
在没有环境的机子上，先安装环境，然后npm install.
然后安装npm install hexo-deployer-git --save
再之后使用hexo命令创建文件，编辑号博客后，hexo deploy提交即可。
参考：
官网：https://hexo.io/zh-cn/docs/deployment.html
搭建：
http://crazymilk.github.io/2015/12/28/GitHub-Pages-Hexo%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2/#more

http://opiece.me/2016/03/12/concise-to-next/（next主题）

next主题：
http://theme-next.iissnan.com/getting-started.html

http://opiece.me/2016/03/12/concise-to-next/

配置disqus：
http://blog.csdn.net/xiongyangg/article/details/50756904

每次使用hexo deploy发送到qianhongxin.github.io时，先将站点下的.deploy_git删除，然后再用那个命令

使用：
http://opiece.me/2015/04/09/hexo-guide-2/
http://wuchong.me/blog/2014/01/17/use-github-to-manage-hexo-source/

更新指南：
先在此项目上利用hexo命令，创建文章，然后hexo server看看效果。可以的话，执行
hexo deploy 将.deploy_git提交到qianhongxin.github.io仓库中，然后子啊xifengblog中commit，然后将修改提交到远程xifengblog中。
