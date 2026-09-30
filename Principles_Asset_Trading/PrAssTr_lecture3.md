# Principles of Asset Trading — Lecture 3

**Topics:** recap → spot rates and the term structure → forward rates → expectations hypothesis vs risk → real vs nominal interest (Fisher) → valuation of equity → Gordon growth model → cost of equity capital

---

## Summary

The YTM uses **one rate** for all cash flows of a bond. In reality, every maturity has its own rate: the **n-year spot rate** $r_n$. How spot rates vary with maturity is called the **term structure**. The correct PV discounts each cash flow at the spot rate for its own date. So two correctly priced bonds can have **different YTMs**, and a higher YTM does **not** mean a better deal. Spot rates imply **forward rates**, the rates you can lock in today for a future period. Nominal interest grows your _euros_; **real** interest grows your _purchasing power_. Fisher links the two: $1 + r_{\text{nom}} = (1 + r_{\text{real}}) \cdot (1 + i)$. A **stock** is valued like a bond: the PV of its expected dividends. With constant dividends this gives $P_0 = D/r$; with constant growth, $P_0 = DIV_1 / (r - g)$. Inverting the growth formula gives the **cost of equity** $r = DIV_1/P_0 + g$: dividend yield plus growth.

---

## 1. Recap

The recap covers Lecture 2: simple vs compound interest, effective vs nominal rate ($(1 + 5\%/4)^4 - 1 = 5.09\%$), continuous compounding ($e^r$), bond cash flows and YTM, the price–yield chart (convexity), duration and volatility. See the Lecture 2 notes.

⚠️ The recap calls the price–yield chart a **"Yield Curve"**. That's the wrong name. A yield curve plots **yield against maturity**; that chart plots **price against yield**. The real yield/spot curve is what this lecture introduces in §2.

---

## 2. Spot rates and the term structure

### 2.1 Why YTM is not enough

Two bonds in the market:

| Bond      | Price   | YTM   |
| --------- | ------- | ----- |
| 5%, 5 yr  | 85.211  | 8.78% |
| 10%, 5 yr | 105.429 | 8.62% |

The slide labels them "2034", but the prices match 5-year bonds on the curve below, so treat them as 5-year bonds.

The YTM forces **one** rate on every cash flow. If rates differ by maturity, the YTM is just an average, **weighted by when the cash comes in**.

### 2.2 Spot rates

The **n-year spot rate** $r_n$ is the annual interest you receive if you fix an investment for $n$ years, starting today. The curve of $r_1, r_2, \dots, r_n$ is the **(interest-rate) term structure**. Discount each cash flow at **its own** spot rate:

$$PV = c_0 + \frac{c_1}{1+r_1} + \frac{c_2}{(1+r_2)^2} + \dots + \frac{c_n}{(1+r_n)^n}$$

**Worked example:** spot rates of 5%, 6%, 7%, 8% and 9% for years 1–5.

| Year      | Spot | 5% bond: CF | PV        | 10% bond: CF | PV         |
| --------- | ---- | ----------- | --------- | ------------ | ---------- |
| 1         | 5%   | 5           | 4.76      | 10           | 9.52       |
| 2         | 6%   | 5           | 4.45      | 10           | 8.90       |
| 3         | 7%   | 5           | 4.08      | 10           | 8.16       |
| 4         | 8%   | 5           | 3.68      | 10           | 7.35       |
| 5         | 9%   | 105         | 68.24     | 110          | 71.49      |
| **Price** |      |             | **85.21** |              | **105.43** |

These are exactly the market prices, so **both bonds are fairly priced**. The YTMs differ only because of timing:

- The 10% bond gets relatively **more cash early**, which is discounted at the **low** early spot rates. Its average rate (YTM) is therefore lower: 8.62%.
- The 5% bond's value sits mostly in year 5, at 9%. So its YTM is higher: 8.78%.

> **Exam trap:** don't rank bonds by YTM when the term structure isn't flat. Compare them by pricing both with the same spot curve.

---

## 3. Forward rates

### 3.1 Definition and derivation

The forward rate $f_{i,j}$ is the rate agreed **today** for a loan that runs from time $i$ to time $j$. Notation: the lecture uses both $r_n$ and $s_n$ for spot rates.

