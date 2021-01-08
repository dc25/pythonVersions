# Demo showing a way to use docker to work with multiple python versions 
```
$ cat aliases 
function dx
{
  sudo docker run -it --rm -v `pwd`:`pwd` -w `pwd` "$@"
}

function p8
{
  dx python:3.8-slim python "$@"
}

function p7
{
  dx python:3.7-slim python "$@"
}

$ . aliases 

$ cat main.py 
#!/usr/bin/env python
import sys
print("Hello from Python, yay")
print(sys.version)

$ p7 main.py 
Hello from Python, yay
3.7.9 (default, Dec 11 2020, 14:53:17) 
[GCC 8.3.0]

$ p8 main.py 
Hello from Python, yay
3.8.7 (default, Dec 22 2020, 18:57:26) 
[GCC 8.3.0]
```
