## 我们本次学习了如何在linux中使用管道和tee将IO输出到文件
>
> ```strace ./hello.out 2>&1 | tee log.text```
> 
> 使用该命令后我们就能将./hello.out的所有系统调用过程传给log.text,我们可以在后续的操作中使用vim来对log.text的内容进行整理
>

## 我们本次还初步学习到了如何使用git来操作我们的repositories

> 我们首先需要通过
> ```git clone URL```
> 
> 来将我们的repositories复制到当前的linux目录下
>
> 我们进行修改后,需要依次输入
> ```git add *```
> ```git config --global user.email "我的邮箱"```
> ```git config --global user.name "我的用户名"```
> ```git commit -m "备注"```
> ```git push```
> ```
> 这个时候密码需要输入我们事先得到的token,具体介绍参考[这里](https://blog.csdn.net/qq_30049011/article/details/121182065?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522170360333316800222832264%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fall.%2522%257D&request_id=170360333316800222832264&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_ecpm_v1~rank_v31_ecpm-2-121182065-null-null.142^v98^pc_search_result_base2&utm_term=github%20token%E7%99%BB%E5%85%A5&spm=1018.2226.3001.4187)
> 但是这里会出现问题,我们每次push就会需要在密码处输入我们的token,这显然很难受,所以我们需要输入以下命令
> ```git remote set-url origin https://<your_token>@github.com/<USERNAME>/<REPO>.git```
> - <your_token>: 这里使用自己的token
> - <USERNAME>: 这里使用自己的用户名
> - <REPO>: 这里使用自己的仓库名称
>
> 示例:
> ```git remote set-url origin https://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@github.com/HelloWorldMyFriends/linux_study.git```	
> 完成后就不需要再复制麻烦的token啦~
>
> 后续还想要提交的话,顺序也是 add -> commit -> push 的三个步骤走
