Bitcoin Market Sentiment & Trader Performance Analysis


211,224 Hyperliquid perpetuals trades · May 2023 – May 2025 · Bitcoin Fear/Greed Index



An end-to-end data analysis project exploring the relationship between Bitcoin market sentiment and trader performance on Hyperliquid — uncovering counterintuitive patterns that challenge common trading narratives.


The Core Finding

Fear, not Greed, produces the most total profit.

Despite Extreme Greed having the highest win rate (89.2%), the Fear regime generates $3.36M in total PnL — more than any other sentiment state. Traders take larger, more decisive positions when sentiment is negative, amplifying absolute returns even as individual win rates dip.


Project Structure

bitcoin-sentiment-analysis/
│
├── README.md                              ← You are here
├── index.html                             ← Interactive web dashboard (open in browser)
├── Bitcoin_Sentiment_Trader_Analysis.pdf  ← 5-page PDF report for sharing
│
└── data/
    ├── historical_data.csv                ← Hyperliquid trade records (211K rows)
    └── fear_greed_index.csv               ← Daily BTC Fear/Greed Index


Datasets

DatasetSourceDate RangeRecordsHyperliquid Historical TradesHyperliquidMay 2023 – May 2025211,224 rowsBitcoin Fear/Greed Indexalternative.meFeb 2018 – May 20252,648 rows

Key columns used:


Account — trader wallet address
Coin — traded asset (BTC, ETH, SOL, HYPE, etc.)
Side — BUY / SELL
Direction — Long / Short
Closed PnL — realised profit/loss per trade
Size USD — notional trade size in USD
Timestamp IST — trade execution time
classification — Fear/Greed label (Extreme Fear → Extreme Greed)
value — Fear/Greed index score (0–100)



Key Metrics

MetricValueTotal closed PnL$10.3MTotal trades211,224Trades with closed PnL84,402Average win rate84.4%Best sentiment regime (total PnL)Fear — $3.36MBest sentiment regime (win rate)Extreme Greed — 89.2%Top trader total PnL$2.14MDate rangeMay 2023 – May 2025


Analysis Breakdown

1. PnL by Sentiment Regime

SentimentMean PnL/TradeWin RateTotal PnLAvg Trade SizeExtreme Greed$130.2189.2%$2.72M$3,112Fear$112.6387.3%$3.36M$7,816Greed$85.4076.9%$2.58M$5,737Neutral$71.2082.4%$1.04M$4,783Extreme Fear$71.0376.2%$0.60M$5,350

2. Long vs Short Win Rates

SentimentLong Win RateShort Win RateFear89.9%83.7%Extreme Greed88.8%89.4%Neutral86.2%77.7%Greed86.7%72.3%Extreme Fear84.7%63.5% ⚠️

Short positions collapse to 63.5% win rate during Extreme Fear — the worst possible time to bet against the market.

3. Volume by Sentiment

SentimentTotal VolumeAvg Trade SizeFear$483.3M$7,816Greed$288.6M$5,737Neutral$180.2M$4,783Extreme Greed$124.5M$3,112Extreme Fear$114.5M$5,350

Fear generates 4× more volume than Extreme Greed — driven by liquidations, stop cascades, and heightened position management.

4. Monthly Highlights


December 2024 — $3.0M (FG ~77, Greed): Driven by HYPE token launch on Hyperliquid
August 2024 — -$107K (FG ~34, Fear): Only negative month; macro uncertainty spike
Excluding December 2024, monthly average normalises to ~$350K


5. Top 10 Traders

RankWalletTotal PnLTradesAvg PnL/Trade10xb123...ed23$2,143,3836,279$341.3620x0833...9012$1,600,2301,732$923.9230xbaaa...7864$940,1649,997$94.0440x513b...4ff1$840,4235,482$153.3150xbee1...9aab$836,08122,551$37.0860x4acb...09f4$677,7472,233$303.5170x7274...7abd$429,356737$582.5780x430f...7413$416,542599$695.4090x72c6...72a0$403,012564$714.56100x75f7...70d4$379,0958,660$43.78

Two dominant styles emerge: high-frequency (many trades, lower avg) vs high-conviction (fewer trades, 2.7× higher avg PnL per trade).


Key Insights

The Fear Paradox
Fear produces the highest total profit despite lower per-trade metrics because traders take larger, more decisive positions — avg trade size in Fear ($7,816) is 2.5× Extreme Greed ($3,112).

Extreme Fear Is a Trap
The popular "buy the blood" narrative doesn't hold statistically. Extreme Fear has the lowest win rate (76.2%), lowest avg PnL, and shorts collapse to 63.5% — execution risk in panic conditions is severely underestimated.

The Volume Paradox
Markets are most active when scared. $483M flows in Fear vs $124.5M in Extreme Greed — fuelled by forced liquidations and emotional trading, not informed positioning.

Long Bias Dominates
Long positions maintain 86–90% win rates across all regimes, reflecting the structural upward bias of the 2023–2025 crypto bull cycle. Shorts are only competitive in Extreme Greed (89.4%).

December 2024 Outlier
A single month accounts for 29% of all dataset PnL. Event-driven alpha (new token launches, protocol milestones) creates asymmetric opportunities that dwarf sentiment-based edge.

Strategy Divergence
High-conviction traders (fewer, larger trades) outperform high-frequency traders on a per-trade basis by 2.7×. Selectivity beats frequency.


Recommended Strategy by FG Zone

FG RangeRegimeRecommended Action75–100Extreme GreedReduce longs · consider shorts (89.4% short win rate)51–74GreedHold longs · avoid new shorts46–54NeutralSelective entries on pullbacks25–49Fear ★Accumulate longs aggressively (best total PnL)0–24Extreme FearWait · micro-size longs only · avoid shorts entirely


Tools & Libraries

ToolPurposePython 3Data processing & analysispandasData manipulation & mergingnumpyNumerical operationsmatplotlibChart generation (PDF)reportlabPDF report generationChart.jsInteractive charts (HTML dashboard)


Methodology


Data ingestion — Loaded both CSVs with pandas
Date parsing — Converted Timestamp IST (DD-MM-YYYY HH:MM) to date objects
Merge — Left-joined trade data onto Fear/Greed Index by date; 99.997% coverage
Filtering — Isolated closed trades (Closed PnL != 0) for performance analysis
Aggregation — Grouped by sentiment classification for PnL, win rate, volume, and directional metrics
Time series — Monthly resampling with dual-axis Fear/Greed overlay
Trader ranking — Grouped by wallet address, filtered to minimum 10 trades



Deliverables


index.html — Fully self-contained interactive dashboard; open in any browser, no server required
Bitcoin_Sentiment_Trader_Analysis.pdf — 5-page formatted report with all charts and insights tables



Disclaimer

This analysis is for educational and research purposes only. Past performance of sentiment-based strategies does not guarantee future results. Nothing in this project constitutes financial advice.
