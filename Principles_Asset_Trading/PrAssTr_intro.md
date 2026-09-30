# Principles of Asset Trading — Introduction to Finance

_Lecturer: Jasper Anderluh · Source: IntroductionToFinance_2026 slides (plus general knowledge where marked **[beyond slides]**)_

**Agenda:** why a financial system → actors → instruments → trading → security of the system → actualities

---

## Summary

The financial system exists because specialisation of labour creates a need for **exchange**. Money provides that exchange, and it also enables **saving** (shifting consumption over time), **safe storage** (banks) and **capital reallocation** (investors fund people with ideas). A set of actors (consumers, companies, banks, insurers, pension funds) uses a set of instruments (money, deposits, bonds, stocks, ETFs, derivatives). These instruments trade on exchanges and settle through a CCP/CSD infrastructure. Watchdogs (central banks, regulators, governments) keep the whole system stable. The 2008 credit crisis shows what happens when that stability fails.

---

## 1. Why a financial system?

- **Welfare** is defined (abstractly) as _the extent to which scarcity can be reduced_.
- Earth's resources are fixed, so growing welfare means **becoming more productive** over time.
- **Drivers of productivity:**
  - **Tools**, e.g. hunters using weapons.
  - **Specialisation of labour**, which exploits the fact that people are skilled differently (the small hunter vs the big builder).
  - **Connectivity and automation**, the accelerator of today's growth.
- **Is growth intrinsic?** People prefer tools to manual labour and automate repetitive work. They are also never satisfied with the status quo and enjoy being busy. So productivity keeps growing, which is not the same thing as growth in consumption.
- **Needs for the financial system:**
  1. **Exchange.** Specialisation means goods and services must be traded, and money is the convenient medium.
  2. **Saving.** You build houses in summer and buy food with that money in winter.
  3. **Safe storage.** A bank keeps the money safe.
  4. **Investment.** Wealth differences emerge, and people with ideas but no capital need investors. This is how a complex financial system is born.
- **Financial centres:** London (the _former_ US–Europe bridge), New York (NYSE), Chicago (CBOE), Hong Kong, Singapore, Tokyo, Shanghai, Shenzhen, Frankfurt (ECB, rising after Brexit), Amsterdam.

---

## 2. Actors

| Actor             | Role in the system                                                                                                                                                                                                                                                                            |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Consumers**     | **Transfer** money (cash = _chartaal_, bank money = _giraal_) · **store** it · **invest** it · **borrow** against future earnings · **insure** against low-probability, high-loss events                                                                                                      |
| **Companies**     | **Transfer** money under payment controls (4-eyes principle) · **treasury**: manage liquidity daily and use credit lines · **attract money** by issuing bonds or stocks · **hedge** foreign-currency or raw-material costs (airline fuel)                                                     |
| **Banks**         | Defined by **holding client money on their own balance sheet**, not by lending · **provide loans** from deposits, which is how banks create money · **other services**: clearing infrastructure, trading on own account, issuing products                                                     |
| **Insurers**      | **Law of large numbers**: pooled risks diversify, so a fixed premium can cover individual risk · **treasury**: invest premiums against long-term liabilities (e.g. 40-year life policies) · **reinsurance** (Munich Re, Swiss Re) spreads locally correlated risks such as regional disasters |
| **Pension funds** | Provide income to retirees on collectively agreed terms · hold **large asset pools** that are hard to store safely and big enough to move markets when reinvested · act as **insurers under defined benefit (DB)** but **not under defined contribution (DC)**                                |
| **Central banks** | **Stability** watchdog · **monetary policy** (keep inflation acceptable) · **payment infrastructure** for cash and securities · **oversight of banks** (regulatory equity) · **resolution** (orderly wind-down of failing banks)                                                              |
| **Regulators**    | **Market access of parties** (licences) · **behavioural oversight** (_gedragstoezicht_): products and information must serve the client · **market access of products** (approve prospectuses)                                                                                                |
| **Governments**   | **Debt issuer** (government bonds) · **safe haven**: government debt is the risk-free benchmark, and governments organise the deposit guarantee system · **financial laws** that shape the system                                                                                             |

---

## 3. Financial instruments

### 3.1 Money

- **Coins became notes.** Coins had intrinsic metal value. Promissory notes (brought from Asia to Europe by Marco Polo) are worthless as material, so you must **trust the issuer**.
- **Notes became bank money.** Through a network of banks you can deposit in one place and withdraw in another.
- **Money has a currency.** Interest rates depend on the currency, largely because inflation differs by country or region.

