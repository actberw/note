###python unittest

主要是四个类(TestLoader, TestCase, TestSuite, TestRunner), TestLoader(默认实例defaultTestLoader)有三个重要的函数:

- loadTestsFromTestCase
- loadTestsFromModule
- loadTestsFromName

TestLoader根据testMethodPrefix(test)查找创建TestCase, 创建TestSuit, TestRunner执行TestSuit.


        suite = unittest.defaultTestLoader.loadTestsFromTestCase(Test)
        unittest.TextTestRunner().run(suite)

####注: python2.7增加了discover方法可以根据pattern(test*.py)查找测试模块.

####refer:
- http://www.toptal.com/python/an-introduction-to-mocking-in-python
