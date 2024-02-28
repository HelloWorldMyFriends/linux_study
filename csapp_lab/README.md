## 学习记录
TODO
### attack lab记录

####ctarget 

#####level1
level1需要我们在getbuf函数的栈帧上改写ret的地址,即原先是返回到test的0x401976,我们知道Gets函数会在0x5561dc78处开始插入基于我们编写的文件变形的文件xxx-raw.txt,于是在0x5561dca0处将0x401976改写为touch1的首地址0x4017c0,于是下一步的ret指令会返回至touch1函数,达到我们的目的



####level2
level2需要我们在改写getbuf栈帧的基础上,给rdi寄存器赋值cookie的值,cookie可以从内存查出值为0x59b997fa,于是我们需要实现两个任务:rdi寄存器的赋值和touch2首地址的返回,我们由于是写入内存,所以这些指令都要以opcode的形式插入.
我们可以这样:
```assembly
mov $0x59b997fa, %rdi
push $4017c0
ret 
```


####level3