### gevent 

1. simple demo

    import gevent

    def foo():
        print "Running foo func"
        gevent.sleep(0)

    def bar():
        print "Running bar func"
        gevent.sleep(0)

    gevent.joinall([
        gevent.spawn(foo), # gevent.spawn is shorthand of Greenlet.spawn
        gevent.spawn(bar)
    ])


