# آموزش بروزرسانی / آپدیت IOS سوییچ Cisco
- ابتدا وارد محیط **configure** شده و دستورات زیر را وارد می‌کنید:
```
Sw(config) # username test secret 12345
Sw(config) # enable secret 12345
Sw(config) # line vty 0 15
Sw(config-line) # password 12345
Sw(config-line) # login local
Sw(config-line) # transport input all
```
<br />

- بعد از این مرحله با دستور ```interface vlan 1```  در محیط **configure** وارد تنظیمات آن می‌شویم و دستورات زیر را  وارد می‌کنیم:
```
Sw(config-if) # ip address 10.10.10.10 255.255.255.0
Sw(config-if) # no shutdown
```
<br />

- سپس پورت مورد نظر را باز کرده و دستور ```switchport host``` و  ```switchport access vlan 1``` را زیر پورت می‌زنیم، سیستم را به پورت سوییچ مورد نظر متصل کرده و در رنج ip مورد نظر به سیستم ip می‌دهیم به عنوان مثال در اینجا می‌شود **255.255.255.0 10.10.10.20** و بعد داخل ترمینال پینگ سوییچ که ip آن **10.10.10.10** را می‌گیریم اگر موفقیت آمیز بود تنظیمات درست اعمال شده.

<br />

- وارد نرم‌افزار **MobaXterm** می‌شوید، روی گزینه **Servers** کلیک کرده و سپس در پنجره باز شده روی گزینه تنظیمات **FTP server** و بعد از آن صفحه تنظیمات باز شده و در قسمت **Root directory** آدرس دایرکتوری مورد نظر جهت انتقال فایل را انتخاب و در نهایت روی گزینه اجرا کلیک می‌کنیم، دقت داشته باشید مقدار **Login** ، **Password** و چک باکس **Promt me before …** را  خالی بگذارید.

<br />

- وارد محیط **enable** سوییچ شده و دستورات زیر را  وارد کنید و منتظر بمانید تا **IOS** از **FTP** به روی سوییچ انتقال یابد:
```
Sw # copy ftp: flash:
Address or name of remote host []? 10.10.10.20
Source filename []? <ios-name.extention>
Destination filename [<ios-name.extention>] ? Enter
```

<br />

- سپس دستورات زیر را در محیط **configure** وارد میکنیم:
```
Sw(config) # boot system flash:packages.conf
Sw(config) # no boot manual
Sw(config) # do write
```

<br />

- سپس به محیط **enable** رفته و برای نصب **ios** دستور زیر را وارد می‌کنیم:
```
Sw # install add file flash: <ios-name.extention> activate commit
```

<br />

- بعد از وارد کردن دستور بالا سوییچ از شما دوسوال میپرسد که به ترتیب زیر میباشدو هدف آن
تایید از کاربر جهت نصب و اکتیو **ios** میباشد.
```
Performing Activate on all members
    [1] Activate package(s) on Switch 1 -> Insert 1 and Enter

Performing Commit on all members
    [1] Commit package(s) on Switch 1 -> Insert 1 and Enter
```