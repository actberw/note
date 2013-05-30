### 关于process user id
1. 实际用户ID(real user id), 执行程序得用户id
2. 有效用户ID(effective user id), 当设置了设置用户id(set user id bit)时，当执行次文件时有效用户ID设置为文件所有者得ID
3. 保存设置用户ID, 由exec复制有效用户ID而来得

几组测试,代码:  

    #include <stdio.h>
    #include <unistd.h>
    #include <sys/types.h>

    int main(void) {
        uid_t r_uid, e_uid;
        r_uid = getuid();
        e_uid = geteuid();
        printf("Real User ID:\t%d\nEffect User ID:\t%d\n", r_uid, e_uid);
    }

直接gcc 编译.  
测试实际用户ID  
    
    $ ls -al ./a.out
    -rwxr-xr-x 1 actberw actberw 7085 May 30 22:54 ./a.out
    $ id
    uid=1000(actberw) gid=1000(actberw) groups=1000(actberw)
    $ ./a.out
    Real User ID:   1000
    Effect User ID: 1000

    $ sudo ./a.out
    Real User ID:   0
    Effect User ID: 0

测试有效用户ID  

    $ chmod u+s ./a.out #设置设置用户ID
    $ ls -al ./a.out 
    -rwsr-xr-x 1 actberw actberw 7.0K May 30 22:54 ./a.out
    $ ./a.out
    Real User ID:   1000
    Effect User ID: 1000
    
    $ sudo ./a.out
    Real User ID:   0
    Effect User ID: 1000

测试进程创建得文件权限  
代码:

    #include <stdio.h>

    #include <unistd.h>
    #include <fcntl.h>
    #include <sys/types.h>
    #define USER_RW (S_IRUSR|S_IWUSR)

    int main(void) {
        uid_t r_uid, e_uid;
        int fd;
        r_uid = getuid();
        e_uid = geteuid();
        printf("Real User ID:\t%d\nEffect User ID:\t%d\n", r_uid, e_uid);
        fd = open("./stat.log", O_CREAT, USER_RW);
        write(fd, "actberw", 7);
        close(fd);
    }

直接gcc编译  

    $ chmod u+s ./a.out
    $ sudo ./a.out 
    Real User ID:   0
    Effect User ID: 1000
    $ ls -al stat.log
    -rw------- 1 actberw root 0 May 30 23:20 stat.log  # 所有者是effective id
