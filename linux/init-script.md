###linux 管理系统启动脚本
主要介绍debian(sysv) 和 centos(bsd)两种风格的管理init脚本的工具, 以 UNIX System V init 进程为基础的, 目前还有两种替代方案：upstart 和 systemd(参见refer#1), 暂不做介绍.
1. 首先介绍下linux运行级别(查看另一篇runlevel笔记)
2. debian中默认安装了sysv-rc(或者sysv-rc-conf一个TUI), 包含两个重要的命令:update-rc.d, invoke-rc.d
3. centos中用chkconfig和initscripts, chkconfig提供一个chkconfig的命令, initscripts主要是service命令.

####refer:
- http://www.ibm.com/developerworks/cn/linux/l-lpic1-v3-101-3/
- http://mylxiaoyi.bokee.com/5747022.html
