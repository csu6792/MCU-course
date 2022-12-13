---
layout: post
title: ESP32 line notifly /line通知介紹
author: [Sheng Jie]
category: [Lecture]
tags: [jekyll, ai]
---

LINE push notifications

---

### [line notifly](https://notify-bot.line.me/zh_TW/)

## install library
## [資料來源](https://ithelp.ithome.com.tw/articles/10271219)
TridentTD_LineNotify<br>
![](https://i.imgur.com/55zuvDi.png)

---

---
**login** <br>

![](https://i.imgur.com/uUWmnzG.png)

**個人頁面** <br>

![](https://i.imgur.com/zFIVy9r.png)

**點擊發行權杖 並選擇要發送的聊天室** <br>

![](https://i.imgur.com/3fwskdF.png)

**複製權杖** <br>

![](https://i.imgur.com/tA7jdvA.png)



**include library**<br>

```
#include <WiFi.h>
#include <WiFiClient.h>
#include <TridentTD_LineNotify.h>
```


set line token
```
#define LINE_TOKEN "jYTanwRtmAwnwevAWbBhU35RKhEq2OXAxxxxxxxxxxx"
```

**main**<br>
```
message_line = "hello";
 void setup() {
  Serial.begin(115200);
  LINE.setToken(LINE_TOKEN);
  LINE.notify("\n" + message_line);
  }
```

---




<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*
