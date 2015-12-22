# Mqtt-chat
Contains SPEC for designing chat based on Mqtt

```
Designing a sane chat based on mqtt.
1. Servers emqtt - https://github.com/emqtt/emqttd or vernemq - https://github.com/erlio/vernemq
2. Client - eclipse paho.
3. channels - client1/others/chatstate, client1/others/presence, client1/others/profile, client1/self/invitations. Client1 subscribes to client1/self. Client 2 and others subscribe to client1/others/*. Authorization by client1 on client/others.
4. messaging between two clients - uuid/messages or client1/client2/messages where client1<client2.
5. Group chat channels - groupchat/messages, groupchat/members. Authorization. How will your group chat members be visible to a new user - since retained message is just 1? One solution is to update the retained messages.
6. Persistent session - autosubscribe - client1/*, groupchat/* . Mark all your client tables with a subscribed field to make sure for subscription.
7. Client state indication - Drop chat states, Group presence and deliver when client state = active (v2). Bundle/Drop incoming packet if your app is in background.
8. Bundle outgoing packets (not critical).
```


