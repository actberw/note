查看电脑的cpu是否支持虚拟化：输入命令 cat /proc/cpuinfo | grep flags ，查看结果中有没有 pae ，若有则支持半虚拟化，再看有没有 vmx(intel) 或 svm((amd) ，若有，则支持全虚拟化。这个要在 xen 安装之前做，安装后默认就看不到 vms/svm 了。
        http://roland.blog.51cto.com/227050/821166
http://en.wikipedia.org/wiki/Hardware_virtual_machine
http://www.ansen.org/openvz-xen-kvm-introduction-and-comparison.html
http://www.vpsee.com/2009/09/xen-vs-kvm-performance-and-scalabilit/
