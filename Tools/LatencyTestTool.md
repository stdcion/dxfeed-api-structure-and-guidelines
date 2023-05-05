# Latency Test Tool

* Type: Task
* Epic: Tools
* Required: Mandatory
* Functional: Pre-Advanced
* Complexity: Medium

## Description

Used to check the maximum performance. The idea is to publish a large number of events (with large buffers configured)
via Java API and wait for the receiving API to process them. Print information about first event latency, last event
latency, processing time per event. You need a special publisher to work.
