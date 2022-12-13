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


### [AsyncTCP](https://github.com/me-no-dev/AsyncTCP)

---

---
**login** <br>

![](https://github.com/csu6792/MCU-course/blob/main/images/webserver_1.png?raw=true)



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
