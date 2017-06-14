
```
shell> esxcli system snmp set
shell> esxcli system snmp set --enable true
```

輸入 esxcli system snmp set --targets target_address@port/community。
使用目標系統的位址、設陷傳送到的連接埠號碼和社群名稱分別取代 target_address、port 和 community。每次使用此命令指定目標時，您所指定的設定將覆寫之前指定的所有設定。若要指定多個目標，請用逗號加以分隔。
例如，若要將 SNMP 設陷從主機 host.example.com 傳送到使用公開社群的 target.example.com 上的連接埠 162，請輸入 esxcli system snmp set --targets target.example.com@162/public。
2
(選擇性) 如果未啟用 SNMP 代理程式，請輸入 esxcli system snmp set --enable true 以將其啟用。
3
(選擇性) 透過輸入 esxcli system snmp test 傳送測試設陷，以驗證代理程式的設定是否正確。
代理程式會將 warmStart 設陷傳送到所設定的目標。





- https://pubs.vmware.com/vsphere-55/index.jsp?topic=%2Fcom.vmware.vsphere.monitoring.doc%2FGUID-EA64297A-35FD-4226-A1B2-367C57D38CBD.html

       ~ # esxcli system snmp set -c public
       ~ # esxcli system snmp set -e yes



