# Schedule

* Type: Epic
* Required: Mandatory
* Functional: Advanced

## Useful Links

Java:
https://github.com/devexperts/QD/blob/master/dxfeed-api/src/main/java/com/dxfeed/schedule

## Description

Provides information about trading days, sessions, and their schedules. Schedule class provides API to retrieve and
explore trading schedules of different exchanges and different classes of financial instruments. Each instance of
schedule covers separate trading schedule of some class of instruments, i.e. NYSE stock trading schedule or CME corn
futures trading schedule. Each schedule splits entire time scale into separate days that are aligned to the specific
trading hours of covered trading schedule.

Consists of the following modules:

* Day
* DayFilter
* Schedule
* Session
* SessionFilter
* SessionType
