# Chart-reader feature engineering

Hamza's saved XGBoost model used 47 inputs. Instead of interpreting chart screenshots, the pipeline represented chart structure numerically.

| Feature family | Examples |
|---|---|
| Momentum | 1-, 5-, 10-, 20-day returns |
| Trend | Close relative to 10-, 20-, 50-, 100-, 200-day moving averages; slope and trend strength |
| Volatility | 10- and 20-day volatility, consolidation range, daily range |
| Support/resistance | Distance from trailing levels, breakout and breakdown flags |
| Market structure | Higher highs/lows, lower highs/lows, swing events, breaks of structure |
| Candle geometry | Body, upper/lower wick, close position as fractions of daily range |
| Volume | Relative volume and breakout/breakdown confirmation |

The V2 implementation sorts observations by ticker and date, uses shifted rolling windows for swing detection, forward-fills known swing levels within each ticker, and compares today's close with prior known levels. Zero-range candles are handled explicitly. The volume confirmation feature compares volume with a trailing mean that excludes the current day.

The integration artifact exports Date, Ticker and chart_probability_up. The probability represents a higher next trading close, not the expected return magnitude. The original chart selection used ROC-AUC and MCC as a tie-breaker. Fourteen chart inputs could be reconstructed for the combined-feature experiments; the separately saved chart probability uses all 47 features.
