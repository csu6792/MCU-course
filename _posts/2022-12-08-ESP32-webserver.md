---
layout: post
title: ESP32 webserver /網頁服務器架設
author: [Sheng Jie]
category: [Lecture]
tags: [jekyll, ai]
---

ESPAsyncWebServer / html

---

### [ESPAsyncWebServer github](https://github.com/me-no-dev/ESPAsyncWebServer)

### [eps32 fs](https://github.com/me-no-dev/arduino-esp32fs-plugin/releases/)

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
#include "WiFi.h"
#include "ESPAsyncWebServer.h"
#include "SPIFFS.h"

const char* ssid     = "csutest";
const char* password = "123456789";
const char* PARAM_MESSAGE = "csucsu";
const int ledPin = 2;

// Create AsyncWebServer object on port 80
AsyncWebServer server(80);
```


**main**<br>
```
void setup(){
  // Serial port for debugging purposes
  Serial.begin(115200);
  pinMode(ledPin, OUTPUT);
  // Initialize SPIFFS
  if(!SPIFFS.begin(true)){
    Serial.println("An Error has occurred while mounting SPIFFS");
    return;
  }

  // Connect to Wi-Fi
  //WiFi.begin(ssid, password);
  WiFi.softAP(ssid, password);
  /*while (WiFi.status() != WL_CONNECTED) {
    delay(1000);
    Serial.println("Connecting to WiFi..");
  }*/
  // Print ESP32 Local IP Address
  Serial.println(WiFi.localIP());
  //server.on("/led_set", led_control);

  server.on("/led_set", HTTP_GET, [](AsyncWebServerRequest *request){
    Serial.println("read");
    String message;
    String state;
    if (request->hasParam("state")) {
       message = request->getParam("state")->value();
       Serial.println(message);
       if(message == "1")
       {
         Serial.println(message);
         
       }
       else
       {
          
        Serial.println(message);
       }
       request->send(200, "text/plane", state);
    }
  });

  server.on("/", HTTP_GET, [](AsyncWebServerRequest *request){
    request->send(SPIFFS, "/index.html");
  });
  
  // Route to load style.css file
  server.on("/style.css", HTTP_GET, [](AsyncWebServerRequest *request){
    request->send(SPIFFS, "/style.css", "text/css");
  });

  server.on("/jquery.min.js", HTTP_GET, [](AsyncWebServerRequest *request){
    request->send(SPIFFS, "/jquery.min.js");
  });
  
  server.on("/unnamed", HTTP_GET, [](AsyncWebServerRequest *request){
    request->send(SPIFFS, "/unnamed.jpg", "image/jpg");
  });
  
  // Start server
  server.begin();
}
 
void loop(){
  
}
```

---




<br>
<br>

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*
