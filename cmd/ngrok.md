
ngrok

Step 1: Download ngrok
```console
shell> wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
```

Step 2: Unzip it
```console
shell> unzip /path/to/ngrok.zip
```

Step 3: Run it!
```console
shell> ./ngrok -help
shell> ngrok http 80
```

```
NAME:
   ngrok - tunnel local ports to public URLs and inspect traffic

DESCRIPTION:
    ngrok exposes local networked services behinds NATs and firewalls to the
    public internet over a secure tunnel. Share local websites, build/test
    webhook consumers and self-host personal services.
    Detailed help for each command is available with 'ngrok help <command>'.
    Open http://localhost:4040 for ngrok's web interface to inspect traffic.

EXAMPLES:
    ngrok http 80                    # secure public URL for port 80 web server
    ngrok http -subdomain=baz 8080   # port 8080 available at baz.ngrok.io
    ngrok http foo.dev:80            # tunnel to host:port instead of localhost
    ngrok tcp 22                     # tunnel arbitrary TCP traffic to port 22
    ngrok tls -hostname=foo.com 443  # TLS traffic for foo.com to port 443
    ngrok start foo bar baz          # start tunnels from the configuration file

VERSION:
   2.0.25

AUTHOR:
  inconshreveable - <alan@ngrok.com>

COMMANDS:
   authtoken	save authtoken to configuration file
   credits	prints author and licensing information
   http		start an HTTP tunnel
   start	start tunnels by name from the configuration file
   tcp		start a TCP tunnel
   test		test ngrok service end-to-end
   tls		start a TLS tunnel
   update	update ngrok to the latest version
   version	print the version string
   help		Shows a list of commands or help for one command
```

`Password Protected`
```console
shell> ngrok http -auth "user:password" 80
```

`TCP Tunnels`
```console
shell> ngrok tcp 22
```

`Your Tunnel Authtoken`
```console
shell> ngrok authtoken 2EGEMGEzckqpWC7BYyGjh_4vAPMtumGJX7mjM8rNBYD
```

--

#### :books: 參考網站：
- [download](https://ngrok.com/download)
- [Windows](https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-windows-amd64.zip)
- [Mac OS X](https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-darwin-amd64.zip)

