# LastEventsConsole

* Type: Task
* Epic: Samples
* Required: Mandatory
* Functional: Pre-Advanced
* Complexity: Low

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-samples/src/main/java/com/dxfeed/sample/console/LastEventsConsole.java

## Description

This sample demonstrates a way to subscribe to the big world of symbols with dxFeed API, so that the events are
updated and cached in memory of this process, and then take snapshots of those events from memory whenever
they are needed. This example repeatedly reads symbol name from the console and prints a snapshot of its last
quote, trade, summary, and profile events.