### 3.2 Savings and term deposits

- Savings sit **on the bank's balance sheet**. The bank uses them for loans and trading and pays you interest in return, so your money is **at risk**. It is protected by regulation and the deposit guarantee system.
- **Term deposit:** the money is locked for a fixed period (6 months, 2 years, …). The interest rate depends on the term.

### 3.3 Bonds

- A fixed-term loan issued by governments or companies, e.g. 5 years with a 2% coupon.
- **Nominal (face) value:** the loan amount of one bond (e.g. €1,000 or $250,000), repaid at **maturity**.
- **Coupon:** the yearly interest on the face value.
  - Example: face value €1,000, coupon 2%. You receive €20 per year, and €1,020 at maturity.
- **Credit spread:** government bonds pay the risk-free rate for that currency. Companies pay a bit more, and that extra is the credit spread.

### 3.4 Stocks

- A share makes you a **partial owner** of the company. If the company goes bankrupt, the shares are worthless.
- **Dividends:** profits paid out to shareholders.
- **Listed vs unlisted:** listed shares trade on an exchange. Many companies are unlisted, some owned by private equity (e.g. HEMA).
- **You have a say:** the shareholder meeting is the final decision maker.

### 3.5 ETFs

- A basket of stocks that tracks an index (AEX, EuroStoxx50).
- **Cheap:** no stock analysis is needed, so fees are low, e.g. 25 bp = 0.25% (100 bp = 1%).
- **Passive:** the fund follows the price discovery of the individual stocks. Theory later in the course (market efficiency) says this is a good way to invest.
- **Complicated under the hood:** tracking is optimised with correlating portfolios and securities lending.

### 3.6 Derivatives

A contract whose **terminal value depends on an underlying value**.

**Forwards and futures**

- The buyer has the **obligation** to buy the underlying at a price agreed now.
- **Forward:** a bilateral (OTC) contract.
- **Future:** a forward traded on an exchange.
  - The futures price is set so that the contract's **current value is 0**, so nothing is paid on entry.
  - **Both** buyer and seller have obligations.
  - Examples: Bund futures, S&P 500 futures (traded 24 hours), index futures, Brent oil, rice, lumber, silver.
  - Size is large for retail: an AEX future moves **€200 per index point**.

**Options**

- The buyer gets the **right** to buy (**call**) or sell (**put**) the underlying at the **strike** $K$.
- **European** options are exercised **at** maturity; **American** options can be exercised **until** maturity.
- Payoffs at maturity:

$$\text{Call: } \max(S_T - K,\ 0) \qquad \text{Put: } \max(K - S_T,\ 0)$$

- Payoff diagrams: the call is flat at 0 up to $K$, then rises with slope +1. The put falls with slope −1 until $K$, then is flat at 0.

  ![Payoff of a long call at maturity](../pictures/PrAssTr/PrAssTr_intro_call-payoff.png)

  ![Payoff of a long put at maturity](../pictures/PrAssTr/PrAssTr_intro_put-payoff.png)

**Long vs short**

- **Long = buyer.**
  - The option buyer holds a right, so the option has positive value and the buyer **pays a premium**.
  - Using the right is called **exercise**.
- **Short = seller ("writer").**
  - The option seller has an **obligation** and **receives the premium**.
- **Futures:** both sides have obligations, and the price is balanced so nothing is paid at entry.

**Other derivatives**

- **Swaps:** exchange fixed interest payments for floating ones.
- **Turbos / speeders:** bank-issued products with an embedded loan, giving leverage.
  - Worked example: ING trades at €15 and you pay €2.50 for the turbo, so you borrow €12.50.
  - If ING moves −€2.50, you lose 100%. If it moves +€2.50, you gain 100%.
  - Leverage $= 15 / 2.5 = 6\times$.
  - The interest due is added to the **stop-loss level** every night.
- **CFDs:** similar to turbos, but offered directly by brokers, with extreme leverage, terrible interest rates and bad prices. The slide calls them _"Poison!!"_

---

## 4. Trading financial instruments

### 4.1 Orders

An order specifies:

- the **instrument**
- **buy or sell**
- the **quantity**
- the **limit price**: the maximum price for a buy, the minimum for a sell. An order with no limit is a **market order** (_bestens_).

### 4.2 Euronext continuous-trading timeline

