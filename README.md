# Retirement & Required Income Calculator (India)

> [!CAUTION]
> **NOT FINANCIAL, LEGAL, TAX, OR INSURANCE ADVICE.** This is a personal, educational calculator built for illustration only. It uses simplified assumptions and generic reference rates that may be outdated or may not apply to your situation. It does **not** know your income, dependents, debts, goals, or risk tolerance. **Nothing here is a recommendation to buy, sell, or hold any financial product.** Do not make investment, insurance, or retirement decisions based solely on this tool — consult a licensed financial advisor, tax professional, or insurance professional for advice specific to you. The creator(s) and distributor(s) of this tool accept no liability for outcomes from its use. All calculations run locally in your browser — no data is collected, stored, or transmitted anywhere.

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

## How the numbers are calculated

- **Future expense** = current expense × (1 + inflation) ^ years to retirement (or the weighted category version, in Custom inflation mode)
- **Corpus needed** = present value of your inflation-adjusted monthly expenses over your retirement years, discounted at the "real" post-retirement return (post-retirement return adjusted for inflation)
- **Required saving (fixed)** = flat monthly amount, growing at the pre-retirement return, that closes the gap between your current savings' future value and the required corpus
- **Required saving (step-up)** = starting monthly amount that, increasing every year by your chosen step-up %, closes the same gap
- **Required salary today** = current expenses ÷ (1 − savings rate)
- **Ranges (Conservative / Expected / Optimistic)** — the required-saving and blended-portfolio figures vary the assumed return ±3 percentage points around your chosen "expected" value, since actual market returns are never a single fixed number.

## About the savings options compared

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

## About the safety-net check

- **Emergency fund target** = your chosen number of months (default 6) × current monthly expenses.
- **Life cover benchmark** = 15 × annual expenses — a simple rule of thumb used because this tool doesn't collect income or number of dependents. A proper **Human Life Value** calculation from an advisor will be more accurate.
- **Health cover benchmark** = a flat ₹10 lakh baseline. Metro cities and family floater plans often need more.

These are rough, generic checks — not a personalized insurance needs analysis.

## General disclaimer

This tool is built for personal and educational use. It is not financial, investment, tax, or insurance advice, and the people who built or shared it are not liable for decisions made using it. Assumptions are simplified (e.g. constant inflation/return rates, flat savings rate elsewhere in the model) and real markets, expenses, and personal circumstances vary. For decisions involving real money, please consult a licensed financial advisor and/or insurance professional.
