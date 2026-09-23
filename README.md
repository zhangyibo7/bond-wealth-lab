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
- Starting valuation accepts either nominal annual YTM or clean price per 100.
- YTM compounds at the selected coupon frequency.
- Add any number of dated YTM shocks between settlement and maturity.
- Each shock persists after its date and combines cumulatively with later shocks.
- Wealth at each date equals dirty bond value plus coupons received in cash.
- Carry + roll-down equals date-specific P&L on the unchanged-YTM path.
- Yield-shock price impact equals shocked-path wealth minus unchanged-YTM wealth on the same date.
- The payback schedule covers every dated shock. For each positive yield shock that creates an immediate loss, payback is the first later date when the full shocked path regains the wealth level immediately before that shock. Later shocks can change each payback date. Negative shocks are shown as no-loss events.
- Coupons can be reinvested fractionally in the same bond at its dirty price, or compounded in a fixed-return cash account.
- Taxes, transaction costs, default risk, and curve-shape changes are excluded.
