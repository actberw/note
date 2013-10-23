#### lzo 及python binding安装
1. 安装lzo

    $ wget http://www.oberhumer.com/opensource/lzo/download/lzo-2.06.tar.gz
    $ tar zxvf lzo-2.06.tar.gz
    $ cd lzo-2.06
    $ ./configure CFLAGS=-fPIC
    $ make 
    $ make install

2. python binding 安装

    $ git clone https://github.com/jd-boyd/python-lzo.git
    $ cd python-lzo
    $ sudo python setup.py install

