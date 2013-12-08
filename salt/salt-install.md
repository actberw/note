### ubuntu install salt

1. 安装

        sudo aptitude install m2crypto python-dev
        sudo pip install salt
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
