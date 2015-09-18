###制作deb包
本文以mysql-dev制作为例
1. 需要安装依赖`sudo apt-get install dh-make`
2. 准备好要做成deb的目录，格式:包名-版本号
3. dh_make -s -e wangjian@admaster.com.cn -f ../libmysqlclient-dev-18.1.0.tar.gz
4. dpkg-buildpackage -rfakeroot -b
