# stg-premium-chart

Two static web pages that track the STG token against its fixed ZRO conversion ratio of 1 STG = 0.08634 ZRO, using Binance public market data. There is no backend and no API key. The browser calls Binance directly, so the charts keep updating while the tab is open.

## Pages

- `index.html`: premium candles of STG over its fair value, which is 0.08634 times the ZRO spot price, with a price panel below. Choose Binance spot or the USDT-M perpetual, and 1s, 1m, 5m, 15m or 1h candles. Binance has no 1s candles for the perpetual, so that option is disabled there.
- `settlement.html`: settlement price calculator for the Binance STGUSDT perpetual delisting. Binance's delisting FAQ defines the settlement price as the average of the per-second index price over the last 30 minutes, 1,800 samples in total. The page draws the index price and a rolling 30-minute average. Inside the window it also draws a running average and a projected settlement price.

## Use

Open a page in a browser, or serve the folder with any static host such as GitHub Pages. To rehearse the settlement window before the real one, add `?start=` with an ISO time, for example `settlement.html?start=2026-09-20T10:30:00%2B08:00`.

## Notes

- Times on the charts are UTC+8.
- The delisting window in `settlement.html` defaults to 2026-09-24 16:30 to 17:00 UTC+8. Change `WS_ISO` in the file or use `?start=`.
- Seconds before the page opened are filled from 1-minute index prices, so they are approximate. The status panel shows how many real per-second samples were collected.
- Keep the settlement page in a foreground tab. Browsers slow timers in background tabs.
- Binance blocks some regions. If the API is unreachable from your network, the charts stay empty.
- Charts use [Lightweight Charts](https://github.com/tradingview/lightweight-charts) 5.0.8 from jsDelivr, pinned with a Subresource Integrity hash.

Nothing here is financial advice.

## License

MIT
