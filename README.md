# Using docker to work with multiple python versions 
```
$ cat aliases
function dx
{
  sudo docker run -it --rm -v `pwd`:`pwd` -w `pwd` "$@"
}

function p3.8
{
  dx python:3.8-slim "$@"
}

function p3.7
{
  dx python:3.7-slim "$@"
}

$ . aliases

$ cat main.py 
#!/usr/bin/env python
import sys
print("Hello from Python, yay")
print(sys.version)

$ p3.7 ./main.py 
Hello from Python, yay
3.7.9 (default, Dec 11 2020, 14:53:17) 
[GCC 8.3.0]

$ p3.8 ./main.py 
Hello from Python, yay
3.8.7 (default, Dec 22 2020, 18:57:26) 
[GCC 8.3.0]

$ p3.7 python main.py 
Hello from Python, yay
3.7.9 (default, Dec 11 2020, 14:53:17) 
[GCC 8.3.0]

$ p3.8 python main.py 
Hello from Python, yay
3.8.7 (default, Dec 22 2020, 18:57:26) 
[GCC 8.3.0]

$ p3.7 python
Python 3.7.9 (default, Dec 11 2020, 14:53:17) 
[GCC 8.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> print ("hi")
hi
>>> exit()
$ 
```
