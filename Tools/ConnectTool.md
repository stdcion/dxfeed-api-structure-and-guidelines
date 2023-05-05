# Connect Tool

* Type: Task
* Epic: Tools
* Required: Mandatory
* Functional: Base
* Complexity: Low

## Useful Links

.NET:
https://github.com/dxFeed/dxfeed-graal-net-api/blob/main/src/DxFeed.Graal.Net.Tools/Connect

## Description

Connects to the specified address(es) and subscribe to the specified events with the specified symbol.

It is important, to add features iteratively, for example in the first stage, it will be difficult to add output to the
tape file (before implementing DXPublisher), the same, with the addition of different time formats, in the first stage,
you can be limited to milliseconds from the UTC epoch.

List of arguments:

```
Usage:
    Connect <address> <types> <symbols> [<options>]

  -f, --from-time     From-time for history subscription in standard formats.

  -s, --source        Order source for the indexed subscription (e.g. NTV, ntv).

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

  types (pos. 1)      Required.
                      Comma-separated list of dxfeed event types (e.g. Quote,TimeAndSale).
                      Use "feed" for all available events.

  symbols (pos. 2)    Required.
                      Comma-separated list of symbol names to get events for (e.g. "IBM,AAPL,MSFT").
                      Use "all" for wildcard subscription. For this, the dxfeed.wildcard.enable property must be set to
                      true.

Examples:
   Connects to the demo-endpoint and subscribes to Quote event for AAPL,IBM,MSFT symbols:
       connect demo.dxfeed.com:7300 Quote AAPL,IBM,MSFT

   Connects to the demo-endpoint and subscribes to Quote,Trade events for AAPL,MSFT symbols
   with aggregation period 5s:
       connect demo.dxfeed.com:7300 Quote,Trade AAPL,MSFT -p dxfeed.aggregationPeriod=5s

   Connects to the demo-endpoint and subscribes to Order event for AAPL symbol
   with order source NTV (NASDAQ Total View):
       connect demo.dxfeed.com:7300 Order AAPL -s NTV

   Connects to the demo-endpoint and subscribes to TimeAndSale event for AAPL symbol
   from starting January 1, 1970:
       connect demo.dxfeed.com:7300 TimeAndSale AAPL -t 0

   Connects to the tape file and subscribes for all events and all symbols:
       connect file:tape.csv feed all -p dxfeed.wildcard.enable=true
```
