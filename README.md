# آموزش بروزرسانی / آپدیت IOS سوییچ Cisco
- ابتدا وارد محیط configure شده و دستورات زیر را وارد می‌کنید:
```
Sw(config) # username test secret 12345
Sw(config) # enable secret 12345
Sw(config) # line vty 0 15
Sw(config-line) # password 12345
Sw(config-line) # login local
Sw(config-line) # transport input all
```
\n
- بعد از این مرحله با دستور interface vlan 1  در محیط configure وارد تنظیمات آن می‌شویم و دستورات زیر را  وارد می‌کنیم:
```
Sw(config-if) # ip address 10.10.10.10 255.255.255.0
Sw(config-if) # no shutdown
```
\n
