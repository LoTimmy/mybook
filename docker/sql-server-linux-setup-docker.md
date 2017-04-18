```console
shell> sudo docker pull microsoft/mssql-server-linux
shell> docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -d microsoft/mssql-server-linux
shell> sudo docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=<YourStrong!Passw0rd>' -p 1433:1433 -v <host directory>:/var/opt/mssql -d microsoft/mssql-server-linux

shell> sudo docker pull microsoft/mssql-server-linux:latest
```

#### :books: 參考網站：
- [sql-server-linux-setup-docker](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-setup-docker)