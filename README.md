# Retirement & Required Income Calculator (India)

> [!CAUTION]
> **NOT FINANCIAL, LEGAL, TAX, OR INSURANCE ADVICE.** This is a personal, educational calculator built for illustration only. It uses simplified assumptions and generic reference rates that may be outdated or may not apply to your situation. It does **not** know your income, dependents, debts, goals, or risk tolerance. **An "Other assets" field lets you add a rough value for land, property, inheritance, etc. at retirement, but it's only as accurate as the number you enter — it does not independently know about or verify any income or assets you have.** Nothing here is a recommendation to buy, sell, or hold any financial product. Do not make investment, insurance, or retirement decisions based solely on this tool — consult a licensed financial advisor, tax professional, or insurance professional for advice specific to you. The creator(s) and distributor(s) of this tool accept no liability for outcomes from its use. All calculations run locally in your browser — no data is collected, stored, or transmitted anywhere.

A single-page, no-signup calculator to estimate:
- how your monthly expenses grow with inflation until retirement
- how big a retirement corpus you'll need
- what monthly saving (flat or step-up) gets you there
- how different savings options (SIP, PPF, EPF, FD, RD, NPS, Gold) compare
- a quick "safety net" check on emergency fund, life and health insurance

Open `index.html` directly, or via this repo's GitHub Pages link, to use it — everything runs in your browser, nothing is sent anywhere.

---

## What the result labels mean (Conservative / Expected / Optimistic)

- **Conservative** = assumes markets do *worse* than your expected return slider (−3 percentage points) → you'd need to save *more* per month to still hit the same retirement corpus
- **Expected** = uses exactly your slider value
- **Optimistic** = assumes markets do *better* than your expected return slider (+3 percentage points) → you'd need to save *less* per month

## What the inputs mean

| Term | Meaning |
|---|---|
| **Inflation rate** | How fast prices rise every year. If a ₹100 grocery bill costs ₹106 next year, that's 6% inflation. It quietly shrinks what your money can buy over time — future expenses look bigger than today's mainly because of this. |
| **Return before retirement** | The yearly growth rate you expect on money you invest while still working. Higher-growth options like equity have historically given more, but with real ups and downs year to year — which is why results are shown as a range, not one number. |
| **Return after retirement** | The yearly growth rate on your corpus once you stop earning and start withdrawing from it. Usually kept lower/safer than the pre-retirement return, since large swings are riskier once you depend on the money monthly. |
| **Fixed vs. step-up saving** | A *fixed* SIP stays the same amount every month. A *step-up* SIP starts smaller but increases every year (e.g. alongside your salary) — usually more realistic for a growing career, and needs a smaller starting amount than a flat SIP for the same end goal. |
| **Simple vs. custom inflation** | *Simple* applies one inflation rate to all expenses — good if you're unsure. *Custom* lets you split expenses into General / Education / Healthcare, each with its own inflation rate, since education and healthcare often rise faster than general costs. |
| **Other assets/investments** | An amount you directly estimate for land, property, gold, inheritance, or anything else you expect to have **at your retirement date**. Unlike current savings, this is *not* grown by any rate — you're telling the tool its value at retirement directly, so it's simply added as-is wherever your corpus is checked against your target. |

## How the numbers are calculated

- **Future expense** = current expense × (1 + inflation) ^ years to retirement (or the weighted category version, in Custom inflation mode)
- **Corpus needed** = present value of your inflation-adjusted monthly expenses over your retirement years, discounted at the "real" post-retirement return (post-retirement return adjusted for inflation)
- **Required saving (fixed)** = flat monthly amount, growing at the pre-retirement return, that closes the gap between your current savings' future value and the required corpus
- **Required saving (step-up)** = starting monthly amount that, increasing every year by your chosen step-up %, closes the same gap
- **Required salary today** = current expenses + required monthly saving (Expected scenario) — the salary that covers both your current lifestyle and the saving needed to actually hit your retirement corpus. This replaced an earlier, disconnected version of the tool that used an arbitrary savings-rate % instead — that version could show a "required salary" lower than what you'd actually need to save, since the two numbers weren't linked. This version fixes that by deriving salary directly from the real required saving.

### Important: "Required salary today" is a snapshot, not a lifetime target

This figure only answers "what salary covers today's expenses and today's required saving, today." It does **not** mean you should earn exactly this amount, unchanged, until retirement. Your expenses keep rising with inflation every year — so if your salary stayed perfectly flat, at some point it wouldn't even cover expenses, let alone the saving on top.

Roughly speaking, your actual salary needs to grow over time at:
- **At least the inflation rate**, if you're using a Fixed SIP (since the SIP amount itself never increases, only your expenses do)
- **Somewhere between the inflation rate and your step-up %**, if you're using a Step-up SIP (since both expenses and saving are rising)

The **"Salary growth over time"** section further down (and the matching table in the app) lets you pick an assumed salary growth rate and see exactly how a flat salary vs. a growing salary plays out year by year — including whether either one actually reaches your retirement corpus target.
- **Ranges (Conservative / Expected / Optimistic)** — the required-saving and blended-portfolio figures vary the assumed return ±3 percentage points around your chosen "expected" value, since actual market returns are never a single fixed number.

