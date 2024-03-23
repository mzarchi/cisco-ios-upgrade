# آموزش تغییر IOS سوییچ Cisco
- ابتدا وارد محیط configure شده و دستورات زیر را وارد می‌کنید:
```Sw(config) # username test secret 12345
Sw(config) # enable secret 12345
Sw(config) # line vty 0 15
Sw(config-line) # password 12345
Sw(config-line) # login local
Sw(config-line) # transport input all```

