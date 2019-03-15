# About

VIZBTS is a Market Pegged Asset issued on the BitShares blockchain. It purpose is to represent a value of 1 VIZ token.

The main goal is to provide **collaterized** trustless asset. Asset is backed by a collateral and can be force settled to get corresponding backing asset amount.

# Target audience

The general audience are those who involved in [VIZ community](https://viz.world/).

* VIZ holders: can deposit VIZ into gateway and get **collaterized** VIZBTS  to trade later (Note: there is no such gateway yet)
* VIZ buyers: buy VIZBTS and withdraw it via secure gateway or excange for XCHNG.VIZ UIA and use their gateway to withdraw
* Traders: can trade XCHNG.VIZ/VIZBTS pair at a fixed spread with center price of 1 to get profits from allowing XCHNG.VIZ <---> VIZBTS exchange (XCHNG.VIZ is an UIA for VIZ, you can deposit/withdraw it via [XCHNG service](https://viz.world/media/@xchng/%D0%BF%D1%80%D0%B0%D0%B2%D0%B8%D0%BB%D0%B0-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B-%D0%B0%D0%B2%D1%82%D0%BE%D0%BC%D0%B0%D1%82%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%BE%D0%B3%D0%BE-%D1%88%D0%BB%D1%8E%D0%B7%D0%B0-xchngviz/))
* Shorters: can borrow VIZBTS to open a short position and then buy back at lower price
* Market makers: trade VIZBTS/XXX pairs to get profits from spread and volatility without carrying gateway risks

# Price feeding

Price feeding currently performed by asset issuer. Because VIZ markets are not yet well-established and VIZ is not listed on exchanges except BitShares, we'll use a special techniques to provide price feed:

* Measure buy order book depth for at least 1000 VIZ on several markets to calculate where is strong buy support. Use averaged buy prices across markets.
* Avoid manipulations by not allowing explosive feed price rise (see below)

# Margin Call protection

At this point, borrowers are protected from **sudden** margin calls by limiting feed price elevation rate. Despite of market movements, feed price daily increase is limited by ~10% rate.

If price moving in down direction, feed price will be adjusted down with no limits.

# Force settlements

Force settlements are recommended as emergency mechanism when asset holder cannot exchange their VIZBTS to another asset for some reason, or for absolutely emergency case when VIZBTS asset issuer is lost (e.g. sudden death).

To discourage unconducive force settlements and protect borrowers, a **Force Settlement Offset** is set to 6%. This means, if feed price is 1, asset holder will settle at price `1 - 6% = 0.94`