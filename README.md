# Mqtt-chat
Contains SPEC for designing chat based on Mqtt

```
Designing a sane lightweight chat protocol based on mqtt.
1. Servers emqtt - https://github.com/emqtt/emqttd or vernemq - https://github.com/erlio/vernemq
2. Client - eclipse paho, mqtt.js.
3. channels - client1/others/chatstate, client1/others/invitations, client1/others/messages, client1/self/presence, client1/self/profile. Client1 subscribes to client1/others/+. Client 2 and others subscribe to client1/self/+. To send message just publish to client1/message. To send chatstate like 'is typing' - client1/chatstate. - Implemented.
4. Group chat channels - groupchat/others/messages, groupchat/others/members, groupchat/others/profile. Authorization. How will your group chat members be visible to a new user - since retained message is just 1? One solution is to update the retained messages. Every one in group will subscribe to groupchat/others/+. -Implemented
5. Persistent session - autosubscribe - client1/*, groupchat/* . Mark all your client tables with a subscribed field to make sure for subscription. - Default.
6. Client state indication - Drop chat states, Group presence and deliver when client state = active (v2). Bundle/Drop incoming packet if your app is in background. If your app is in background use GCM.
7. Work across resource. If you have a web client, desktop client, mobile client message should be synced across all. Indication if the message is seen across clients.
8. Should work with clients with no offline storage.
9. Add support for send, delivery and read receipts. - Implemented
10. Also add provision for GCM, APNS to make it work with app standy mode and IOS systems.
11. SIP support by providing chat message channels. - Implemented.

TODO - Find a way to generate smaller unique identifiers. 
```

  Design Philosophy:

Making it infinitely extensible by using a ProviderManager similar to Smack. Every packet have a provider and is responsible for it's own processing. Sample implementation - https://github.com/DrawersApp/Node-Sdk/tree/mqtt/src .   


