# Roadmap

## Phase 1

| Feature/component                | Status | Notes                                                                                                                                                           |
|----------------------------------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Strategy metrics export          | 100%   |                                                                                                                                                                 |
| Strategy fetcher                 | 100%   |                                                                                                                                                                 |
| Strategy import on DB            | 100%   | Portion of code that connects to the strategy fetcher, retrieves the metrics and store them into a local DB. Implemented in the portfolio trader component      |
| Portfolio monitoring             | 100%   | Display retrieved metrics in a chart, enabling or disabling trading systems. Supports drawdowns and equities (at the trading system level and at overall level) |
| Authentication and authorization | 100%   | Add Keycloak as an identity provider and implement frontend and backend authentication                                                                          |
| Trading system filtering         | 100%   | Add rules to provide hints to activate/deactivate trading systems                                                                                               |
| Portfolio optimization           | 0%     | Combine rules above to rank trading systems and decide which one should be activated or not                                                                     |
| Periodic filtering actions       | 0%     | Implement a process that periodically analyzes the trading systems and (say every week) provides a rank result                                                  |

## Phase 2

| Feature/component        | Status | Notes                                                                                                                                                         |
|--------------------------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Data collector           | 10%    | Collect instrument metrics from several sources and stores it locally.<br/>- core data management<br/>- REST API<br/>- UI: data visualization (daily, annual) |
| BFS data import          | 0%     | BFS command to import ascii metrics into the local adapter                                                                                                    |
| System adapter           | 100%   | Adapter component to abstract trading primitives and adapt requests to adapters                                                                               |
| Local adapter            | 5%     | Adapter to store local metrics exported from other systems                                                                                                    |
| IB adapter               | 5%     | Adapter for Interactive Brokers                                                                                                                               |
| Shell                    | 40%    |                                                                                                                                                               |
| BIAS analyzer            | 0%     | Possibility to analyze instrument BIASES in order to create strategies                                                                                        |
| Margin + balance monitor | 0%     | Possibility to retrieve the daily min/max margin and balance and display it in a chart                                                                        |

## Phase 3

| Feature/component | Status | Notes                                                                                     |
|-------------------|--------|-------------------------------------------------------------------------------------------|
| BFL parser        | 0%     | Parser for the BitFever Language. Include language definition through a BFNL              |
| Sick engine       | 0%     | Library to run BFL code, loading it from a folder                                         |
| Rewind engine     | 0%     | Library to run backtesting using BFL code                                                 |
| Realtime trading  | 0%     | Portfolio trader: use Rewind and Sick to run live trading systems                         |
| Auto on/off       | 0%     | Portfolio trader: activate/deactivate live trading systems depending on their performance |
| Position sizing   | 0%     | Portfolio trader: add position sizing to a portfolio                                      |
