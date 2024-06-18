#include "CTBot.h"
CTBot robot;
int relay = 4;

void setup() {
    Serial. begin(115200);
    pinNode(relay, OUTPUT);
    digitalWrite(relay, HIGH) ;
    robot. wifiConnect("NAMA WIFI","PASSWORD NYA");
    robot. serTelegramToken("angka token nya disini");
    if(robot.testConnection())
        Serial. printin("Terhubung!");
    else
        Serial. printin("Error! ");

}

void loop() {
    TBMessage pesan;

    if(robot.getNewMessage(pesan)) {
        Serial. print("Ada pesan masuk: ");
        Serial. printin(pesan.text);
        if(pesan. text. equalsIgnoreCase("RELAY ON")) {
            digitalWrite(relay, LOW);
            robot. sendMessage(pesan.sender.id,"Relay Menyala");
        }
        else if(pesan.text.equalsIgnoreCase("RELAY OFF")) {
            digitWrite(relay, HIGH);
            robot. sendMessage(pesan.sender.id,"Relay Padam");
        }
        else
        }
    string balas;
    balas="Maaf, perintahnya salah. Coba kirim RELAY ON atau RELAY OFF. );
    robot. sendMessage(pesan.sendder.id.balas);
}
}
