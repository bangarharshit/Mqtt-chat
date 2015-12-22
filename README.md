# Mqtt-chat
Contains SPEC for designing chat based on Mqtt

```
Designing a sane chat protocol based on mqtt.
1. Servers emqtt - https://github.com/emqtt/emqttd or vernemq - https://github.com/erlio/vernemq
2. Client - eclipse paho.
3. channels - client1/others/chatstate, client1/others/presence, client1/others/profile, client1/self/invitations. Client1 subscribes to client1/self. Client 2 and others subscribe to client1/others/*. Authorization by client1 on client/others.
4. Group chat channels - groupchat/messages/clientid, groupchat/members/clientid. Authorization. How will your group chat members be visible to a new user - since retained message is just 1? One solution is to update the retained messages. Removed concept of single user chat to simplify. Every one in group will subscribe to groupchat/messages/* and groupchat/members/*
5. Persistent session - autosubscribe - client1/*, groupchat/* . Mark all your client tables with a subscribed field to make sure for subscription.
6. Client state indication - Drop chat states, Group presence and deliver when client state = active (v2). Bundle/Drop incoming packet if your app is in background. If your app is in background use GCM.
7. Bundle outgoing packets (not critical).
8. Work across resource. If you have a web client, desktop client, mobile client message should be synced across all. Indication if the message is seen across clients.
9. Should work with clients with no offline storage.
10. Add support for send, delivery and read receipts.
11. Also add provision for GCM, APNS to make it work with app standy mode and IOS systems.
12. SIP support by providing groupid/call/clientid channels. Every client will publish their information on these channels and everyone will subscribe to groupid/call/* channel. 

TODO - Find a way to generate smaller unique identifiers. 
```


