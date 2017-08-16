![](https://raw.githubusercontent.com/docker-library/docs/master/mono/logo.png)

MyProject

```csharp
// Hello1.cs
class Hello1
{
   static void Main()
   {
      System.Console.WriteLine("Hello, World!");
   }
}

/* */
```

```
編譯 Hello1.cs 產生 Hello1.exe
dmcs Hello1.cs
gmcs Hello1.cs

編譯 Hello1.cs 和建立 My.exe
dmcs Hello1.cs -out:My.exe
gmcs Hello1.cs -out:My.exe

dmcs -optimize Hello1.cs


mono Hello1.exe
```



```csharp
// Hello2.cs
using System;

class Hello2
{
   static void Main()
   {
      Console.WriteLine("Hello, World!");
   }
}
```


```csharp
// Hello3.cs
// arguments: A B C D
using System;

class Hello3
{
   static void Main(string[] args)
   {
      Console.WriteLine("Hello, World!");
      Console.WriteLine("You entered the following {0} command line arguments:",
         args.Length );
      for (int i=0; i < args.Length; i++)
      {
         Console.WriteLine("{0}", args[i]); 
      }
   }
}
```

```csharp
// Hello4.cs
using System;

class Hello4
{
   static void Main(string[] args)
   {
      string myName ="N/A";
      int myAge = 0;
      Console.WriteLine(myName, myAge);
   }
}

```




```csharp
using System;
 using System.Data;
 using MySql.Data.MySqlClient;
 
 public class Test
 {
    public static void Main(string[] args)
    {
       string connectionString =
          "Server=172.17.42.1;" +
          "Port=49155;" +
          "Database=test;" +
          "User ID=root;" +
          "Password=mysecretpassword;" +
          "Pooling=false";
       IDbConnection dbcon;
       dbcon = new MySqlConnection(connectionString);
       dbcon.Open();
       IDbCommand dbcmd = dbcon.CreateCommand();
       // requires a table to be created named employee
       // with columns firstname and lastname
       // such as,
       //        CREATE TABLE employee (
       //           firstname varchar(32),
       //           lastname varchar(32));
       string sql =
           "SELECT firstname, lastname " +
           "FROM employee";
       dbcmd.CommandText = sql;
       IDataReader reader = dbcmd.ExecuteReader();
       while(reader.Read()) {
            string FirstName = (string) reader["firstname"];
            string LastName = (string) reader["lastname"];
            Console.WriteLine("Name: " +
                  FirstName + " " + LastName);
       }
       // clean up
       reader.Close();
       reader = null;
       dbcmd.Dispose();
       dbcmd = null;
       dbcon.Close();
       dbcon = null;
    }
 }
```



```
shell> mkdir mysql-connector-net
shell> cd mysql-connector-net
shell> wget https://dl.dropboxusercontent.com/u/4276183/mysql-connector-net-1.0.10-noinstall.zip
shell> unzip mysql-connector-net-1.0.10-noinstall.zip
shell> gacutil -i MySql.Data.dll 
Installed MySql.Data.dll into the gac (/usr/lib/mono/gac)

shell> mcs TestExample.cs -r:System.Data.dll -r:/path/to/MySql.Data.dll
shell> mono TestExample.exe
>>>>>>> 668cce56c488474ad44d7328411a5c3af28c7df3
```

```
shell> apt-get install apache2
shell> service apache2 stop
shell> apt-get install mono-apache-server2 libapache2-mod-mono libmono-i18n2.0-cil
shell> apt-get install mono-apache-server4 libapache2-mod-mono libmono-i18n4.0-cil
shell> service apache2 start
shell> a2dismod mod_mono
shell> a2enmod mod_mono_auto

shell> mono --version

Mono JIT compiler version 3.2.8 (Debian 3.2.8+dfsg-4ubuntu1)
Copyright (C) 2002-2014 Novell, Inc, Xamarin Inc and Contributors. www.mono-project.com
	TLS:           __thread
	SIGSEGV:       altstack
	Notifications: epoll
	Architecture:  amd64
	Disabled:      none
	Misc:          softdebug 
	LLVM:          supported, not enabled.
	GC:            sgen

shell> vim /etc/apache2/sites-enabled/000-default.conf

    Alias /aspnet "/var/www/aspnet"
#    MonoServerPath aspnet "/usr/bin/mod-mono-server2"
    MonoServerPath aspnet "/usr/bin/mod-mono-server4"
    MonoDebug aspnet true
    MonoSetEnv aspnet MONO_IOMAP=all
    MonoApplications WebService "/aspnet:/var/www/aspnet"

    <Location "/aspnet">
        Allow from all
        Order allow,deny
        MonoSetServerAlias aspnet
        SetHandler mono
        SetOutputFilter DEFLATE
        SetEnvIfNoCase Request_URI "\.(?:gif|jpe?g|png)$" no-gzip dont-vary
    </Location>

    <IfModule mod_deflate.c>
        AddOutputFilterByType DEFLATE text/html text/plain text/xml text/javascript
    </IfModule>

shell> cd /var/www/aspnet
shell> vim hello.aspx
```

```csharp
<%@ Page Language="C#" %>
<html>
<head>
   <title>Sample Calendar</title>
</head>
<asp:calendar showtitle="true" runat="server">
</asp:calendar>
```


dotnetcore

.NET Core

Install for Ubuntu 14.04, 16.04 & Linux Mint 17

```
 OS Name:     ubuntu
 OS Version:  14.04
 OS Platform: Linux
 RID:         ubuntu.14.04-x64
```

```
shell> sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
shell> sudo apt-key adv --keyserver apt-mo.trafficmanager.net --recv-keys 417A0893
shell> sudo apt-get update
```

```
shell> sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
shell> sudo apt-key adv --keyserver apt-mo.trafficmanager.net --recv-keys 417A0893
shell> sudo apt-get update
```

```
shell> sudo apt-get install dotnet-dev-1.0.0-preview2-003121
shell> dotnet --version
shell> dotnet --info
```

```
shell> mkdir hwapp
shell> cd hwapp
shell> dotnet new
```

```
shell> dotnet restore
shell> dotnet run
```

.NET Core SDK = Develop apps with .NET Core and the SDK+CLI (Software Development Kit/Command Line Interface) tools
.NET Core = Run apps with the .NET Core runtime

```csharp
using System;

namespace ConsoleApplication
{
    public class Program
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

```
shell> git clone https://github.com/aspnet/cli-samples.git
shell> cd cli-samples/HelloMvc
shell> dotnet restore
shell> dotnet publish -c Release --output /srv/aspnet
shell> dotnet /srv/aspnet/HelloMvc.dll
```



---

#### :books: 參考網站：
- [core#ubuntu](https://www.microsoft.com/net/core#ubuntu)
- [dotnet](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0.md)

- [dotnet](https://dotnet.github.io/)
- [connector-net-installation-unix](http://dev.mysql.com/doc/connector-net/en/connector-net-installation-unix.html)
- [](http://msdn.microsoft.com/en-us/library/aa288463(v=vs.71).aspx)
- [](http://msdn.microsoft.com/zh-tw/library/z1zx9t92%28v=vs.80%29.aspx)
- [](http://msdn.microsoft.com/zh-tw/library/78f4aasd(v=vs.80).aspx)
- [https://registry.hub.docker.com/_/mono/](https://registry.hub.docker.com/_/mono/)
- [](http://www.mono-project.com/docs/database-access/providers/mysql/)
- [Mono Basics](http://www.mono-project.com/docs/getting-started/mono-basics/)
- [](http://msdn.microsoft.com/zh-tw/library/015103yb(v=vs.100).aspx)
