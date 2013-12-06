### ubuntu install salt

#### 安装
1. install `sudo aptitude install m2crypto`
2. `sudo pip install salt`

#### 启动

1. `sudo salt-minion -d` or `sudo salt-master -d`

#### 停止

1. `kill -TERM pid`

#### 证书授权

在master上执行`salt-key -L`, 执行`salt-key -a name` 添加未授权的证书。
