# webapp.py, webapp_bootstrap.py

* Error: line 19 `TypeError: a bytes-like object is required, not 'str'`
* Cause: msg is a byte object, not a string as written in the Popen documentation, *If text mode is not used, stdin, stdout and stderr will be opened as binary streams* [https://docs.python.org/3.6/library/subprocess.html#frequently-used-arguments]
* Solution: add in the call of subprocess.Popen `universal_newlines=True`