`ss`

```
# Display all TCP sockets.
shell> ss -t -a

# Display all UDP sockets.
shell> ss -u -a

# Display all established ssh connections.
shell> ss -o state established '( dport = :ssh or sport = :ssh )'

shell> ss -l
shell> ss -lt
```
