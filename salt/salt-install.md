### ubuntu install salt

1. 安装
        
        # ubuntu
        sudo aptitude install m2crypto python-dev 
        # centos 
        # sudo yum install python-devel m2crypto
        sudo pip install salt==0.17.2
        # 查看版本
        salt --version
2. 配置

3. 启动
        
        # 启动主结点
        sudo salt-master -d
        # 启动子结点
        sudo salt-minion -d

4. 停止

        kill -TERM pid

4. 证书授权
在master上执行`salt-key -L`, 执行`salt-key -a name` 添加未授权的证书。

注: 0.17.2的 master有一个bug，具体见refer#1
####refer:
 - https://github.com/saltstack/salt/issues/8176
