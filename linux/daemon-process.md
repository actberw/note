### 守护进程  
#### 守护进程(daemon process)特点:  
1. PPID 为 1  
2. 控制终端(TTY, Teletypes) 为"?"  
3. 守护进程必须与其运行前的环境隔离开来，包括未关闭的文件描述符，控制终端，会话，工作目录，以及umask等。这些都是从父进程继承过来的。   
  
#### 创建守护进程的步骤:  
1. fork创建子进程, 父进程退出  
2. 调用setsid() 创建新会话  
3. 再次fork，父进程退出  
4. 将当前工作目录改为根目录  
5. 设定uamsk值为0  
6. 关闭不必要的文件描述符  
7. 打开/dev/null，dup2(0, 1, 2)  