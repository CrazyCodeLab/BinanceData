# 币安公开数据

为了帮助用户轻松下载我们的公共数据，我们已将所有货币对的所有 Kline、Trade 和 AggTrade 数据逐月放到网上。

[API 文档](https://binance-docs.github.io/apidocs/spot/cn/#market_data)

## 有哪些数据可用

### 现货

* `聚合交易`
* `K线`
* `交易`


#### 聚合交易

聚合交易是从 `/api/v3/aggTrades` 下载的, 每列的标题如下:

|聚合交易 ID|价格|数量|第一个交易 ID|最后交易编号|时间戳|买家是挂单者|交易是最好的价格匹配|
| -- | -- | -- | -- | -- | -- | -- | -- |
|0|0.20000000|50.00000000|0|0|1608872400000|False|True|

> 聚合交易: 获得压缩的汇总交易。在同一时间从同一订单以相同价格成交的交易将汇总数量。

#### Klines
The klines data is downloaded from `/api/v3/klines` and the title for each column in the kline data:
K线数据从`/api/v3/klines`下载，k线数据中每列的标题如下:

|开盘时间|开盘价|最高价|最低价|收盘价|交易量|收盘时间|报价资产量|交易数量(订单)|吃单者购买的基础资产量|吃单者买入的报价资产量|忽略|
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
|1601510340000|4.15070000|4.15870000|4.15060000|4.15540000|539.23000000|1601510399999|2240.39860900|13|401.82000000|1669.98121300|0|

> 基础资产与报价资产: 交易对有两部分，第一部分为基础资产，第二部分是报价资产，用来显示第一部分的价格. 例如 BTC/USDT 表示用美元表示比特币的价格

#### 交易
The trades data is downloaded from `/api/v3/historicalTrades`, the title for each column in the trades data:
交易数据是从 `/api/v3/historicalTrades` 下载的，交易数据中每一列的标题如下：

|交易编号|价格| 基础货币数量|报价货币数量|时间|是买方挂单|是最佳匹配|
| -- | -- | -- | -- | -- | -- | -- |
|51175358|17.80180000|5.69000000|101.29224200|1583709433583|True|True|

> qty与quoteQty: 交易对有两部分，第一部分为基础资产，第二部分是报价资产，用来显示第一部分的价格. 例如 BTC/USDT 表示用美元表示比特币的价格


### 期货

* U本位期货: 用美元做保证金的期货
* 币本位期货: 用币做保证金的期货

#### 聚合交易

聚合交易与 `/fapi/v1/aggTrades`、`/dapi/v1/aggTrades` 和每列的标题相同：

|聚合交易 ID|价格|数量|第一个交易 ID|最后交易编号|时间戳|买家是挂单者|
| -- | -- | -- | -- | -- | -- | -- |
|26129|0.01633102|4.70443515|27781|27781|1498793709153|true|

#### K线

K线数据与 `/fapi/v1/klines`、`/dapi/v1/klines` 和每列的标题相同：

U本位期货

|Open time|Open|High|Low|Close|Volume|Close time|Quote asset volume|Number of trades|Taker buy base asset volume|Taker buy quote asset volume|Ignore|
|开盘时间|开盘价|最高价|最低价|收盘价|交易量|收盘时间|报价资产量|交易数量(订单)|吃单者购买的基础资产量|吃单者买入的报价资产量|忽略|
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
|1499040000000|0.01634790|0.80000000|0.01575800|0.01577100|148976.11427815|1499644799999|2434.19055334|308|1756.87402397|28.46694368|17928899.62484339|

**币本位期货**

|开盘时间|开盘价|最高价|最低价|收盘价|交易量|收盘时间|基础资产数量|交易数量(订单)|吃单者购买产量|吃单者买入的基础资产量|忽略|
| -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- | -- |
|1591258320000|9640.7|9642.4|9640.6|9642.0|206|1591258379999|2.13660389|48|119|1.23424865|0|

#### Trades

交易数据与`/fapi/v1/trades`、`/dapi/v1/trades`相同，每列的标题:

USD-M Futures

|trade Id| price| qty|quoteQty|time|isBuyerMaker|
| -- | -- | -- | -- | -- | -- |
|28457|4.00000100|12.00000000|48.00|1499865549590|true|

COIN-M Futures

|trade Id| price| qty|baseQty|time|isBuyerMaker|
| -- | -- | -- | -- | -- | -- |
|28457|9635.0|1|0.01037883|1591250192508|true|

## Where do I access it

The base url is `https://data.binance.vision` and you can use your browser to view and download the data.

### Klines

All symbols are supported, the file format is:<br/>
`<base_url>/data/spot/monthly/klines/<symbol_in_uppercase>/<interval>/<symbol_in_uppercase>-<interval>-<year>-<month>.zip`<br/><br/>
e.g. the url for BNBUSDT 1m klines for 2019-01 is:<br/>
`https://data.binance.vision/data/spot/monthly/klines/BNBUSDT/1m/BNBUSDT-1m-2019-01.zip`


#### Intervals

All intervals are supported: 
`1m`, `3m`, `5m`, `15m`, `30m`, `1h`, `2h`, `4h`, `6h`, `8h`, `12h`, `1d`, `3d`, `1w`, `1mo`
- `1mo` is used instead of `1M` to supprt non-case sensitive file systems.

### Trades

All symbols are supported, the file format is:<br/>
`<base_url>/data/spot/monthly/trades/<symbol_in_uppercase>/<symbol_in_uppercase>-trades-<year>-<month>.zip`<br/><br/>
e.g. the url BNBUSDT trades in 2019-01 is:<br/>
`https://data.binance.vision/data/spot/monthly/trades/BNBUSDT/BNBUSDT-trades-2019-01.zip`

### AggTrades

This section will be updated when the data is uploaded.


## How to download programatically

```shell

# download a single file
curl -s "https://data.binance.vision/data/spot/monthly/klines/ADABKRW/1h/ADABKRW-1h-2020-08.zip" -o ADABKRW-1h-2020-08.zip
wget "https://data.binance.vision/data/spot/monthly/klines/ADABKRW/1h/ADABKRW-1h-2020-08.zip"
```

We will expand this section with more methods in the future.

There are additional helper scripts both in python and shell in their respective folders of this repository.

## CHECKSUM
Each zip file has a `.CHECKSUM` file together in the same folder to verify data integrity.

To Check:

```shell
# From Linux, sha256sum -c <zip_file_name.CHECKSUM>
sha256sum -c BNBUSDT-1m-2021-01.zip.CHECKSUM

# From MacOS
shasum -a 256 -c BNBUSDT-1m-2021-01.zip.CHECKSUM
```


## I have an issue/question

Please open an issue [here](https://github.com/binance/binance-public-data/issues). 

## Licence
MIT

```shell
# k 线数据
# Open time,Open,High,Low,Close,Volume,Close time,Quote asset volume,Number of trades,Taker buy base asset volume,Taker buy quote asset volume,Ignore
python download-kline.py --help
# python download-kline.py -s BTCUSDT -i 1m -endDate 2021-12-31 -c 1
python download-kline.py -s BTCUSDT ETHUSDT BNBUSDT SOLUSDT XRPUSDT ADAUSDT LUNAUSDT AVAXUSDT DOTUSDT DOGEUSDT SHIBUSDT NEARUSDT MATICUSDT CROUSDT ATOMUSDT LTCUSDT LINKUSDT UNIUSDT TRXUSDT BCHUSDT FTTUSDT LEOUSDT ETCUSDT ALGOUSDT XLMSDT VETUSDT MANAUSDT HBARUSDT FILUSDT ICPUSDT XMRUSDT EGLDUSDT THETAUSDT SANDUSDT FTMUSDT AXSUSDT APEUSDT RUNEUSDT WAVESUSDT KLAYUSDT XTZUSDT AAVEUSDT HNTUSDT ZECUSDT CAKEUSDT -i 1m -endDate 2021-12-31 -c 1
python download-kline.py -s EOSUSDT FLOWUSDT IOTAUSDT MKRUSDT CVXUSDT XECUSDT GRTUSDT BTTUSDT BSVUSDT STXUSDT ONEUSDT CELOUSDT KCSUSDT NEOUSDT KSMUSDT ZILUSDT GALAUSDT MINAUSDT QNTUSDT ENJUSDT HTUSDT CHZUSDT NEXOUSDT LRCUSDT GMTUSDT DASHUSDT OKBUSDT CRVUSDT ARUSDT BATUSDT KDAUSDT AMPUSDT HOTUSDT TFUELUSDT XEMUSDT COMPUSDT ROSEUSDT SCRTUSDT KAVAUSDT GLMRUSDT ANCUSDT DCRUSDT ICXUSDT YFIUSDT IOTXUSDT -i 1m -endDate 2021-12-31 -c 1

# 历史交易
# trade Id,price,qty,quoteQty,time,isBuyerMaker,isBestMatch
python download-trade.py --help
# python download-trade.py -s BTCUSDT -startDate 2017-06-01 -endDate 2021-12-31 -c 1
python download-trade.py -s BTCUSDT ETHUSDT BNBUSDT SOLUSDT XRPUSDT ADAUSDT LUNAUSDT AVAXUSDT DOTUSDT DOGEUSDT SHIBUSDT NEARUSDT MATICUSDT CROUSDT ATOMUSDT LTCUSDT LINKUSDT UNIUSDT TRXUSDT BCHUSDT FTTUSDT LEOUSDT ETCUSDT ALGOUSDT XLMSDT VETUSDT MANAUSDT HBARUSDT FILUSDT ICPUSDT XMRUSDT EGLDUSDT THETAUSDT SANDUSDT FTMUSDT AXSUSDT APEUSDT RUNEUSDT WAVESUSDT KLAYUSDT XTZUSDT AAVEUSDT HNTUSDT ZECUSDT CAKEUSDT -startDate 2017-06-01 -endDate 2021-12-31 -c 1
python download-trade.py -s EOSUSDT FLOWUSDT IOTAUSDT MKRUSDT CVXUSDT XECUSDT GRTUSDT BTTUSDT BSVUSDT STXUSDT ONEUSDT CELOUSDT KCSUSDT NEOUSDT KSMUSDT ZILUSDT GALAUSDT MINAUSDT QNTUSDT ENJUSDT HTUSDT CHZUSDT NEXOUSDT LRCUSDT GMTUSDT DASHUSDT OKBUSDT CRVUSDT ARUSDT BATUSDT KDAUSDT AMPUSDT HOTUSDT TFUELUSDT XEMUSDT COMPUSDT ROSEUSDT SCRTUSDT KAVAUSDT GLMRUSDT ANCUSDT DCRUSDT ICXUSDT YFIUSDT IOTXUSDT -startDate 2017-06-01 -endDate 2021-12-31 -c 1

# 聚合交易
# Aggregate tradeId,Price,Quantity,First tradeId,Last tradeId,Timestamp,Was the buyer the maker,Was the trade the best price match
python download-aggTrade.py --help
# python download-aggTrade.py -s BTCUSDT -startDate 2017-06-01 -endDate 2021-12-31 -c 1
python download-aggTrade.py -s BTCUSDT ETHUSDT BNBUSDT SOLUSDT XRPUSDT ADAUSDT LUNAUSDT AVAXUSDT DOTUSDT DOGEUSDT SHIBUSDT NEARUSDT MATICUSDT CROUSDT ATOMUSDT LTCUSDT LINKUSDT UNIUSDT TRXUSDT BCHUSDT FTTUSDT LEOUSDT ETCUSDT ALGOUSDT XLMSDT VETUSDT MANAUSDT HBARUSDT FILUSDT ICPUSDT XMRUSDT EGLDUSDT THETAUSDT SANDUSDT FTMUSDT AXSUSDT APEUSDT RUNEUSDT WAVESUSDT KLAYUSDT XTZUSDT AAVEUSDT HNTUSDT ZECUSDT CAKEUSDT -startDate 2017-06-01 -endDate 2021-12-31 -c 1
python download-aggTrade.py -s EOSUSDT FLOWUSDT IOTAUSDT MKRUSDT CVXUSDT XECUSDT GRTUSDT BTTUSDT BSVUSDT STXUSDT ONEUSDT CELOUSDT KCSUSDT NEOUSDT KSMUSDT ZILUSDT GALAUSDT MINAUSDT QNTUSDT ENJUSDT HTUSDT CHZUSDT NEXOUSDT LRCUSDT GMTUSDT DASHUSDT OKBUSDT CRVUSDT ARUSDT BATUSDT KDAUSDT AMPUSDT HOTUSDT TFUELUSDT XEMUSDT COMPUSDT ROSEUSDT SCRTUSDT KAVAUSDT GLMRUSDT ANCUSDT DCRUSDT ICXUSDT YFIUSDT IOTXUSDT -startDate 2017-06-01 -endDate 2021-12-31 -c 1
```
