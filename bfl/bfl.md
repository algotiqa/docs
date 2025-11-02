# Data types

## Basic types

| Type | Description                  |
|------|------------------------------|
| int  | 64 bit signed integer        |
| real | 64 bit floating point number |
| bool | Boolean value                |
|string| Unicode string               |

## Nulls

A *null* is a special value

## Containers

Containers are types that contain elements inside them. These elements can be ordered (lists) or unordered (maps, sets)

### Lists

Represents a list of elements of any type (basic, container, class or null). 

Examples:
```
a = list of [n] int
a.add(5)
a.get(index)
a.add(null)
a.size()
a.clear()
a.deleteAt(index)
```

### Maps

Allows to store (key,value) pairs. 
- Keys can be string or int
- Values can be of any type (basic, container, class or null)

Examples:
```
a = map of string,int
a.get(key)
a.set(key,value)
a.contains(key)
a.size()
a.clear()
a.delete(key)
```

### Sets

## Classes

# Conditions

```
if <condition> { statement* }
[else if <condition> { statement* }]*
[else { statement* }]
```

```
switch myVar {
 case <value>:
    statement*
 case <value>:
    statement*
 default:
    statement*
}
```

# Loops

## For loops

```
for e in listObject {
    e.index
    e.value
    e.isLast
}
```

```
for e in mapObject {
    e.key
    e.value
    e.isLast
}
```

```
for i=0; i<5; i++ {
}

```

## While

```
while <condition> {
}
```

# Functions and methods

Parameters are passed by reference (also for basic types?)

# Structure

## File structure

Given a folder (i.e. the strategy's code folder), all *.bfl files into this folders are loaded. 
Subfolders are scan recursively.

Each source file will have the following structure:
- Class definitions
- Variable definitions
- Function definitions
- Strategy definition
- Interface definition


## Packages

Each strategy code will land into the *default* package.

Users will have the possibility to create other packages. If a user will use an existing system package
the user's package will have priority when resolving functions. This allows users to patch or improve the
system packages.

There will be the following system packages: os, io, math. An administrator will have the possibility
to install new versions of these packages.

# Runtime environment

## Runtime variables

The following variables will be available to a strategy:

- open, close, high, low: time series indicating the current price values
- openS, closeS, highS, lowS: time series for session related values (typically 1 value per day)

### The *bar* object

| Property         | Description                                                             |
|------------------|-------------------------------------------------------------------------|
| index            | Starts from 0 and represents the number of bars that has been processed |
| open             |                                                                         |
| close            |                                                                         |
| high             |                                                                         |
| low              |                                                                         |
| openS            |                                                                         |
| closeS           |                                                                         |
| highS            |                                                                         |
| lowS             |                                                                         |
| isSessionStarted | Indicates if this bar is the first bar of a new session                 |
| isSessionEnded   | Indicates if this bar is the last bar of the session                    |


### The *trade* object

Represents the current trade and contains the following properties and methods:

| Property   | Description                                                                                         |
|------------|-----------------------------------------------------------------------------------------------------|
| position   | Can be positive (for long) or negative (for short). The quantity represents the number of contracts |
| isLong     |                                                                                                     |
| isShort    |                                                                                                     |
| isFlat     |                                                                                                     |
| profit     | Current profit of the trade. Can be positive (gain) or negative (loss)                              |
| maxProfit  | Max profit achieved by the trade                                                                    |

Methods:

| Method | Description                                               |
|-----|-----------------------------------------------------------|
| close | Closes the open position, buying or selling all contracts |

## Events

- onTradeEnter(): called when a new trade has started
- onTradeExit(): called when exiting from a trade. Can be used to export trades
- onSessionStart()
- onSessionEnd()

# Future

- Possibility to apply a transformation on input prices
