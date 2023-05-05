# Performance Test Tool

* Type: Task
* Epic: Tools
* Required: Mandatory
* Functional: Base
* Complexity: Medium

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net.Tools/PerfTest

## Description

Connects to the specified address(es) and calculates performance counters (events per second, memory usage, cpu usage,
etc).

It is possible not to implement the functionality that is responsible for the output of system information about memory
consumption, CPU load, etc.

List of arguments:

```
Usage:
    PerfTest <address> <types> <symbols> [<options>]

  --force-stream         Enforces a streaming contract for subscription. The StreamFeed role is used instead of Feed.

  --cpu-usage-by-core    Show CPU usage by core (where 1 core = 100%).

  --detach-listener      Don't attach a listener. Used for debugging purposes.

  -p, --properties       Comma-separated list of properties.
                         Examples:
                             -p dxfeed.aggregationPeriod=5s - to set the aggregation period.
                             -p dxfeed.wildcard.enable=true - to enable the wildcard symbol.

  --help                 Display this help screen.

  --version              Display version information.

  address (pos. 0)       Required.
                         The address to connect to retrieve data (remote host or local tape file).
                         If you do not specify a prefix (tcp: or file:) it will try to automatically determine the
                         connector.
                         Examples:
                             <tcp:hostname:port> - for remote host.
                             <file:path_to_file> - for local file.

  types (pos. 1)         Required.
                         Comma-separated list of dxfeed event types (e.g. Quote,TimeAndSale).
                         Use "feed" for all available events.

  symbols (pos. 2)       Required.
                         Comma-separated list of symbol names to get events for (e.g. "IBM,AAPL,MSFT").
                         Use "all" for wildcard subscription. For this, the dxfeed.wildcard.enable property must be set
                         to true.



Examples:
    Connects to the local endpoint, subscribes to TimeAndSale event for ETH/USD:GDAX symbol
    and print performance counters:
       perftest 127.0.0.1:7777 TimeAndSale ETH/USD:GDAX

    Connects to the tape file (on max speed and cyclically), subscribes for all events and all symbols
    and print performance counters:
        perftest file:tape.csv[speed=mac,cycle] feed all -force-stream
```
