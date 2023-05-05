# ObservableSubscriptionChangeListener

* Type: Task
* Epic: Api/Osub
* Required: Mandatory
* Functional: Pre-Advanced
* Complexity: Medium

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/api/osub/ObservableSubscriptionChangeListener.java

## Description

The listener interface for receiving notifications on the changes of observed subscription.
All methods on this interface are invoked while holding a lock on ObservableSubscription instance,
thus all changes for a given subscription are synchronized with respect to each other.
