# Olympia Distribution WG

https://dao.joystream.org/#/working-groups/distribution

- Lead: [l1dev](https://dao.joystream.org/#/proposals/preview/13) ([Applications](https://dao.joystream.org/#/working-groups/openings/distributionWorkingGroup-0))
- Budget: [Proposal](https://dao.joystream.org/#/proposals/preview/18) ([Discussion](https://discord.com/channels/811216481340751934/812343711870091285/957682269475201025))

## Bucket Families

| Family | Label | Region | Workers |
|---|---|---|---|
| 0 | EU-1 | N EU | @l1 @max @mike |
| 1 | EU-2 | central EU | @yasir @l1 |
| 2 | AS-1 | E EU / NW AS | @lkskrn @mike |
| 3 | AS-2 | E AS | @ilich |
| 4 | AS-3 | SEA |  @cooloNe |
| 5 | AF-1 | N AF / S EU | |
| 6 | AF-2 | S AF | @Alex |
| 7 | OC | AU / Oceania | @l1 |
| 8 | SA-1 | S SA | |
| 9 | SA-2 | N SA + central | @0x2bc @spat |
| 10 | NA-1 | NA W | @cooloNe |
| 11 | NA-2 | NA central | |
| 12 | NA-3 | NA E | @l1 |

## Workers

https://dao.joystream.org/#/working-groups/distribution

[Pin](https://discord.com/channels/811216481340751934/933726271832227911/957589245407678494)

![](https://cdn.discordapp.com/attachments/933726271832227911/957675927326838814/olympia-distribution.png)

### Upgrading

- [QN](https://discord.com/channels/811216481340751934/933726271832227911/957653724174614559), [also](https://discord.com/channels/811216481340751934/933726271832227911/957390875959361597)
- [Validator](https://discord.com/channels/811216481340751934/933726271832227911/957572146958319616) (`--rpc-cors`)

### Costs

To be added

## Config
> Get a ("censored") version of each distributors config.yml file, share them, and propose/require changes.

```
id: test-node # change to: `<countryCode>-<familyId>-<bucketIndex>-<memberID>-<handle>` for example *ca-3-0-515-l1dev* (need to be unique to identify test results)
endpoints:
  queryNode: http://localhost:8081/graphql  # should use QN from your localhost
  joystreamNodeWs: ws://localhost:9944         # should use endpoint on the localhost
directories:
  assets: ./local/data                                       # can be any directory or mountpoint, see role guide
  cacheState: ./local/cache                                  # ^
logs:
  file:
    level: debug                              # you can set higher level to reduce output if needed
    path: ./local/logs                       # path to logs location
    maxFiles: 30 # 1 log file for 30 days or 30 * 50 MB
    maxSize: 50485760 # 50 MB - max log file size
  console:
    level: verbose                           # adjust to your needs for testing, should run as system service with log file during production (see guide).
  # elasti
  #   level: info
  #   endpoint: http://localhost:9200/       
limits:
  storage: 100G				     # !IMPORTANT - adjust it to the size of your hard drive. Leave some space for OS and logs and this is the value for the distributor payload
  maxConcurrentStorageNodeDownloads: 100     #  also understand in detail: https://github.com/Joystream/joystream/blob/master/distributor-node/docs/node/index.md#caching
  maxConcurrentOutboundConnections: 300
  outboundRequestsTimeoutMs: 5000
  pendingDownloadTimeoutSec: 3600
  maxCachedItemSize: 1G
intervals:
  saveCacheState: 60
  checkStorageNodeResponseTimes: 60
  cacheCleanup: 60
publicApi:
  port: 3334
operatorApi:
  port: 3335
  hmacSecret: some-random-value
keys:
workerId: 0                                  # Ask lead for this value
```

## Setup

- [Commands](https://discord.com/channels/811216481340751934/933726271832227911/957567685993050162)
- Hint: [set dynamic bag policy early to avoid manual bag assignment](https://discord.com/channels/811216481340751934/933726271832227911/957592223422230566)

## Bugs

- multiple workers can be invited to the same bucket ([details](https://discord.com/channels/811216481340751934/933726271832227911/957673382936199240))
- worker id is not displayed on https://dao.joystream.org/#/working-groups/distribution 
- only one of three hired workers is displayed on https://dao.joystream.org/#/working-groups/openings/distributionWorkingGroup-4
