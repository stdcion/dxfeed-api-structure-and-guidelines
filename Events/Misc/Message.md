# Message

* Type: Task
* Epic: Events/Misc
* Required: Mandatory
* Functional: Advanced
* Complexity: Medium

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/event/misc/Message.java

## Description

Message event with application-specific attachment. Messages are never conflated and are delivered to
all connected subscribers. There is no built-in persistence for messages. They are lost when subscribers
are not connected to the message publisher, so they shall be only used for notification purposes in
addition to persistence mechanism.
