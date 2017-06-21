
```xml
<Value>Windows 7 STARTER</Value><!-- Windows 7 簡易版 -->
<Value>Windows 7 HOMEBASIC</Value><!-- Windows 7 家用入門版 -->
<Value>Windows 7 HOMEPREMIUM</Value><!-- Windows 7 家用進階版 -->
<Value>Windows 7 PROFESSIONAL</Value><!-- Windows 7 專業版 -->								
<Value>Windows 7 ULTIMATE</Value><!-- Windows 7 旗艦版 -->
```

**Autounattend.xml** (x86)
```xml
<?xml version="1.0" encoding="utf-8" ?>
<unattend
    xmlns="urn:schemas-microsoft-com:unattend">
    <settings pass="windowsPE">
        <component name="Microsoft-Windows-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS"
            xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <ImageInstall>
                <OSImage>
                    <InstallFrom>
                        <MetaData wcm:action="add">
                            <Key>/IMAGE/INDEX</Key>
                            <Value>Windows 7 PROFESSIONAL</Value>                          
                        </MetaData>
                    </InstallFrom>
                </OSImage>
            </ImageInstall>
            <UserData>
                <AcceptEula>true</AcceptEula>
                <!-- 指定是否要在 Windows 安裝程式執行期間接受 Microsoft 軟體授權合約。 -->
            </UserData>
        </component>
        <component name="Microsoft-Windows-International-Core-WinPE" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS"
            xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <SetupUILanguage>
                <UILanguage>zh-tw</UILanguage>
            </SetupUILanguage>
            <InputLocale>zh-tw</InputLocale>
            <!-- 指定 Windows 安裝的預設輸入法地區設定。 -->
            <UILanguage>zh-tw</UILanguage>
            <!-- 指定 Windows 安裝的預設 UI 語言。 -->
            <UILanguageFallback>zh-tw</UILanguageFallback>
            <UserLocale>zh-tw</UserLocale>
            <!-- 指定 Windows 安裝的預設使用者地區設定。 -->
        </component>
    </settings>
    <settings pass="oobeSystem">
        <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS"
            xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <OOBE>
                <HideEULAPage>true</HideEULAPage>
                <!--  指定以隱藏 [Microsoft 軟體授權合約] 頁面 -->
                <ProtectYourPC>3</ProtectYourPC>
                <!-- 指定 Windows 安裝的保護等級。 -->
                <SkipMachineOOBE>true</SkipMachineOOBE>
                <SkipUserOOBE>true</SkipUserOOBE>
                <NetworkLocation>Work</NetworkLocation>
                <!-- 指定電腦的位置。 -->
                <HideWirelessSetupInOOBE>true</HideWirelessSetupInOOBE>
                <!-- 隱藏 [無線網路] 選取頁面。 -->
            </OOBE>
            <AutoLogon>
                <Password>
                    <Value></Value>
                    <PlainText>true</PlainText>
                </Password>
                <LogonCount>1</LogonCount>
                <Username>Administrator</Username>
                <Enabled>true</Enabled>
            </AutoLogon>
            <UserAccounts>
                <AdministratorPassword>
                    <Value></Value>
                    <PlainText>true</PlainText>
                </AdministratorPassword>
            </UserAccounts>
        </component>
    </settings>
</unattend>
```