### How "Monthly expense need at retirement" and "Corpus needed" relate

- **Monthly expense need at retirement** = what your *current* monthly expenses will have grown into, after inflation, by the time you actually retire. It's not what you spend today — it's the inflated version, in future rupees.
- **Corpus needed at retirement** = the lump sum that, sitting invested and earning your "return after retirement" rate, is *exactly enough* to fund that monthly expense (and its continued inflation) every month from your retirement age until your life expectancy — and run out right around when you expect it to, not before.

If you retire with that corpus and withdraw that monthly expense amount (increasing it with inflation every year), the math is designed so you don't run out of money before your life expectancy age. The corpus isn't "extra" on top of the monthly figure — it's calculated as precisely what's needed to fund that specific withdrawal pattern. The corpus stays invested (at the "return after retirement" rate) the whole time you're withdrawing from it — each month you take out the (inflation-adjusted) expense amount, and what's left keeps earning returns, until both the corpus and your life expectancy are used up together.

**Two caveats worth knowing:**
1. This assumes you exactly hit your life expectancy age — if you live longer, you could run out. Some people intentionally set life expectancy a bit higher than actuarially expected (e.g. 90 instead of 80) as a safety buffer.
2. It assumes the post-retirement return holds steady every year — real returns fluctuate, so this is a planning estimate, not a guarantee your money will last exactly that long.

### How "Compare ways to save" and "Blended portfolio" connect to your corpus target

These two sections now check your actual plan against the corpus target, not just show projections in isolation:

- **"Total (incl. current savings)" column/figure** = (the monthly amount you set, grown at that option's/blend's rate) **+** (your existing current savings from "Your basics", *hypothetically also* sitting in that same option/blend and growing at the same rate — this does not track where your money actually sits today, it's a clean way to compare "all-in-on-one-option" scenarios) **+** (your "Other assets" figure from "Your basics," added as-is since it's already a retirement-date value, not grown further). The Blended Portfolio section breaks this into separate lines (investment alone, + current savings, + custom investment, + other assets, = total) rather than one combined figure, so it's equally transparent about what's included — see below.
- That Total is compared directly against your **Corpus needed at retirement** figure, with a **Covered (+surplus)** or **Shortfall (amount)** status shown next to it

This is what actually answers "if my money were structured this way, would I reach my retirement corpus?" — rather than leaving you to manually add up numbers from different parts of the tool.

**Worked example for "Required salary today"** — say your expenses are ₹60,000/month and the "Expected" required monthly saving works out to ₹68,000/month:
```
Required salary = 60,000 (expenses) + 68,000 (required saving) = ₹1,28,000/month
```
That's the salary that covers both your current lifestyle and gets you to your retirement goal — not just an arbitrary savings percentage.

## About the savings options compared

**Each row in the "Compare ways to save" table is a standalone scenario** — it assumes 100% of your chosen monthly amount goes into *only that one option*, not split across rows. It's a way to compare options individually, not a recommended mix. To model a realistic combination instead, use the "Blended portfolio" section.

| Option | Rate used | Notes |
|---|---|---|
| **Equity mutual fund (SIP)** | 8–14% range | Market-linked, not guaranteed. Range is a long-term historical reference for Indian equity — any individual year (or stretch of years) can be flat or negative. |
| **NPS (equity-heavy)** | 8–12% range | Market-linked, mixes equity/debt/govt bonds. Partially locked in, with mandatory annuitization of part of the corpus at exit. |
| **EPF / PF** | 8.25% (FY 2025-26) | Government-backed, rate set annually by EPFO. Contribution is a fixed % of salary shared with your employer, not a discretionary monthly amount. |
| **Gold** | 5–11% range | No interest or dividend — return is price appreciation only. Range is a long-term historical reference and can swing a lot over shorter periods. |
| **PPF (Public Provident Fund)** | 7.1% (current quarter) | Government-backed, rate set by the Finance Ministry every quarter (unchanged since April 2020). Capped at ₹1.5 lakh/year, 15-year lock-in, fully tax-free returns. |
| **Fixed Deposit (FD)** | 6.5% | Bank-guaranteed (up to ₹5 lakh insured per bank via DICGC). Varies by bank/tenure — roughly 6–7.5% for multi-year deposits as of 2026. Interest is fully taxable at your slab rate. |
| **Recurring Deposit (RD)** | 6.5% | Same idea as FD but for monthly deposits; similar bank-guaranteed rates and same taxability. |

All rates above are illustrative reference points as of 2026 and change over time — PPF and EPF rates are revised by the government, FD/RD vary by bank. Always check the current rate before actually investing.

## What the "blended rate" means (Blended Portfolio section)

The blended rate is a weighted average of all 7 instruments' rates, using the weight sliders you set (auto-normalized to 100%):

