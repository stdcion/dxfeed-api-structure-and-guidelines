# Dump Tool

* Type: Task
* Epic: Tools
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net.Tools/Dump

## Description

Dumps all events received from address.\
Enforces a streaming contract for subscription. A wildcard enabled by default.\
This was designed to receive data from a file.

It is important, to add features iteratively, for example in the first stage, it will be difficult to add output to the
tape file (before implementing DXPublisher).

List of arguments:

```
Usage:
    Dump <address>
    Dump <address> <types> <symbols> [<options>]

  -p, --properties    Comma-separated list of properties.
                      Examples:
                          -p dxfeed.aggregationPeriod=5s - to set the aggregation period.
                          -p dxfeed.wildcard.enable=true - to enable the wildcard symbol.

  -t, --tape          Tape all incoming data into the spcified file.
                      This option has several parameters:

                      "format" parameter defines format of stored data. Its value can be one of "text", "binary" or
                      "blob:<record>:<symbol>" (binary format is used by default).
                      Blob is a special format that is used for compact store of a single-record, single-symbol data
                      stream.

                      "saveas" parameter overrides the type of stored messages.
                      Data messages can be stored as "ticker_data", "stream_data","history_data", or "raw_data".

  -q, --quite         Be quiet, event printing is disabled.

  --help              Display this help screen.

  --version           Display version information.

  address (pos. 0)    Required.
                      The address to connect to retrieve data (remote host or local tape file).
                      If you do not specify a prefix (tcp: or file:) it will try to automatically determine the
                      connector.
                      Examples:
                          <tcp:hostname:port> - for remote host.
                          <file:path_to_file> - for local file.

  types (pos. 1)      Comma-separated list of dxfeed event types (e.g. Quote,TimeAndSale).
                      Use "feed" for all available events.

  symbols (pos. 2)    Comma-separated list of symbol names to get events for (e.g. "IBM,AAPL,MSFT").
                      Use "all" for wildcard subscription. For this, the dxfeed.wildcard.enable property must be set to
                      true.



Examples:
  Dump all events and all symbols from the specified file:
      dump tape.csv

  Dump all events and all symbols from the specified file at maximum speed:
      dump tape.csv[speed=max]

  Dump all events and all symbols from the specified file at maximum speed, cyclically:
      dump tape.csv[speed=max,cycle]

  Dump only Quote event for all symbols from the specified file:
      dump tape.csv Quote

  Dump only Quote event for AAPL symbol from the specified file:
      dump tape.csv Quote AAPL

  Dump only Quote event for AAPL symbol from the specified address in a stream contract:
      dump demo.dxfeed.com:7300 Quote AAPL

  Tape only Quote event for AAPL symbol from the specified address in a stream contract into the specified tape file:
      dump demo.dxfeed.com:7300 Quote AAPL -q -t tape.bin
```
