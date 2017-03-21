
`socat - Multipurpose relay (SOcket CAT)`

----------

```console
shell> socat TCP-LISTEN:25,reuseaddr,fork TCP:mailhost.example.com:25
shell> socat TCP-LISTEN:110,reuseaddr,fork TCP:mailhost.example.com:110
shell> socat TCP-LISTEN:143,reuseaddr,fork TCP:mailhost.example.com:143

shell> socat TCP-LISTEN:80,reuseaddr,fork TCP:www.example.com:80
```

```sh
(sudo socat TCP-LISTEN:25,reuseaddr,fork TCP:mailhost.example.com:25) &
(sudo socat TCP-LISTEN:25,reuseaddr,fork TCP:mailhost.example.com:25) &
(sudo socat TCP-LISTEN:25,reuseaddr,fork TCP:mailhost.example.com:25) &
```





```
socat TCP-LISTEN:1234,reuseaddr,fork EXEC:./helloworld
socat OPENSSL-LISTEN:443,cert=/cert.pem -
socat - OPENSSL:localhost:443
( sudo socat -T15 udp4-recvfrom:53,reuseaddr,fork tcp:localhost:5353 ) &

```







```
TCP-LISTEN:<port>
TCP4:<host>:<port>
TCP6:<host>:<port>
TCP:<host>:<port>

reuseaddr
fork
``` 
