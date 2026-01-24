# Concepts

## Modes of a trading system

Modes are logical groupings of trading systems that reflect their lifecycle. There are 3 of them (**development**,
**trading** and **archive**) and a trading system can be in only one of them.


### Development mode

When a user creates a trading system it is in this mode, and it will remain in this mode during its development.
During development, any aspect of a trading system can be changed at will. After some time, when the user decides
that it is good enough, they can finalize the trading system, moving it into the **trading** mode.

*Finalization* is the process that closes the development, making the trading system ready for trading.


### Trading mode

When a trading system is moved to the **trading** mode, the trading engine starts to generate trades for it.
In particular, the running flag (on/off) means:

- **Off** : The trading system is *not live* but it generates trades anyway. This is a particular status useful to
  monitor the system with real new data but acting like paper trading (orders are not sent to the broker). After 
  a few months of monitoring, if the performance is satisfactory, the trading system can be turned on to go live

- **On** : The trading system is considered *live* and orders are sent to the broker

A trading system in this mode cannot be modified and must be moved back to the *ready* mode if some changes are
required.


### Archive mode

A trading system is in **archive** mode when it has been traded in the past but now its performance is not good enough to justify its execution. This mode collects all systems that the user doesn't want to delete. 

When in this mode, a trading system has limited editing capabilities. The only fields that can be modified are:
- Name
- Strategy type
- Overnight flag
- Tags

Trading systems in this mode are not considered by the trading engine so they don't generate trades.


### Technical details

| Mode        | Conditions                                 |
|-------------|--------------------------------------------|
| Development | ts.finalized = false                       |
| Trading     | ts.finalized = true AND ts.trading = true  |
| Archive     | ts.finalized = true AND ts.trading = false |
