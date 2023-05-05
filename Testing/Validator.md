# Validator

* Type: Task
* Epic: Testing
* Required: Mandatory
* Functional: Pre-Advanced
* Complexity: High

## Description

It is used to verify that all market events are parsed/composed correctly. Implemented as a separate jar file that
allows you to compare all event fields with the reference dxFeed Java API. The dump tool (inside API) is required for
proper operation. Can be implemented as part of a CI/CD.

The idea is that the jar file generates and writes data to a tape file, which
is then played with the dump tool (a specific API) and written to another tape file, and then compared by the validator
for inconsistencies.

This is a quick and easy way to check the correctness of events without having to develop separate unit tests (which
does not rule out the need to write them).
