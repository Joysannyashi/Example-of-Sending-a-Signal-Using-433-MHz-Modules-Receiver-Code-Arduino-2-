// Example-of-Sending-a-Signal-Using-433-MHz-Modules-Receiver-Code-Arduino-2-
#include <VirtualWire.h>

void setup() {
  Serial.begin(9600);  // Start serial communication for debugging
  vw_setup(2000);  // Bits per second (baud rate)
  vw_set_rx_pin(11);  // Receiver is connected to pin 11
  vw_rx_start();  // Start the receiver
}

void loop() {
  uint8_t buf[VW_MAX_MESSAGE_LEN];
  uint8_t buflen = VW_MAX_MESSAGE_LEN;
  
  if (vw_get_message(buf, &buflen)) {  // Check if data is received
    Serial.print("Received: ");
    for (int i = 0; i < buflen; i++) {
      Serial.write(buf[i]);  // Print the received message
    }
    Serial.println();
  }
}