**Replicating a forward loan from year 1 to year 2 with spot trades:**

1. Today, **lend** $\frac{100}{1+s_1}$ for 1 year. At year 1 you receive **€100**.
2. Today, **borrow** the same $\frac{100}{1+s_1}$ for 2 years. At year 2 you repay $\frac{100}{1+s_1} \cdot (1+s_2)^2$.

Net result: zero cash today, +€100 at year 1, and a repayment at year 2. That is exactly a one-year loan starting next year, so its rate must be:

$$f_{1,2} = \frac{(1+s_2)^2}{1+s_1} - 1$$

If the forward rate were anything else, you could lock in a riskless profit (arbitrage).

**Worked example:** $s_1 = 5\%$, $s_2 = 6\%$.

$$f_{1,2} = \frac{1.06^2}{1.05} - 1 = \frac{1.1236}{1.05} - 1 = 7.01\%$$

On €100 borrowed at year 1, you repay €107.01 at year 2.

**General form [beyond slides]:**

$$1 + f_{n-1,n} = \frac{(1+s_n)^n}{(1+s_{n-1})^{n-1}}$$

For the curve in §2.2 this gives forwards of 7.01%, 9.03%, 11.06% and 13.09%. An upward-sloping spot curve implies forwards **above** the spot rates.

### 3.2 Choosing between strategies

To invest for 2 years, you can:

| Strategy               | Year 1         | Year 2                                |
| ---------------------- | -------------- | ------------------------------------- |
| **A. Roll over**       | 5% (1-yr spot) | next year's 1-yr spot (unknown today) |
| **B. Fix for 2 years** | 6%             | 6%                                    |

Strategy B is equivalent to 5% followed by 7.01%, because $1.06^2 = 1.05 \cdot 1.0701$.

- **Choose B (fix)** if you expect next year's 1-year spot rate to be **below 7.01%**.
- **Choose A (roll)** if you expect it to be **above 7.01%**.

### 3.3 Why is the spot curve usually rising?

- **Expectations hypothesis:** forward rates are the market's forecast of future spot rates. A rising curve means the market expects rates to go up.
- **Risk perspective (liquidity preference):** next year's spot rate is **uncertain**. To commit for longer, investors demand a forward rate **above** the expected future spot rate. That risk premium makes the curve slope up even when rates aren't expected to rise.

---

## 4. Real vs nominal interest

### 4.1 Intuition

The bank grows your savings from $A$ to $A \cdot (1+r)$ **in euros**. That says nothing about how much **stuff** you can buy.

### 4.2 Worked example: bread

- The bank pays 10%, so €2.00 becomes €2.20.
- Bread inflation is 6%, so a loaf goes from €2.00 to €2.12.
- In loaves: 1 loaf now → $2.20 / 2.12 = 1.038$ loaves next year.

$$1 + r_{\text{real}} = \frac{1 + r_{\text{nominal}}}{1 + i} = \frac{1.10}{1.06} = 1.038 \;\Rightarrow\; r_{\text{real}} = 3.8\%$$

⚠️ The lecture's formula has **"inflation rate"** in the denominator. It should be **1 + inflation rate** (1.06, not 0.06).

### 4.3 Fisher's theory

Changes in the nominal rate are driven by the **expected inflation rate** $i$:

$$1 + r_{\text{nominal}} = (1 + r_{\text{real}}) \cdot (1 + i) \qquad \text{approximation: } r_{\text{real}} \approx r_{\text{nominal}} - i$$

The approximation gives 10% − 6% = 4%, while the exact value is 3.77%. The gap grows when rates are high.

- In practice you know the **nominal** return in advance, but not the **real** one, because future inflation is unknown.
- **The lecture's claim:** "the real interest cannot be negative (in a normal situation)", but this is **not true for perishable goods**.
  - **The logic:** you can buy **durable** goods now and store them. A negative real rate would make holding goods better than lending money. You can't store perishable goods (bread, vegetables), so no such floor exists for them.
  - **In practice [beyond slides]:** real rates _have_ been clearly negative. In 2022, eurozone inflation was about 10% while ECB rates were around 0–2%. The intro lecture's "negative interest" and "post-COVID inflation" topics are examples.

