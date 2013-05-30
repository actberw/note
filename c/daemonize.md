### daemonize c 实现

原理看[../linux/daemon-process.md](../linux/daemon-process.md)

    #include <unistd.h>

    int daemonize(void) {
        int  fd;

        switch (fork()) {
        case -1:
            //log_error(NGX_LOG_EMERG, log, ngx_errno, "fork() failed");
            return NGX_ERROR;

        case 0:
            break;

        default:
            exit(0);
        }

        ngx_pid = ngx_getpid();

        if (setsid() == -1) {
            ngx_log_error(NGX_LOG_EMERG, log, ngx_errno, "setsid() failed");
            return NGX_ERROR;
        }

        umask(0);
        chdir('/')

    
        fd = open("/dev/null", O_RDWR);
        if (fd == -1) {
            ngx_log_error(NGX_LOG_EMERG, log, ngx_errno,
                          "open(\"/dev/null\") failed");
            return NGX_ERROR;
        }

        if (dup2(fd, STDIN_FILENO) == -1) {
            ngx_log_error(NGX_LOG_EMERG, log, ngx_errno, "dup2(STDIN) failed");
            return NGX_ERROR;
        }

        if (dup2(fd, STDOUT_FILENO) == -1) {
            ngx_log_error(NGX_LOG_EMERG, log, ngx_errno, "dup2(STDOUT) failed");
            return NGX_ERROR;
        }
