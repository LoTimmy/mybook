
```
shell> choco install pstools -y
```

```
shell> cmdkey /add:targetname /user:username /pass:password
shell> psexec \\targetname cmd
shell> psexec -s -d -i 1 \\targetname "c:\program files\internet explorer\iexplore.exe"
shell> cmdkey /delete:targetname
```

```
shell> cmdkey /add:10.27.55.201 /user:Administrator /pass:password
shell> psexec \\10.27.55.201 cmd
shell> cmdkey /delete:10.27.55.201
```

```
shell> cmdkey /list
shell> cmdkey /add:server01 /user:mikedan /pass:Kleo
shell> cmdkey cmdkey /delete:Server01
```

```
shell> psping -n 10 -w 3 targetname

pskill iexplore.exe
pslist \\targetname 
pslist \\targetname -e iexplore 

FINDSTR

%date%
%time%

@echo off


:end
echo End of batch program.
 
```


psexec -s -d -i 1 \\10.27.55.201 "c:\program files\internet explorer\iexplore.exe"



@ECHO OFF

IF ERRORLEVEL 0 goto okay

if not errorlevel 1 goto end


FINDSTR


@echo off

if '%OS%'=='Windosws_NT' goto good

:good

goto finish
:finish

@pslist \\targetname
@if errorlevel 1 goto failed 


%OS%  
**Windows_NT**
%date%
**2015/11/19 週四**
%date:~5,2%
**11**


#### :books: 參考網站：

[](https://technet.microsoft.com/zh-tw/library/cc754335(v=ws.10).aspx)
[cmdkey](https://technet.microsoft.com/zh-tw/library/cc754243(v=ws.10).aspx)
[PsTools](https://technet.microsoft.com/en-us/sysinternals/bb896649.aspx)
[psexec](https://technet.microsoft.com/en-us/sysinternals/psexec)
[pslist](https://technet.microsoft.com/en-us/sysinternals/pslist)
