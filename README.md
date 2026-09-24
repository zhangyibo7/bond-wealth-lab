# Bond Wealth Lab

A dependency-free, single-page fixed-rate bond scenario tool. It can be hosted directly with GitHub Pages.

## Publish with GitHub Pages

1. Create a new GitHub repository.
2. Upload `index.html` to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch and `/ (root)`, then save.

## Model conventions

- Fixed-rate, non-callable bullet bond.
- Switch between **Simple bond** (a single YTM) and **Curve** models.
- Starting valuation accepts either nominal annual YTM or clean price per 100.
- YTM compounds at the selected coupon frequency.
- In Curve mode, enter continuously compounded zero rates at 1Y, 2Y, 3Y, 5Y, 7Y, 10Y, 20Y, and 30Y. Rates between nodes use linear interpolation.
- Curve mode calculates static-curve roll-down and supports dated, independent shocks at every curve tenor.
- Index mode models a bond index or ETF from investment amount, starting yield, constant modified duration, holding period, and optional convexity.
- Index income is automatically reinvested at the prevailing yield. Each dated yield shock changes price using duration/convexity and changes future carry.
- Add any number of dated YTM shocks between settlement and maturity.
- Each shock persists after its date and combines cumulatively with later shocks.
- Wealth at each date equals dirty bond value plus coupons received in cash.
- Carry + roll-down equals date-specific P&L on the unchanged-rate path. In Curve mode, this includes the price effect of rolling down a static zero curve.
- Yield-shock price impact equals shocked-path wealth minus unchanged-YTM wealth on the same date.
- The payback schedule covers every dated shock. For each positive yield shock that creates an immediate loss, payback is the first later date when the full shocked path regains the wealth level immediately before that shock. Later shocks can change each payback date. Negative shocks are shown as no-loss events.
- Coupons can be reinvested fractionally in the same bond at its dirty price, or compounded in a fixed-return cash account.
- Taxes, transaction costs, default risk, and curve-shape changes are excluded.
- Index mode also excludes fees, tracking error, spread/default losses, and changes in duration or convexity.