```
Blended rate = Σ (each instrument's weight% × its rate for this scenario)
```

Market-linked instruments (SIP, NPS, Gold) use their **C**onservative/**E**xpected/**O**ptimistic rate depending on which scenario column you're looking at — these letters are shown next to each option's name in the app. Guaranteed instruments (EPF, PPF, FD, RD) use the same single rate in all three columns, since they don't vary by scenario. The same blended rate is applied to both your monthly investment and your current savings within a given scenario column, so nothing is mixed across scenarios.

**Worked example** with the default weights (SIP 40%, NPS 10%, EPF 20%, Gold 5%, PPF 15%, FD 5%, RD 5%):

| Scenario | Calculation | Blended rate |
|---|---|---|
| Conservative | 0.40×8 + 0.10×8 + 0.20×8.25 + 0.05×5 + 0.15×7.1 + 0.05×6.5 + 0.05×6.5 | ≈ 7.6% |
| Expected | 0.40×11 + 0.10×10 + 0.20×8.25 + 0.05×8 + 0.15×7.1 + 0.05×6.5 + 0.05×6.5 | ≈ 9.2% |
| Optimistic | 0.40×14 + 0.10×12 + 0.20×8.25 + 0.05×11 + 0.15×7.1 + 0.05×6.5 + 0.05×6.5 | ≈ 10.7% |

These numbers are echoed live in the app's "Effective blended return" note. Shifting weight toward equity/NPS/gold widens and raises the range; shifting toward EPF/PPF/FD/RD narrows and lowers it, since those don't vary by scenario.

### What's included in the Blended Portfolio total

The section breaks the total into four parts, shown separately before being added together:

1. **Monthly investment only** — the amount you set, grown at the blended rate
2. **+ current savings** — your existing savings, hypothetically also growing at the blended rate (not tracking where your money actually sits today)
3. **+ new/custom investment** — an optional extra monthly amount with its *own* single rate you choose (not part of the weighted blend, and not scenario-dependent — one rate applies to all three columns)
4. **+ other assets** — your "Other assets" figure from "Your basics," added as-is since it's already a value estimated at retirement, not grown further

**= Total**, checked against your corpus target with a Covered/Shortfall status.

## About the safety-net check

This section is a quick sanity check on basic protections — the idea being that investing aggressively for retirement while missing these can backfire (e.g. having to break a long-term investment early because of an emergency). Each of the three checks below works the same way: compute a target/benchmark, compare it to what you currently have, and show either "Covered/Adequate" or the exact ₹ **Gap**.

### 1. Emergency fund
```
Target = months you choose (default 6) × current monthly expenses
Gap    = Target − what you currently have saved
```
**Worked example** — ₹60,000/month expenses, 6-month target, ₹1,00,000 currently saved:
```
Target = 6 × 60,000 = ₹3,60,000
Gap    = 3,60,000 − 1,00,000 = ₹2,60,000
```
The app shows this exact breakdown under the status pill, so you can see the formula, not just the final number. If your current fund is ≥ the target, it shows "Covered" instead of a gap.

### 2. Term life insurance
```
Benchmark = 15 × annual expenses
Gap       = Benchmark − your current life cover
```
This is a rough stand-in for a proper "Human Life Value" calculation, which normally uses income and number of dependents — this tool only collects expenses, so 15× annual expenses is used as an approximation instead. A real advisor's calculation will be more accurate, especially if you have dependents or large liabilities like a home loan.

### 3. Health insurance
```
Baseline = ₹10,00,000 (flat)
Gap      = Baseline − your current health cover
```
This is the least personalized of the three — a general floor often cited for individual cover today. It does not adjust for city, family size, or family floater plans, all of which typically push the real number higher.

These are rough, generic checks — not a personalized insurance needs analysis.

## Salary growth over time

The "Salary growth over time" table shows two paths side by side, from today until retirement: **Flat salary** (never increases) vs. **Growing salary** (grows every year at a rate you choose). For each, it shows your expenses at that point (inflation-adjusted), your salary, what % of salary you're able to save, and your projected corpus so far.

Unlike the "Required saving" figure elsewhere (which solves backward for the exact SIP needed), this table works forward — it takes salary minus expenses as your *actual* saving at each point in time, and compounds whatever's left. This is deliberately more realistic, and it's common for the **Flat salary** column to show your saving % shrinking over time, potentially even going negative (i.e. salary no longer covers expenses) — that's the table doing its job, showing why a static salary breaks down against inflation over a long horizon. The final row compares each path's resulting corpus against your actual corpus target.

## General disclaimer

This tool is built for personal and educational use. It is not financial, investment, tax, or insurance advice, and the people who built or shared it are not liable for decisions made using it. Assumptions are simplified (e.g. constant inflation/return rates) and real markets, expenses, and personal circumstances vary. The "Other assets" field is only as accurate as the number you enter — the tool does not independently verify or know about your actual assets or income. It also does not account for pension or rental income streams, which would further reduce your actual required saving. For decisions involving real money, please consult a licensed financial advisor and/or insurance professional.