| Time        | Phase                     | What happens                                                                                                                 |
| ----------- | ------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| 07:15       | **Pre-opening**           | Orders are entered but **not matched**. The exchange publishes a _theoretical opening price_.                                |
| 09:00       | **Opening auction**       | Order entry stops and the opening price is calculated (see rule below).                                                      |
| 09:0x–17:30 | **Continuous trading**    | Incoming orders are matched if a counterparty exists; otherwise they rest in the **order book**.                             |
| 17:30       | **Pre-closing**           | Matching stops. New orders go into the book and a theoretical closing price is calculated.                                   |
| 17:35       | **Closing auction**       | The closing price is determined **the same way as the opening price**. (The slide's "equal to the opening price" is a typo.) |
| 17:35+      | **TAL (trading at last)** | Orders are only possible at the closing price.                                                                               |
| 17:40       | **Close**                 | No more orders are accepted.                                                                                                 |

**Auction rule:** the auction price is the price at which **all market orders are executed** and the remaining book is **in balance**. That means every buy order with limit ≥ price is executed, and every sell order with limit ≤ price is executed.

### 4.3 Order-book mechanics (ING example)

Starting book:

| bid vol |    bid |    ask | ask vol |
| ------: | -----: | -----: | ------: |
|     200 |  14.80 |  14.81 |     350 |
|     400 | 14.795 | 14.815 |     175 |
|     180 |  14.78 |  14.83 |     231 |

- **BBO line** (best bid/offer) = 14.80 / 14.81.
- **Bid-ask spread** = 14.81 − 14.80 = €0.01.
- **Depth** = the volumes further down the book.

**Case 1 — buy 50 @ 14.81**

- Trade 50 @ 14.81.
- Ask volume at 14.81 falls from 350 to **300**.

**Case 2 — buy 500 @ 14.81**

- Trade 350 @ 14.81.
- There are no more asks ≤ 14.81, so the **remaining 150 rests as the new best bid at 14.81**.
- New BBO = 14.81 (150) / 14.815 (175).

**Case 3 — buy 500 @ 14.82**

- Trade 350 @ 14.81, then **150 @ 14.815**.
- 25 remain on the ask at 14.815. New BBO = 14.80 / 14.815.
- ⚠️ The slide writes "150@14.82". The fill is at the **resting ask price 14.815**: your limit is a cap, not the execution price.

**Case 4 — buy 50 @ 14.80**

- The limit is below the best ask, so **no trade**.
- Bid volume at 14.80 rises from 200 to **250**.

### 4.4 Settlement

- **Trading members:** a member that gives access to non-members is a **broker** (e.g. Binck, DEGIRO). Otherwise it is a **dealer** (e.g. Flow Traders).
- **Anonymous:** you never know your counterparty, because everyone trades against the **central counterparty (CCP)**.

  ![Investors trade via brokers/dealers (trading members) on the exchange](../pictures/PrAssTr/PrAssTr_intro_trading-members.png)

- **CCP:** a trade creates open positions at the clearing members. The CCP steps in between and **guarantees settlement of the net positions**.
- **CSD (Central Securities Depository):** every clearing member is typically also a settlement member with an account at the CSD, where the securities are held.
- **Delivery vs payment (DVP):** the CCP instructs the CSD to move securities from seller to buyer and cash from buyer to seller **simultaneously**, and guarantees that this succeeds.
- **Settlement date:** $T+2$, two business days after the trade.

  ![Trade day: orders via trading members to the platform, open positions at clearing members and the CCP](../pictures/PrAssTr/PrAssTr_intro_settlement-trade-day.png)

  ![T+2: CCP instructs the CSD, delivery vs payment via settlement members and the central bank](../pictures/PrAssTr/PrAssTr_intro_settlement-T2.png)

- **Custody chain:** investor → broker → clearing member → settlement member → CSD. Each link is only a **claim** on the next one, and in international positions parts of the chain can sit in foreign jurisdictions.
- **Asset segregation:** client assets are kept separate from the institution's business risk.
- **Short selling:** because delivery happens only at $T+2$, you can sell securities you don't own, provided you borrow them before settlement.

---

## 5. Security of the financial system

### 5.1 Cleared derivatives

- **Historical motivation:**
  - **Tulip bubble:** bulbs were traded before they existed. The paper profits never materialised because counterparties defaulted.
  - **Lehman default:** the US government let Lehman fail, having earlier handled Bear Stearns "successfully" and assuming Lehman was of the same magnitude.
- **Key contrast:**
  - For **securities**, counterparty risk exists **only until settlement**. After that, the only issue is safekeeping.
  - For **derivatives**, the risk lasts **as long as the position is open** (possibly years), and the amount you are owed can be large compared with the initial investment.
- **Guarantee chain:** CCP (clearing house) → clearing members → brokers/dealers → clients. Every link needs its own risk management.

### 5.2 OTC derivatives

- **Bilateral risk:** you are directly exposed to the institution. If it defaults, you receive only what is left after the default is settled.
- **Close-out netting:** only your **net** position is at risk. Without it you might pay 100% on your shorts and receive only 50% on your longs.
- **Less transparency:** derivatives create exposure without immediate balance-sheet value. Regulators therefore push for oversight (see EMIR).

### 5.3 Asset segregation

- **Custodians / safekeeping entities:** these hold accounts at the CSD and do nothing else. Sometimes they open **sub-accounts in the client's name**, so the client's assets are identifiable if something defaults.
- **Client money (by law):** accounts labelled "client money" cannot be used for recourse by the firm's creditors. The Dutch implementation is the **WGE** (_Wet Giraal Effectenverkeer_).
- **Laws are local, assets are international:** Fortis successfully took recourse on Lehman's client-money accounts in the Netherlands, because the UK client-money law did not hold up under Dutch law.
- **Cash is not segregated.** It sits on a bank's balance sheet (only banks may hold it).
  - The **DGS** guarantees up to **€100,000 per retail individual**.
  - **Companies and institutions are not protected** and can lose (part of) their money in a default.
  - This is why institutions park large cash amounts in **short-term government bonds of reliable governments**, even at **negative rates**.

---

## 6. Actualities

### 6.1 The 2008 credit crisis

1. After the dotcom recovery (2000) there was a lot of money in the system. **Mortgage-backed securities** (packages of tradeable mortgages, which had existed since the '80s) were an attractive investment.
2. **Rating-based investment:** pension funds and insurers may only buy debt of certain ratings. The scale runs from AAA to about E/F.
   - Slide: investment grade = AAA to **BB-**.
   - Market convention (S&P/Fitch, B&M) **[beyond slides]**: investment grade = AAA to **BBB-**. BB+ and below is high yield ("junk").
   - Check which one the exam expects.

![Rating scales of the main agencies](../pictures/PrAssTr/PrAssTr_intro_rating-scales.png)

3. **CDO:** a pool of loans cut into senior (AAA), mezzanine (BBB) and equity tranches. Diversification in the pool means the senior tranche is "almost always" paid, so it gets investment grade. Institutions could now buy mortgage risk they couldn't access directly.

![Basic CDO structure: collateral pool cut into senior, mezzanine and equity tranches](../pictures/PrAssTr/PrAssTr_intro_cdo-structure.png)

4. **Running out of mortgages:** lending standards were softened (Alt-A, subprime), using low **teaser rates** and the plan to refinance once the normal rate kicked in.
5. **CDOs of CDOs:** tranches that didn't qualify as investment grade were re-bundled into a new CDO.
6. **CDS:** insurance against default. On a default event, you hand in the bond and receive the nominal value. The logic was _risky bond + CDS = investment grade_. The biggest seller was **AIG** (a "monoline"), which became too big to fail.

![Growth of CDS notional outstanding, 2001–2008](../pictures/PrAssTr/PrAssTr_intro_cds-growth.png)

7. **Collapse:**
   - Refinancing after the teaser period failed.
   - US borrowers could simply hand in the keys (foreclosure).
   - The worst mortgages had almost no collateral (a trailer).
   - Defaults turned out **highly correlated**, so the CDOs were far riskier than assumed.
   - The CDS exposure was concentrated in the monolines, and governments had to bail them out.

### 6.2 Brexit

- The UK was the **gateway** for non-European banks into licensed EU financial services.
- Finance is about **13% of UK GDP** (NL: about 7%).
- Open questions: where does the activity relocate, is concentration desirable, and will other countries leave the single-market concept?

### 6.3 Post-COVID inflation

- **Government subsidies:** more money without matching production.
- **Central-bank bond buying (QE):** effectively printing money.
- **Negative interest rates:** meant to push people to spend.
- **Ukraine war:** an energy (gas) shortage that raised prices.

### 6.4 Regulation

Triggers:

- **Madoff:** a regulated fund that passed due diligence but was a scam.
- **Bank rescues:** led to Basel III.
- **Out-of-sight positions:** regulators want insight into interconnections between institutions.
- **FTX:** client crypto assets were not actually held.

| Regulation          | Purpose                                                                              |
| ------------------- | ------------------------------------------------------------------------------------ |
| **AIFMD**           | Alternative funds. Response to Madoff: controls and task duplication across entities |
| **MiFID II**        | More transparency and duty of care (on top of MiFID I)                               |
| **EMIR**            | Reporting of derivative positions, including OTC; moves toward a clearing obligation |
| **PRIIPs**          | Client information for products with embedded derivatives                            |
| **CRD** (Basel III) | Capital requirements for banks                                                       |
| **Solvency**        | Capital requirements for insurers                                                    |
| **MiCAR**           | Regulation of crypto assets                                                          |

---

## Questions from the lecture

**Q1. What is welfare?**
**Answer:** There is no unique definition. The lecture uses "the extent to which scarcity can be reduced".
_Why:_ the more of what people need that can be made available, the less scarcity, and the higher the welfare.

**Q2. So, what do we have to do to reach welfare, and how?**
**Answer:** Come up with things: use the earth's (fixed) resources to produce goods and services.
_Why:_ resources are fixed, so more welfare can only come from producing more out of the same resources, i.e. becoming **more productive** over time.

**Q3. How can productivity be increased?**
**Answer:** With **tools** (hunters with weapons) and **specialisation of labour** (people are skilled differently: the small guy hunts in the narrow woods, the big guy builds houses).
_Why:_ tools raise the output per person, and specialisation lets everyone do what they're best at. That in turn creates the need to exchange, which is why the financial system exists.

**Q4. What is the accelerator of our current growth in productivity?**
**Answer:** **Connectivity and automation.**
_Why:_ automation removes repetitive work, and connectivity links specialists and markets worldwide.

**Q5. Is growth intrinsic?**
**Answer:** According to the lecture, yes, but it is growth in _productivity_, not necessarily in consumption.
_Why:_ people prefer tools to manual labour and automate repetitive work. They are never satisfied with the status quo and enjoy being busy (joblessness is not attractive even without starvation).

**Q6. What happens in the order book if we enter a buy order for 50@14.81, 500@14.81, 500@14.82 or 50@14.80?**
**Answer:** See the four worked cases in §4.3.
_Why:_ an incoming order executes against resting orders at **their** prices, as long as your limit allows. Anything left over rests in the book at your limit.

**Q7. What happens after a transaction at the exchange?**
**Answer:** Clearing and settlement.

1. The CCP steps in between the clearing members and guarantees the net positions.
2. At T+2, the CSD moves the securities and the cash simultaneously (delivery vs payment).

See §4.4.
_Why:_ this removes counterparty risk from anonymous trading and makes sure nobody delivers without being paid.

**Q8. Why is Brexit such a hot issue in finance?**
**Answer:**

- The UK was the licensed **gateway** to the EU for non-European banks.
- Finance is about **13% of UK GDP** (NL about 7%).
- It raises questions about where activity relocates, and whether others leave the single market.

See §6.2.
_Why:_ losing EU passporting forces banks to move licensed activities and staff to the continent.

---

## Key-formulas box

$$\text{Coupon} = c \cdot N \qquad \text{(e.g. } 0.02 \cdot 1000 = €20\text{/yr; final payment } N + c \cdot N = €1{,}020)$$

$$\text{Call payoff} = \max(S_T - K,\ 0) \qquad \text{Put payoff} = \max(K - S_T,\ 0)$$

$$\text{Turbo leverage} = \frac{S}{\text{turbo price}} = \frac{15}{2.5} = 6$$

$$1\ \text{bp} = 0.01\% \qquad 100\ \text{bp} = 1\%$$

$$\text{Bid-ask spread} = \text{best ask} - \text{best bid}$$

---

## Links to later lectures

- Bonds, coupons and credit spread → **bond pricing, YTM, duration** (the risk-free rate as the discount benchmark).
- "Passive investing is theoretically good" → **efficient markets and the NPV rule**.
- Credit spread and CDS → the **cost of capital depends on risk**.
- Bank balance-sheet risk and the DGS → **stability of banks and insurers**, ratings, CDO/CDS.

## Open questions

1. Investment grade: does the exam use the slide's BB- or the standard BBB-?
2. Why can a DB pension fund be called an insurer but a DC fund not? (Who bears longevity and investment risk?)
3. What changes for short sellers when the EU moves from $T+2$ to $T+1$? **[beyond slides]** The US moved in May 2024; the EU is scheduled for 11 October 2027.
4. Why is diversification in a CDO pool useless when defaults are correlated?
5. Why do institutions accept negative yields on short-term government bonds instead of holding bank deposits?