```xml
<?xml version="1.0" encoding="utf-8" ?>
<unattend
    xmlns="urn:schemas-microsoft-com:unattend">
    <settings pass="windowsPE">
        <component name="Microsoft-Windows-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS"
            xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <ImageInstall>
                <OSImage>
                    <InstallFrom>
                        <MetaData wcm:action="add">
                            <Key>/IMAGE/NAME</Key>
                            <!-- <Value>Windows 7 STARTER</Value> -->
                            <!-- Windows 7 簡易版 -->
                            <!-- <Value>Windows 7 HOMEBASIC</Value> -->
                            <!-- Windows 7 家用入門版 -->
                            <!-- <Value>Windows 7 HOMEPREMIUM</Value> -->
                            <!-- Windows 7 家用進階版 -->
                            <Value>Windows 7 PROFESSIONAL</Value>
                            <!-- Windows 7 專業版 -->
                            <!-- <Value>Windows 7 ULTIMATE</Value> -->
                            <!-- Windows 7 旗艦版 -->
                        </MetaData>
                    </InstallFrom>
                </OSImage>
            </ImageInstall>
            <UserData>
                <AcceptEula>true</AcceptEula>
                <!-- 指定是否要在 Windows 安裝程式執行期間接受 Microsoft 軟體授權合約。 -->
            </UserData>
        </component>
        <component name="Microsoft-Windows-International-Core-WinPE" processorArchitecture="amd64" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS"
            xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <SetupUILanguage>
                <UILanguage>zh-tw</UILanguage>
            </SetupUILanguage>
            <InputLocale>zh-tw</InputLocale>
            <!-- 指定 Windows 安裝的預設輸入法地區設定。 -->
            <UILanguage>zh-tw</UILanguage>
            <!-- 指定 Windows 安裝的預設 UI 語言。 -->
            <UILanguageFallback>zh-tw</UILanguageFallback>
            <UserLocale>zh-tw</UserLocale>
            <!-- 指定 Windows 安裝的預設使用者地區設定。 -->
        </component>
    </settings>
    <settings pass="oobeSystem">
        <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS"
            xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
            <OOBE>
                <HideEULAPage>true</HideEULAPage>
                <!--  指定以隱藏 [Microsoft 軟體授權合約] 頁面 -->
                <ProtectYourPC>3</ProtectYourPC>
                <!-- 指定 Windows 安裝的保護等級。 -->
                <SkipMachineOOBE>true</SkipMachineOOBE>
                <SkipUserOOBE>true</SkipUserOOBE>
                <NetworkLocation>Work</NetworkLocation>
                <!-- 指定電腦的位置。 -->
                <HideWirelessSetupInOOBE>true</HideWirelessSetupInOOBE>
                <!-- 隱藏 [無線網路] 選取頁面。 -->
            </OOBE>
            <AutoLogon>
                <Password>
                    <Value></Value>
                    <PlainText>true</PlainText>
                </Password>
                <LogonCount>1</LogonCount>
                <Username>Administrator</Username>
                <Enabled>true</Enabled>
            </AutoLogon>
            <UserAccounts>
                <AdministratorPassword>
                    <!-- 設定 Administrator 帳戶密碼。 -->
                    <Value></Value>
                    <PlainText>true</PlainText>
                </AdministratorPassword>
            </UserAccounts>
        </component>
    </settings>
</unattend>

```

### :books: 參考網站：

- [執行 Windows 安裝程式的方法](https://technet.microsoft.com/zh-tw/library/cc749415(v=ws.10).aspx)
- [iT自救術─x86和x64到底有什麼差異？](http://www.ithome.com.tw/node/56880)
- [Windows 7：常見問題](http://www.dell.com/learn/tw/zh/twbsd1/operating-systems/windows7_smb_faq)
- [逐步解說： Boot Windows PE from CD-ROM](https://technet.microsoft.com/zh-tw/library/cc766385(v=ws.10).aspx)
- [下載 Windows 7 光碟映像 (ISO 檔案)](https://www.microsoft.com/zh-tw/software-download/windows7)
- https://technet.microsoft.com/en-us/library/dn621892.aspx
- https://technet.microsoft.com/zh-tw/library/cc722388(v=ws.10).aspx
- https://technet.microsoft.com/en-us/library/ff715379.aspx
- https://technet.microsoft.com/zh-tw/library/cc749278(v=ws.10).aspx
- https://technet.microsoft.com/zh-tw/library/jj200142(v=ws.11).aspx
- https://technet.microsoft.com/zh-tw/library/dd744547(v=ws.10).aspx
- https://www.microsoft.com/en-ca/software-download/windows7
- https://technet.microsoft.com/zh-tw/library/cc722150(v=ws.10).aspx
- https://technet.microsoft.com/zh-tw/library/ff716385.aspx
- https://winscp.net/eng/docs/guide_windows_openssh_server