---

## 5. Valuation of equity

### 5.1 The same formula as a bond

$$PV(\text{stock}) = PV(\text{cash flows to receive}) = PV(\text{expected dividends})$$

**One period:**

$$P_0 = \frac{DIV_1 + P_1}{1+r}$$

Here $P_0$ is the price now, $DIV_1$ the dividend in 1 year, $P_1$ the price in 1 year, and $r$ the **cost of equity**: the return on stocks with the same risk.

**Substitute** $P_1 = \frac{DIV_2 + P_2}{1+r}$, and keep going:

$$P_0 = \frac{DIV_1}{1+r} + \frac{DIV_2}{(1+r)^2} + \dots + \frac{DIV_n + P_n}{(1+r)^n} = \sum_{k=1}^{n} \frac{DIV_k}{(1+r)^k} + \frac{P_n}{(1+r)^n}$$

As $n \to \infty$, the term $\frac{P_n}{(1+r)^n} \to 0$. So **the price equals the PV of all future dividends**. Price gains are simply future dividends seen by the next buyer.

### 5.2 Constant dividend

With $DIV_k = D$ forever, the stock is a perpetuity:

$$P_0 = \frac{D}{r}$$

**Worked example:** $D = 5$, $r = 15\%$.

- Holding for 20 years and selling at 50: $P_0 = 34.35$. The 20 dividends are worth 31.30, and the sale is worth $50 \cdot 0.0611 = 3.05$.
- Selling at 100 instead: $P_0 = 37.41$. The sale price 20 years out only adds about 3.
- Over an infinite horizon: $P_0 = 5 / 0.15 = 33.33$.

### 5.3 Constant growth: the Gordon growth model

With $DIV_k = D \cdot (1+g)^{k-1}$:

$$P_0 = \sum_{k=1}^{n} \frac{D \cdot (1+g)^{k-1}}{(1+r)^k} + \frac{P_n}{(1+r)^n} \;\xrightarrow{\,n\to\infty\,}\; \boxed{P_0 = \frac{DIV_1}{r - g}} \qquad (g < r)$$

**Worked example:** $D = 5$, $r = 15\%$, $g = 10\%$.

- 20 years, sell at 50: $P_0 = 61.95$.
- 20 years, sell at 100: $P_0 = 65.00$.
- Infinite horizon: $P_0 = 5 / (0.15 - 0.10) = 100$.

**Why don't the 20-year tables reach 100?** The assumed selling price is too low. A **consistent** selling price at year 20 is the Gordon price at that moment:

$$P_{20} = \frac{DIV_{21}}{r-g} = \frac{5 \cdot 1.1^{20}}{0.05} = 672.75$$

With that selling price, the table gives exactly **100**. Likewise, the constant-dividend table should use $P_{20} = 33.33$, which gives exactly 33.33.

> **Exam traps**
>
> - Use $DIV_1$, the **next** dividend, not the one just paid. If $DIV_0$ is given, $DIV_1 = DIV_0 \cdot (1+g)$.
> - The formula only works for $g < r$. As $g$ approaches $r$, the price explodes.
> - The price is very sensitive to $g$: at $r = 15\%$, raising $g$ from 10% to 11% moves $P_0$ from 100 to 125.

---

## 6. Cost of equity capital

### 6.1 Inverting Gordon

Rearranging $P_0 = \frac{DIV_1}{r-g}$ gives

$$r = \frac{DIV_1}{P_0} + g = \text{dividend yield} + \text{growth rate}$$

Take a **stable business** such as a utility, where "constant growth forever" is a reasonable assumption.

### 6.2 Worked example: Northwest Natural Gas (NWN)

From Yahoo: price about \$46.44, dividend \$1.66, EPS \$2.83.

$$\text{Dividend yield} = \frac{1.66}{46.44} = 3.57\%$$

Yahoo shows 3.60%, because it uses a slightly different price.

**Estimating $g$:**

