# Mqtt-chat
Contains SPEC for designing chat based on Mqtt

```
Designing chat based on mqtt.
1. Servers emqtt - https://github.com/emqtt/emqttd or vernemq - https://github.com/erlio/vernemq
2. Client - eclipse paho.
3. channels - client1/message, client1/chatstate, client1/presence. Authorization.
4. Group chat channels - groupchat/messages, groupchat/members. Authorization.
5. Persistent session - autosubscribe - client1/*, groupchat/* . Mark all your client tables with a subscribed field to make sure for subscription.
6. Client state indication - Drop chat states, Group presence and deliver when client state = active (v2). Bundle/Drop incoming packet if your app is in background.
7. Bundle outgoing packets (not critical).
```


