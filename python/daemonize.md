### python daemon代码
原理看[../linux/daemon-process.md](../linux/daemon-process.md)

    import os

    def daemonize():
        pid = os.fork()
        if pid:
            # The forked process also has a handle on resources, so we
            # *don't* want proper termination of the process, we just
            # want to exit quick (which os._exit() does)
            os._exit(0)

        # Make this the session leader
        os.setsid()

        # @@: Should we set the umask and cwd now?
        os.umask(0)
        os.chdir('/')

        # Fork again for good measure!
        pid = os.fork()
        if pid:
            os._exit(0)
        # close unnecessary fd
        import resource  # Resource usage information.
        maxfd = resource.getrlimit(resource.RLIMIT_NOFILE)[1]
        if (maxfd == resource.RLIM_INFINITY):
            maxfd = MAXFD
        # Iterate through and close all file descriptors.
        for fd in range(0, maxfd):
            try:
                os.close(fd)
            except OSError:  # ERROR, fd wasn't open to begin with (ignored)
                pass

        if (hasattr(os, "devnull")):
            REDIRECT_TO = os.devnull
        else:
            REDIRECT_TO = "/dev/null"

        # Duplicate standard input to standard output and standard error.
        os.open(REDIRECT_TO, os.O_RDWR)  # standard input (0) aready 0
        os.dup2(0, 1)  # standard output (1)
        os.dup2(0, 2)  # standard error (2)