1. **Analysts' forecasts** of dividend or earnings growth.
2. **Historical** dividend growth rates.
3. **Sustainable growth [beyond slides, B&M]:** $g = \text{plowback ratio} \cdot ROE$.
   - Plowback = 1 − payout = $1 - 1.66/2.83 = 41\%$ of earnings is reinvested.
   - Those earnings grow at the return on equity.

_Illustration (assumed g):_ with $g = 4\%$, $r \approx 3.6\% + 4\% = 7.6\%$.

Estimates are noisy, so B&M's advice is to average over a **group of similar firms** (e.g. several utilities) rather than trust one company. **[beyond slides]**

---

## Questions from the lecture

**Q1. The 10% bond (YTM 8.62%) vs the 5% bond (YTM 8.78%): is the 10% bond a better or a worse deal?**
**Answer:** Neither. Both are **fairly priced** on the same spot curve (85.21 and 105.43).
_Why:_ the YTM is an average rate weighted by cash-flow timing. The 10% bond receives more of its value early, at low spot rates, so its average comes out lower. A lower YTM here doesn't mean "worse"; it reflects a different payment pattern.

**Q2. You lend €100 next year for one year. What interest would you want to receive?**
(The slide says "borrow", but asks what you'd _receive_, so it means lending.)
**Answer:** The forward rate $f_{1,2} = 7.01\%$, i.e. €107.01 back at year 2.
_Why:_ you can build this exact loan today from spot trades (§3.1): lend $100/1.05$ for 1 year and borrow the same amount for 2 years at 6%. Any other rate would allow arbitrage.

**Q3. Investing for 2 years: which rate "??%" in year 2 makes rolling over equal to fixing at 6%?**
**Answer:** 7.01%.
_Why:_ $1.06^2 = 1.05 \cdot (1 + f_{1,2})$. If you expect next year's 1-year spot rate below 7.01%, fix now at 6%; above it, roll over.

**Q4. You get 10% interest and bread gets 6% more expensive. What is your real interest ("?%")?**
**Answer:** 3.8% (exactly 3.77%).
_Why:_ €2.20 buys $2.20 / 2.12 = 1.038$ loaves instead of 1. Real interest measures growth in goods, not euros: $1.10 / 1.06 - 1$.

**Q5. How important is the stock price in 1 year?**
**Answer:** Very important. In the constant-dividend example ($D = 5$, $r = 15\%$), about **87%** of today's price comes from $P_1$.
_Why:_ $P_0 = (5 + 33.33) / 1.15 = 33.33$, and $P_1$ contributes $33.33 / 1.15 = 28.99$ of that. But $P_1$ is itself just the PV of the dividends after year 1. That's why, taken to the limit, the price equals the PV of all dividends.

**Q6. You can sell for 100 at year 20 instead of 50 (constant dividend). What will the stock price be?**
**Answer:** 37.41 instead of 34.35, about +3.
_Why:_ an extra 50 received in 20 years is worth only $50 \cdot 0.0611 = 3.05$ today. Far-away cash flows barely matter at 15%, which is why the terminal term goes to 0.

**Q7. In reality dividends grow. Why?**
**Answer:** Firms **reinvest** part of their earnings (plowback). New investments raise future earnings, and with them future dividends. Inflation also raises nominal earnings over time.
_Why:_ a firm that paid out all earnings and never invested would just keep a constant dividend. Growth comes from retained earnings earning a return (§6.2).

**Q8. What should you pay if dividends grow 10% every year?**
**Answer:** €100: $P_0 = 5 / (0.15 - 0.10)$. The 20-year table with a sale at 50 gives only 61.95.
_Why:_ growing dividends are worth much more than a flat stream of 5. The Gordon formula is the infinite-horizon value.

**Q9. Again, what if you can sell for 100 instead of 50 (growing dividends)?**
**Answer:** 65.00 instead of 61.95.
_Why:_ same effect as Q6. The extra 50 is worth only 3.05 today. The table is still far from 100 because both selling prices are far too low (see Q10).

**Q10. Why did we not arrive at 100 in the previous table? What should the selling price have been?**
**Answer:** $P_{20} = 5 \cdot 1.1^{20} / 0.05 = 672.75$. With that selling price, the table gives exactly 100.
_Why:_ the buyer at year 20 pays the PV of all dividends from year 21 onward, which by then have grown to $5 \cdot 1.1^{20} = 33.64$ per year. A selling price of 50 or 100 ignores that growth.

**Q11. Derive $P_0 \to D/(r-g)$ (homework assignment).**
**Hint only**, since this is an assignment:

1. Write the dividend sum as a **geometric series** with ratio $q = \frac{1+g}{1+r}$.
2. Use $\sum_{k=1}^{n} q^{k-1} = \frac{1 - q^n}{1 - q}$.
3. Simplify $\frac{D}{1+r} \cdot \frac{1}{1-q}$.
4. Check what happens to $q^n$ as $n \to \infty$ when $g < r$.

Send me your derivation and I'll check it.

**Q12. How do you determine the growth rate g?**
**Answer:** Three ways:

- analysts' forecasts
- historical dividend growth
- sustainable growth $g$ = plowback ratio · ROE

_Why:_ $g$ can't be observed, so each method estimates it. Since $r = DIV_1/P_0 + g$, any error in $g$ goes one-to-one into the cost of equity. That's why you average over several similar firms. (The third method and the averaging advice are **[beyond slides]**, from B&M.)

---

## Key-formulas box

$$PV = c_0 + \sum_{k=1}^{n} \frac{c_k}{(1+r_k)^k} \qquad f_{1,2} = \frac{(1+s_2)^2}{1+s_1} - 1 \qquad 1 + f_{n-1,n} = \frac{(1+s_n)^n}{(1+s_{n-1})^{n-1}}$$

$$1 + r_{\text{nominal}} = (1 + r_{\text{real}}) \cdot (1 + i) \qquad r_{\text{real}} \approx r_{\text{nominal}} - i$$

$$P_0 = \frac{DIV_1 + P_1}{1+r} \qquad P_0 = \frac{D}{r} \qquad P_0 = \frac{DIV_1}{r-g} \qquad r = \frac{DIV_1}{P_0} + g$$

## Python check

```python
s = [0.05, 0.06, 0.07, 0.08, 0.09]
pv = lambda cf: sum(c/(1+s[k])**(k+1) for k, c in enumerate(cf))
print(round(pv([5]*4 + [105]), 2), round(pv([10]*4 + [110]), 2))  # 85.21 105.43

print(round(1.06**2/1.05 - 1, 4))   # 0.0701  (forward f12)
print(round(1.10/1.06 - 1, 4))      # 0.0377  (real rate)

r, D, g = 0.15, 5, 0.10
stock = lambda g, sell, n=20: sum(D*(1+g)**(k-1)/(1+r)**k for k in range(1, n+1)) + sell/(1+r)**n
print(round(stock(0, 50), 2), round(stock(g, 50), 2))   # 34.35 61.95
print(round(stock(g, D*(1+g)**20/(r-g)), 2))           # 100.0
```

---

## Links to earlier lectures

- **Lecture 2:** YTM was the single discount rate. Spot rates refine it, one rate per maturity, and the YTM is their cash-flow-weighted average. The WSJ Treasury table was already a term structure.
- **Lecture 1:** $P_0 = D/r$ is the perpetuity $P = A/r$, and the Gordon formula is a growing perpetuity. The cost of equity is the opportunity cost of capital for shareholders (the 12% "stock-like risk" rate).
- **Lecture 1:** the one-period stock formula $P_0 = (DIV_1 + P_1)/(1+r)$ is the same PV logic as the office building ($420 / 1.12$).
- **Intro:** Fisher links to the inflation actuality: negative real rates after COVID. The intro's ETFs as "passive investing" link to using market prices ($P_0$) to back out $r$.

## Open questions

1. Does the lecturer mean "real rates can't be negative" as a theoretical equilibrium claim, given the real negative rates of 2020–2022?
2. How are spot rates found in practice when most bonds pay coupons? (Bootstrapping from bond prices, or zero-coupon strips.) **[beyond slides]**
3. Expectations vs risk premium: can you ever separate the two from market data?
4. What if a firm pays no dividends (many tech firms)? Does "PV of dividends" still work, e.g. via buybacks or future dividends? **[beyond slides]**
5. How does the Gordon model connect to CAPM for estimating $r$ (later in the course)?
