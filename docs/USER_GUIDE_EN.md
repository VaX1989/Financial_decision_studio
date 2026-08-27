# FINANCIAL DECISION STUDIO
## Complete User Guide

**Documented version:** Financial Decision Studio 3.0.0  
**Engine:** 3.0.0  
**Schema:** 2.1.0  
**Build:** `FDS-DEFINITIVE-20260826`

---

## How to use this guide

Financial Decision Studio uses an English-language interface. This guide therefore keeps the product's exact UI labels—such as **Liquid Net Worth**, **Run simulation**, **Create scenario**, and **Rebase future plan from this snapshot**—and explains what they mean in practical financial terms.

If you simply want to get started, read **Part II — Start in 5 minutes** and **Part IV — Dashboard and KPIs**. If you are comparing alternatives, move to **Part V — Decisions**. If you need to understand probability, downside risk, assumption fragility, or the drivers of a result, use **Part VIII — Lab**. **Data**, **Audit**, and **Expert plan JSON** are primarily advanced-user tools.

> **Important —** Financial Decision Studio is a planning and scenario-analysis application. It is not a promise about the future, not tax-filing software, and not a substitute for professional financial, tax, legal, mortgage, or insurance advice.

---

# Part I — Introduction

## 1. What Financial Decision Studio is

Financial Decision Studio is a personal financial-planning application contained in a single self-contained HTML file. It builds a monthly projection of a household's finances and balance sheet, then lets you compare alternative decisions under explicit assumptions.

The model can represent, among other things:

- cash and liquid investments;
- income and expenses;
- renting, a primary home, and a mortgage;
- additional properties;
- other liabilities;
- financial goals;
- scheduled life events;
- configured insurance premiums and benefits;
- reserve, surplus-investment, and rebalancing policies;
- taxes through the available tax packs;
- alternative scenarios;
- parametric Monte Carlo simulation;
- robustness, sensitivity, and attribution analysis;
- **Actual vs plan** tracking;
- a double-entry accounting ledger that makes financial movements auditable.

Its purpose is not to produce one magical answer. It is designed to help answer questions such as:

- Can I genuinely afford this home without destroying my liquidity buffer?
- Should I direct a fixed monthly amount toward mortgage prepayment or investments?
- How sensitive is a Rent-vs-Buy decision to the mortgage rate, rent, expected return, or home appreciation?
- Is my wealth goal achievable only in the central case, or does it remain plausible under uncertainty?
- After one year, is reality ahead of or behind the plan—and how should I update the future without rewriting the past?

## 2. Product philosophy: decisions, not predictions

Financial Decision Studio separates three ideas that should not be confused.

**Plan** — your starting financial state, expected cash flows, assets, debts, housing, goals, and policies.

**Scenario** — a branch that changes one or more elements of the plan to represent an alternative decision: buy instead of rent, retire earlier, change LTV, raise savings, prepay a mortgage, and so on.

**Simulation** — the calculation of what those assumptions imply. The deterministic engine uses the assumptions as entered. Monte Carlo generates many possible paths around the stochastic assumptions.

A forecast is often read as “this is what will happen.” A sound planning model asks a different question: “if these assumptions and behaviors are reasonable, what consequences follow, where are the vulnerabilities, and what would have to change for the decision to reverse?” Financial Decision Studio belongs to the second category.

## 3. Local-first, offline, and single-file by design

The application is designed to work **local-first**. Financial calculations run in the browser, and the product does not require a backend or a network connection to operate. You can keep the HTML file on a computer or phone and open it directly.

This has two practical consequences:

1. your plan does not need to be sent to a product server for calculation;
2. browser persistence can vary, especially when the app is opened as a local `file://` document.

For that reason, do not treat browser storage as your only backup. Keep periodic copies in **Plan JSON** and/or **Portable HTML** form.

## 4. The essential financial model

Before entering data, understand six distinctions.

| Concept | Practical meaning |
|---|---|
| **Net Worth** | Assets minus liabilities. It includes assets that may not be immediately spendable, such as real estate. |
| **Accessible Wealth** | Cash plus liquid investments after estimated latent capital-gains tax where applicable. |
| **Liquid Net Worth** | Accessible wealth minus liabilities that still economically claim against your wealth. |
| **Income** | External economic resources entering the household, such as salary or pension income. |
| **Expense** | A consumed cost that reduces wealth, such as rent, interest, maintenance, or living expenses. |
| **Balance-sheet transfer** | A movement of value from one form to another that is not, by itself, a consumed expense. Buying an investment or repaying mortgage principal are examples. |

> **Example —** If you move €1,000 from cash into an ETF, cash falls and investments rise, but you have not consumed €1,000 of wealth. If you pay €1,000 of rent or interest, that amount is a consumed cost.

---

# Part II — Start in 5 minutes

## 5. The three first-run paths

When no previously saved plan is loaded, the application offers three starting routes.

### Quick Decision

**Quick Decision** opens **Decisions → Rent vs Buy** immediately. Use it when your question is narrow and you do not yet want to build a complete household model.

It is ideal for an initial controlled comparison. You can vary home price, rent, mortgage rate, LTV, home appreciation, and portfolio return. If the question becomes important enough to integrate into your full plan, use **Create Rent / Buy scenarios**.

### Explore example

**Explore example** keeps the preconfigured example plan. This is the easiest way to learn the interface without entering personal data.

A useful learning sequence is:

1. change one input at a time under **Fast assumptions**;
2. inspect the six dashboard KPIs;
3. open **Decisions** and compare branches;
4. inspect **Goals**;
5. run **Lab → Risk**;
6. return to the plan and observe how each assumption changes the outcome.

### Build my plan

**Build my plan** starts a five-step onboarding wizard:

1. **Household** — plan name, number of adults, birth year, and indicative retirement year;
2. **Current position** — starting cash, investments, housing status, home value and mortgage where relevant;
3. **Monthly cash flow** — household net income, essential living costs, and rent when applicable;
4. **Main goal** — wealth target, years to target, and goal importance;
5. **Assumptions review** — horizon, inflation, and expected global-equity return.

The wizard deliberately asks for only decision-critical information. You can add detailed assets, liabilities, properties, events, policies, and advanced assumptions afterward.

## 6. Recommended path for a new user

For most users, the best sequence is:

1. Open **Explore example** for a few minutes.
2. Use **Build my plan** to create a rough personal baseline.
3. Stay in **Simple** mode until the headline numbers make sense.
4. Switch to **Detailed** and improve income, expenses, investments, and housing.
5. Add one meaningful **Goal**.
6. Check **Liquidity Runway** before optimizing anything.
7. Create a decision branch in **Decisions**.
8. Run **Lab → Risk** only after the deterministic baseline is sensible.
9. Use **Sensitivity** or **Robustness** to see what assumptions matter.
10. Export a **Portable HTML** or **Plan JSON** backup.

This sequence is intentionally progressive. A complex model entered badly is less useful than a simple model entered carefully.

## 6.1 Finding your way around the interface

The five main areas are:

- **Plan** — baseline, KPIs, fast assumptions, detailed entities, and Actual vs plan;
- **Decisions** — scenarios and decision templates;
- **Goals** — deterministic goal status and funding diagnostics;
- **Optimize** — bounded deterministic solvers;
- **Lab** — Risk, Robustness, Sensitivity, Attribution, Ledger, Data, and Audit.

On desktop these appear in the left navigation. On narrow mobile screens they appear in the bottom navigation.

The header also provides:

- validation status;
- Undo and Redo when available;
- current save state;
- **Share**;
- **Export**;
- theme toggle;
- the **⋯** data/settings menu.

---

# Part III — Building your plan

## 7. Simple, Detailed, and Expert

Financial Decision Studio uses progressive disclosure so that the financial model can be rich without forcing every user to confront every field.

### Simple

**Simple** exposes the six KPIs, charts, and **Fast assumptions**. It is the correct mode for an initial baseline or quick adjustment.

Fast assumptions include controls such as:

- analysis horizon;
- starting cash;
- monthly income;
- essential living costs;
- housing strategy;
- rent or home price;
- mortgage rate and LTV when buying;
- expected equity return;
- inflation;
- minimum cash reserve;
- additional net cash flow.

Use Simple to answer “is the overall model directionally sensible?”

### Detailed

**Detailed** adds the normal entity editors, including:

- income and expenses;
- investment portfolio;
- housing and mortgage;
- **Actual vs plan**.

It is the default level for building a serious personal plan.

### Expert

**Expert** does not change the financial state simply by being selected. It tells you where the deeper model lives: **Lab → Data / Audit** and **Expert plan JSON**.

Use Expert only when you need features such as additional properties, other liabilities, life events, policies, the full correlation matrix, advanced goal fields, or configuration that is not exposed in the standard forms.

## 8. Household

The household model defines the people represented in the plan. Basic onboarding captures the principal adult information, while **Lab → Data → Household members** allows additional household entries.

Typical fields include:

- ID and name;
- role;
- birth year;
- retirement year.

The household model is not an actuarial family model. Birth and retirement dates help organize planning timelines and retirement scenario creation, but the current version does not model full longevity, survivor, dependency, long-term-care, or household demographic transitions automatically.

## 9. Starting Cash

Starting cash represents immediately available cash at the beginning of the projection.

Do not include the same money twice—for example once as cash and again as an investment holding.

Starting cash plays several roles:

- pays initial costs;
- protects the emergency reserve;
- funds mandatory obligations;
- provides the source for optional investments or prepayments when the reserve rule allows;
- affects **Liquidity Runway** and path feasibility.

A high Net Worth with very little cash may still produce an unsafe plan if obligations cannot be funded at the right time.

## 10. Accounts, Assets, and Positions

The model distinguishes three layers.

**Account** — where value is held. The supported account semantics in this release are cash and taxable-investment accounts.

**Asset** — the investment type and its economic assumptions: expected return, volatility, fee, return mode, distribution yield, and asset class.

**Position / Holding** — a specific holding of an asset in an account, with its own market value, cost basis, and target weight.

This distinction matters because two positions in the same asset may have different cost bases. The canonical plan preserves position identity rather than assuming that every unit of the same asset is one indistinguishable lot.

### 10.1 Asset editor fields

The normal asset editor exposes the fields needed to model a liquid investment holding. Depending on the entity, these include:

- name;
- asset class;
- account;
- opening market value;
- cost basis;
- target allocation;
- expected annual return;
- annual volatility;
- fee rate;
- return mode;
- distribution yield.

Expected return and volatility are assumptions, not historical facts and not promises.

### 10.2 Total return vs Price return + distributions

The engine supports two economically distinct return conventions.

**Total return** means the expected return already includes distributions. In this mode, explicit distribution yield must not be added again.

**Price return + distributions** treats price appreciation and distributions separately.

> **Attention —** Do not enter a total-return assumption and also add a distribution yield for the same asset. The validator is designed to prevent return double counting.

### 10.3 Cost basis

**Cost basis** is the tax basis associated with a position. It matters when the model estimates capital-gains tax on a taxable sale.

A €100,000 investment with €100,000 cost basis is very different, from a liquidation perspective, from a €100,000 investment with €40,000 cost basis.

The current model preserves cost basis at position level, but it is not a full transaction-by-transaction tax-lot engine.

## 11. Income

Income streams represent resources entering the household from outside the existing balance sheet.

Typical properties include:

- amount;
- frequency;
- start and end timing;
- growth;
- person association;
- tax mode: **net** or **gross**.

Supported frequencies include monthly, quarterly, annual, and one-time schedules where configured.

Use **net** when the amount is already after tax and you do not want the tax pack to calculate tax on it. Use **gross** only when the simplified tax model is appropriate for that stream.

> **Important —** Do not use income as a hidden balancing plug. If you want to compare “what if I earn €500 more per month?”, that is a legitimate external-resource scenario. If you want to reallocate existing cash, use investment, prepayment, or policy controls instead.

## 12. Expenses

Expense streams are consumed household costs. They can be essential or discretionary and can grow over time.

Examples include:

- food and utilities;
- transportation;
- recurring subscriptions;
- childcare;
- recurring health costs;
- other living expenses.

An expense is not the same thing as every cash outflow. Buying an investment and repaying debt principal also use cash, but they are balance-sheet transfers rather than consumed expenses.

## 13. Housing — renting

When **Housing strategy** is set to **Rent**, the model can represent:

- monthly rent;
- rent growth;
- deposit expressed in months of rent;
- initial transaction costs;
- other monthly housing cost;
- configured deposit loss;
- advanced lease-end timing when configured through expert data.

A security deposit is treated as an asset while recoverable. It is not automatically treated as an expense on payment. At settlement, the recovered portion returns to cash and any configured lost portion becomes an expense.

Do not confuse the focused **Rent vs Buy** decision model with the full household rent model. The former is a controlled decision tool; the latter is part of the canonical plan.

## 14. Housing — ownership and mortgage

When **Housing strategy** is **Own / buy**, the model can represent:

- home price or current home value;
- purchase costs;
- LTV for a new purchase;
- mortgage rate and term;
- current mortgage balance and remaining term for an existing home;
- maintenance rate;
- property tax assumption;
- annual insurance;
- home appreciation;
- sale cost rate;
- explicit sale/disposal tax assumption where relevant;
- optional extra principal payments.

### 14.1 New purchase vs already-owned home

The acquisition mode matters.

For a **new purchase**, LTV can determine the financing structure.

For an **existing home**, current mortgage balance and remaining term are the relevant debt state. Changing the historical LTV does not economically refinance an existing loan. This is why some Optimize tools display **New-purchase scenario required** for an already-owned home.

### 14.2 Principal and interest

A mortgage payment contains two economically different components:

- **interest** is a consumed financing expense;
- **principal** reduces cash and reduces the liability by the same amount.

Therefore principal repayment does not reduce Net Worth dollar-for-dollar. It converts liquid assets into home equity by extinguishing debt.

### 14.3 Extra principal

Extra mortgage principal is an optional allocation. It is subject to the reserve logic: the model should not consume protected emergency reserves for an optional prepayment unless the configured policy permits it.

## 15. Additional Properties

Additional properties are managed under **Lab → Data → Additional properties**.

They are intended for rental properties, second homes, or other modeled real-estate assets. Depending on configuration, fields may include:

- current or purchase value;
- appreciation;
- monthly rental income;
- operating costs;
- linked debt;
- sale month;
- sale transaction costs;
- explicit disposal-tax assumption.

When a property is sold, the engine treats sale proceeds, transaction costs, disposal tax, and linked-debt payoff as separate economic components. A debt linked to the property should be settled exactly once.

> **Attention —** Real-estate taxes, legal costs, transaction rules, and country-specific disposal taxation can be complex. Entering a simplified assumption does not make the model a legal or tax calculator.

## 16. Liabilities — other debt

Use **Lab → Data → Other liabilities** for loans and debt beyond the primary mortgage.

Typical fields include:

- principal;
- annual interest rate;
- term in months;
- payment timing;
- linkage to another modeled entity where supported.

Debt is economically important for both Net Worth and Liquid Net Worth. A liability does not disappear merely because the borrowed cash has already been spent.

Unsupported or invalid debt structures are better blocked than silently approximated.

## 17. Goals

Goals define what the plan is trying to accomplish.

The standard goal editor is designed around:

- name;
- metric type;
- priority;
- target value;
- target month;
- value basis;
- inflation linkage where available.

Advanced goal fields, including a separate **minimumValue**, may require Expert JSON rather than the standard Goal form.

Goal semantics are explained fully in Part VI.

## 18. Events — life events

**Lab → Data → Life events** supports scheduled, potentially multi-action events.

Events are useful for situations such as:

- a future cash inflow;
- a large one-time cost;
- an investment action;
- a debt prepayment;
- a combination of actions representing one life event.

The engine uses atomic/preflight semantics for mandatory event funding where applicable. It should not post part of a required event and then leave the financial state inconsistent because the rest cannot be funded.

Timing matters. Events can be associated with the model's monthly ordering and advanced start/end-of-month semantics where configured.

## 19. Insurance & protection

**Lab → Data → Insurance & protection** can represent configured insurance premiums and event-triggered benefits.

This is a financial cash-flow representation, not a policy-valuation engine. It does not automatically determine whether your coverage is sufficient, price insurance risk, model underwriting, or interpret policy wording.

Use it to include known premium and benefit mechanics in a plan—not as a replacement for insurance analysis.

## 20. Financial Policies

**Lab → Data → Financial policies** contains rules that alter how surplus liquidity is handled.

### Reserve

Defines the protected minimum cash buffer, usually expressed in months of essential outflow.

### Invest surplus

Determines whether eligible cash above the reserve is invested and what proportion is allocated.

### Rebalance

Controls periodic portfolio rebalancing, including frequency and tolerance/band assumptions.

The preferred logic is economically conservative: use incoming cash to fill underweights before selling taxable positions, and do not consume protected reserves for optional allocation.

## 21. Assumptions and tax packs

Open **Lab → Data → Assumptions & tax pack** to inspect the active tax pack and major assumptions.

### Generic / user-net inputs

The generic tax pack performs no automatic income-tax calculation. It is appropriate when you enter net cash flows directly or want tax handling to remain external to the model.

### Italy 2026 planning pack

The Italy 2026 pack is explicitly a **planning approximation**. It uses simplified national IRPEF brackets and generic financial-tax assumptions, plus simplified mortgage-interest-credit logic.

It does **not** fully model:

- regional surtaxes;
- municipal surtaxes;
- all deductions and tax credits;
- income-category-specific rules;
- every high-income interaction;
- instrument-specific taxation;
- preferential sovereign-debt tax rates;
- all mortgage eligibility conditions;
- future tax-law changes.

If the plan extends beyond the pack's effective period, the application warns that the configured hold-last assumption is being used.

## 22. Correlation matrix

**Edit asset correlation matrix** controls the correlation assumptions used by the stochastic engine.

Correlation values must be mathematically valid. The engine checks properties such as:

- matching dimensions;
- unique driver IDs;
- diagonal values of 1;
- symmetry;
- values between -1 and +1;
- positive-semidefinite validity.

A perfectly correlated singular matrix can be mathematically valid; the engine is designed to support valid PSD cases rather than requiring strict positive definiteness.

Stable stochastic drivers are identified semantically rather than by UI order. Reordering assets or adding an unused stochastic asset should not change the random world experienced by existing active drivers.

---

# Part IV — Dashboard and KPIs

## 23. Projected Net Worth

### What it means

**Projected Net Worth** is the final projected value of assets minus liabilities at the end of the analysis horizon.

It can include cash, investments, property, recoverable deposits, and other modeled assets, less mortgages and other debt.

### How it is used

It is a long-horizon balance-sheet measure and a useful common outcome for scenario comparison.

### How to interpret it

Higher is usually better **all else equal**, but all else is rarely equal. A plan with higher terminal wealth may involve more liquidity risk, leverage, volatility, or lifestyle sacrifice.

### Watch out for

Do not treat terminal Net Worth as a complete decision score. Always read it alongside liquidity, goal status, risk, and the assumptions needed to produce it.

## 24. Liquid Net Worth

### What it means

**Liquid Net Worth** is the model's debt-aware measure of immediately or reasonably accessible wealth.

Conceptually it starts from:

- cash;
- liquid investments after estimated latent tax where applicable;

and then subtracts outstanding liabilities that remain claims against your wealth.

### How to interpret it

It answers a different question from Net Worth: “how strong is my financial position if I focus on wealth that can support obligations without relying on the gross value of illiquid assets?”

### Watch out for

A household can have substantial Net Worth and weak Liquid Net Worth—for example when most wealth is tied up in a mortgaged home.

## 25. Primary Goal

### What it means

The **Primary Goal** KPI displays the funding ratio of the first goal returned by the plan, along with its priority and deterministic status.

### How to interpret it

A value around 100% means the modeled metric at the goal date is around the target. Above 100% indicates a modeled surplus relative to the target; below 100% indicates a shortfall.

### Watch out for

This is a deterministic ratio, not a Monte Carlo probability. A goal can look fully funded in the central projection but still have a meaningful failure probability under stochastic paths.

## 26. Liquidity Runway

### What it means

**Liquidity Runway** estimates how many months of essential outflow could be covered by accessible wealth under the model's current state.

### How to interpret it

Think of it as a resilience indicator. A longer runway generally means more ability to absorb shocks or timing mismatches.

### What it does NOT mean

It is not a guarantee that every future obligation can be funded. A large one-time payment can still create a path failure even when average monthly runway looks healthy.

### Risk signal

The dashboard visually treats short runway as a warning condition. Do not optimize terminal wealth while ignoring a fragile funding path.

## 27. Debt Free

### What it means

**Debt Free** shows the first projected month after the start when modeled total debt falls below the engine's near-zero threshold.

### How to interpret it

It gives a simple timing milestone for debt elimination.

### Watch out for

The absence of debt is not automatically an optimal objective. Cheap debt, liquidity needs, taxes, and investment opportunity cost can all matter.

## 28. Plan Status

The application derives an explicit plan status rather than using one ambiguous wealth number.

Typical states include:

- **Incomplete** — blocking validation prevents a valid simulation;
- **Off track** — deterministic failure or required-goal failure;
- **Needs attention** — a required target is marginal;
- **At risk** — the deterministic plan works but Monte Carlo goal success falls below the configured threshold;
- **On track** — required conditions are currently satisfied.

> **Important —** Risk status only reflects the most recent stochastic result currently associated with the plan. After a material plan change, rerun **Lab → Risk** before relying on Monte Carlo-based status.

## 29. Charts on the Plan page

### Wealth trajectory

Shows how wealth evolves through time. Use it to identify inflection points, drawdowns, debt payoff effects, retirement transitions, or the impact of large events.

### Balance-sheet composition

Shows the changing composition of assets and debt. Two plans with identical terminal Net Worth can have very different paths and balance-sheet structures.

Charts are exploratory aids. Always confirm a surprising visual result with the underlying KPIs or ledger.

---

# Part V — Decisions

## 30. Baseline and scenarios

The **Baseline** is the reference plan. Scenarios are branches that inherit from an ancestor and store changes as patches.

A scenario can therefore represent a decision without duplicating the entire household state.

The Scenario manager shows, for each branch:

- Net Worth;
- Liquid wealth;
- goal funding;
- minimum runway;
- feasibility status.

Selecting a scenario makes it active across the application.

> **Important —** A branch inherits from its parent. If the baseline changes later, a child scenario can change too unless a field is explicitly overridden by that scenario. **Branch** is therefore a more accurate mental model than a frozen clone.

## 31. Creating a scenario

Use **+ Scenario** to create a new alternative or **Branch** to create a child from an existing scenario.

A good scenario changes only the variables required to represent a decision. If you change salary, spending, home price, returns, and goal at the same time, you may no longer know what caused the difference.

Use clear names such as:

- `Baseline`;
- `Buy 80% LTV`;
- `Remain renter`;
- `Prepay €500`;
- `Retire 2038`.

## 32. The fair-comparison principle

A valid financial comparison should keep initial resources and external assumptions equal unless the decision itself changes them.

For example, comparing mortgage prepayment with investing is unfair if one branch receives an additional €500 per month from outside the household while the other merely reallocates existing cash.

Financial Decision Studio's decision templates are designed around resource conservation where appropriate.

## 33. Rent vs Buy

The focused **Rent vs Buy** tool is a controlled housing decision model. It exposes variables such as:

- Home price;
- Monthly rent;
- Mortgage rate;
- Loan-to-value;
- Home appreciation;
- Portfolio return.

It reports:

- **Rent + invest** terminal wealth;
- **Buy with mortgage** terminal wealth;
- **Mortgage − Rent** difference;
- mortgage payment.

Use **Open sensitivity** to inspect decision boundaries and **Create Rent / Buy scenarios** to convert the controlled comparison into branches of the canonical household model.

The focused model exists for controlled comparison and regression-quality consistency. It is not a second full financial-planning engine.

### Create Rent / Buy scenarios

This action creates plan scenarios corresponding to the compared housing strategies. Use the resulting branches to bring the decision back into the full household model, where liquidity, goals, debt, taxation, and other plan elements can matter.

## 34. Complete example — continue renting vs buy a home

Assume:

- home price: €250,000;
- rent: €900/month;
- mortgage rate: 3.0%;
- LTV: 80%;
- home appreciation: 2.0%;
- portfolio return: 6.0%;
- long horizon.

A sensible workflow is:

1. Open **Decisions → Rent vs Buy**.
2. Enter the six controlled assumptions.
3. Compare **Rent + invest** and **Buy with mortgage**.
4. Do not stop at the headline winner.
5. Open **Sensitivity** and inspect the mortgage-rate × rent heatmap.
6. Look for the mortgage-rate break-even.
7. Create Rent and Buy scenarios.
8. Compare their **Liquid Net Worth**, not only terminal Net Worth.
9. Run **Lab → Risk** on both scenarios.
10. Use **Robustness** to test whether the housing conclusion survives assumption error.

Suppose Buy is ahead by €40,000 in the central case, but the decision flips if the mortgage rate rises by 0.4 percentage points or home appreciation falls modestly. That is not a “strong Buy” result. It is a fragile central-case advantage.

Conversely, if Buy remains ahead across a broad range of plausible rents, rates, and returns, the financial case is more robust—although non-financial factors still matter.

## 35. Prepay vs Invest

The **Prepay vs Invest** template becomes relevant when the active scenario owns a home with a mortgage.

It compares:

- scheduled mortgage only;
- an extra principal allocation;
- investing the same cash allocation.

The key phrase is **the same cash allocation**. The investment branch does not receive new external income merely to make the comparison work.

The allocation is optional and follows the reserve rule. This makes the comparison economically more defensible.

## 36. Refinance

**Refinance** is an economic screen, not an automatic refinancing engine.

It shows items such as:

- current balance;
- remaining term;
- current rate and payment;
- an illustrative lower rate and payment;
- monthly payment difference.

The screen deliberately warns that eligibility, fees, timing, and actual refinancing availability must be modeled explicitly in a scenario before relying on the result.

## 37. Retirement

The **Retirement** template helps create a branch that ends selected earned income and introduces pension income.

A crucial design choice is that existing living expenses continue unless you explicitly change them. The tool does not silently assume that retirement spending will fall.

This is a scenario template, not a full actuarial retirement-income engine.

## 38. Big Purchase

**Big Purchase** helps compare a large one-time purchase through the canonical financial model.

The quick editor records the purchase as a one-time essential expense, making it visible to the ledger and liquidity engine.

For more complex life events involving several simultaneous actions, use Expert events under **Lab → Data**.


---

# Part VI — Goals

## 39. What a goal can measure

A goal defines a future condition that matters to you. The current product supports goal metrics such as wealth-oriented targets, with the configured metric evaluated at a specific target month.

A goal is not merely a label. It participates in deterministic status and, for required goals, in stochastic success calculations.

## 40. Hard, Target, and Aspirational

### Hard

A **Hard** goal is a minimum requirement. Missing it means the plan fails the requirement.

Use Hard only for genuinely non-negotiable constraints. Making every preference Hard can make a realistic plan appear artificially impossible.

### Target

A **Target** is the normal planning objective. It may contain both a desired target and, in the underlying model, a lower minimum threshold.

A Target can therefore be fully on track, marginal, or off track depending on the achieved value.

### Aspirational

An **Aspirational** goal is desirable but does not determine overall required-goal failure.

It is appropriate for stretch objectives: a larger inheritance target, a luxury purchase, or an upside wealth ambition that should not make the entire plan “fail.”

## 41. Target and minimum

The model distinguishes the desired **target** from an optional **minimum**.

Conceptually:

- below minimum → off track;
- between minimum and target → marginal;
- at or above target → on track.

The standard Goal editor emphasizes the target. A separate `minimumValue` is an advanced model field and may require **Expert plan JSON** to edit directly in this release.

This distinction is valuable because many real goals are not binary. “€500,000 desired, €400,000 acceptable” is more informative than pretending that €499,999 and €400,001 mean the same thing.

## 42. Target month

Goals are evaluated at a specific future month rather than only at the end of the plan.

A retirement capital target due in 15 years should not be considered successful because the plan reaches it in year 28. Timing is part of the goal.

When rebasing the plan after an Actual Snapshot, the application shifts future references so that calendar intent is preserved where possible.

## 43. Nominal at target vs Current purchasing power

### Nominal at target

The entered amount is interpreted as the number of future currency units required at the target date.

Example: €500,000 means €500,000 at that future date.

### Current purchasing power

When the corresponding value basis/inflation linkage is configured, the goal can instead represent today's purchasing power, requiring the nominal future target to grow with inflation.

Example: “I want the purchasing power of €500,000 today in 20 years” is a different target from “I want exactly €500,000 nominal in 20 years.”

Always check the value basis before comparing goals.

## 44. Reading goal status

A goal card shows a funding percentage and status. Interpret it in layers:

- **Funding ratio** — modeled metric divided by target;
- **On track** — deterministic result meets the target;
- **Marginal** — above the acceptable minimum but below target;
- **Off track** — below the required threshold.

Then ask a second question in **Lab → Risk**: what proportion of stochastic paths achieve the required goals?

A deterministic goal at 105% with low stochastic success is not a robustly funded goal. A deterministic goal at 95% may be close enough that a small, realistic policy change solves it.

---

# Part VII — Optimize

## 45. What Optimize actually does

**Optimize** contains transparent bounded deterministic solvers. It does not claim to use a global evolutionary optimizer, NSGA-II, Differential Evolution, or a validated stochastic optimizer.

Results are not silently applied. Where supported, you can create a scenario from a candidate and then test that scenario elsewhere.

## 46. Affordable home price

### What it searches for

The highest modeled **new-purchase** home price that preserves the current minimum liquidity-runway constraint.

### Method

A bounded deterministic price search.

### Constraints

The solver respects the modeled liquidity path and the configured minimum cash/runway requirement.

For an already-owned home, it can display **New-purchase scenario required**, because changing the historical purchase price is not a meaningful control variable for current debt.

### How to interpret it

Treat the output as a model-implied ceiling under the current assumptions—not as the amount a bank will lend you and not as a recommendation to spend up to the limit.

If the result is €320,000, a financially resilient choice may still be below €320,000 once you consider uncertainty, lifestyle preferences, job risk, and unmodeled costs.

## 47. LTV search

### What it searches for

The **Loan-to-value** level that gives the best terminal objective among tested feasible leverage choices for a new purchase.

### Method

A bounded deterministic grid search.

### Constraints

Candidate LTVs must satisfy the model's liquidity constraint. The objective is the configured terminal wealth measure, including terminal liquidation semantics when enabled.

### How to interpret it

The “best” LTV is best only for the modeled objective under the current assumptions. It is not necessarily the most comfortable, lowest-risk, or easiest-to-finance LTV.

The leverage frontier chart is often more useful than a single winner because it shows how terminal wealth and liquidity trade off across candidate LTVs.

## 48. Required external monthly capacity

### What it searches for

The additional **external net monthly cash flow** required for the selected deterministic goal to be reached.

### Method

A bounded deterministic root solve.

### Attention

This is deliberately labeled **external** capacity. It is not a reallocation of money already in the plan.

If the solver returns €350/month, the interpretation is approximately: “under these assumptions, the plan needs about €350/month of additional external net resources to reach the deterministic goal.”

Do not reinterpret that as “invest €350 that was already sitting in cash” unless you explicitly model that reallocation instead.

## 49. After Optimize

Optimization should be the start of validation, not the end.

For any candidate:

1. create the scenario;
2. inspect **Liquidity Runway**;
3. compare Net Worth and Liquid Net Worth;
4. run **Lab → Risk**;
5. use Sensitivity or Robustness where relevant;
6. ask whether the result still makes sense under less favorable assumptions.

The product explicitly warns that its solvers are deterministic and that selected candidates should be stress-tested before adoption.

---

# Part VIII — Lab

## 50. Risk / Monte Carlo

### 50.1 What Monte Carlo is

**Lab → Risk** runs a parametric Monte Carlo simulation using correlated asset shocks, configured property volatility, stable random seeds, and pathwise liquidity failure.

It asks: “given the model and stochastic assumptions, what distribution of outcomes is generated across many simulated paths?”

It does **not** ask: “what will the market actually do?”

### 50.2 Paths

**Paths** is the number of simulated futures.

The UI allows path counts from 500 upward. More paths reduce sampling noise but require more computation.

Practical use:

- ~500: quick iteration;
- ~2,000: normal analysis;
- ~5,000 or more: deeper validation when the device handles it comfortably.

Do not interpret tiny percentage differences as meaningful when path counts are modest.

### 50.3 Seed

The **Seed** controls reproducibility. With the same plan, same seed, and same stochastic assumptions, the model can reproduce the same random experiment.

This is especially important when comparing scenarios. The engine uses stable driver-keyed Common Random Numbers so that scenario A and scenario B experience the same exogenous stochastic world where appropriate.

Changing asset display order should not give one scenario “luckier markets” than another.

### 50.4 Median terminal

**Median terminal** is the 50th percentile of the unconditional terminal wealth distribution.

Half of simulated terminal outcomes lie below it and half above it.

It is not the same as the expected value and not a guarantee.

### 50.5 P10 / P90 and percentiles

A percentile is a location in the simulated distribution.

- **P10** — 10% of paths finish at or below this level;
- **P50** — median;
- **P90** — 90% of paths finish at or below this level.

The P10–P90 range is useful for understanding dispersion without focusing only on extreme tails.

### 50.6 Goal success

**Goal success** is the fraction of simulated paths satisfying the required goal semantics.

The UI also reports a **95% Wilson confidence interval**. This interval reflects statistical uncertainty from a finite number of simulated paths. It does not represent all real-world model uncertainty.

Aspirational goals do not incorrectly turn the whole plan into a required-goal failure.

### 50.7 Liquidity failure

**Liquidity failure** is the fraction of simulated paths in which a mandatory obligation cannot be funded under the model's funding rules.

This is often more decision-relevant than terminal wealth. A path that becomes insolvent in year 8 should not be treated as successful merely because a hypothetical year-30 asset value would have been high.

### 50.8 P5 minimum liquidity

This metric summarizes a lower-tail measure of the minimum liquidity observed across paths.

Use it to ask whether the plan becomes dangerously thin in adverse paths even if the median outcome looks comfortable.

### 50.9 Max drawdown

The Risk screen reports median and upper-tail maximum drawdown statistics.

Drawdown measures decline from a prior peak. It helps describe path pain and volatility, not just final wealth.

### 50.10 Outcome distribution

The histogram shows the terminal outcome distribution for the active scenario.

If liquidity failures occur, failed paths remain part of the unconditional outcome accounting and failure is reported separately. The UI may also show a survivor-only median.

Never look only at the survivor number; doing so can hide the paths that failed.

### 50.11 Fan chart

The **Fan chart** displays wealth percentile bands over time, including P5–P95 ranges for the active stochastic result.

It is useful for seeing when uncertainty widens and when the plan becomes most exposed.

The fan chart is not a confidence band around one forecast. It is a visual summary of simulated path distributions under the model.

> **Important —** After materially changing a plan or scenario, rerun Monte Carlo. Do not assume an old Risk result still describes the new configuration.

## 51. Robustness

**Lab → Robustness** is currently a focused Rent-vs-Buy assumption-uncertainty analysis.

It generates 1,000 deterministic assumption states around the current controlled housing comparison. This is intentionally different from Monte Carlo path risk.

Monte Carlo asks: “what happens across stochastic market/property paths?”

Robustness asks: “does the decision survive plausible error in the assumptions themselves?”

### Indicators

The screen includes measures such as:

- **Buy win rate** — fraction of sampled assumption states in which Buy beats Rent;
- **Median Buy − Rent** — median decision advantage;
- **P5 / P95 decision delta** — spread of the decision difference;
- decision-critical assumptions ranked by correlation with the outcome;
- base-case winner;
- robust winner;
- ambiguity band;
- sample count.

The UI may display a **regret proxy**. Treat it exactly as labeled: a proxy within this controlled decision analysis, not a universal formal regret-optimization framework.

A useful interpretation:

- Buy win rate >70% → Buy is comparatively robust in the sampled region;
- Buy win rate <30% → Rent is comparatively robust;
- 30–70% → no dominant choice; the answer is assumption-sensitive.

These are interpretation aids, not laws of decision theory.

## 52. Sensitivity

**Lab → Sensitivity** provides a controlled Rent-vs-Buy sensitivity analysis.

The current heatmap varies:

- mortgage rate on one axis;
- monthly rent on the other.

Each cell represents:

**Buy with mortgage Net Worth − Rent + invest Net Worth**.

Positive cells favor Buy in the controlled model; negative cells favor Rent.

### Break-even

The **Mortgage-rate break-even** identifies rate values at which the modeled Rent-vs-Buy advantage crosses zero.

This is often more useful than the central result. If the current mortgage rate is 3.0% and the break-even is 3.1%, your conclusion is fragile. If the break-even is 5.5%, the result is less sensitive to modest rate estimation error.

A decision boundary tells you **what would have to change for the conclusion to reverse**.

## 53. Attribution

**Lab → Attribution** explains the terminal Net Worth difference between the active child scenario and baseline.

The tool performs a Shapley-style decomposition of scenario patch groups.

It shows:

- baseline outcome;
- active-scenario outcome;
- total delta;
- method;
- number of groups;
- residual;
- contribution of each patch group.

For a small enough number of groups the method is **Exact Shapley**; beyond the implemented threshold it becomes **Permutation-sampled**.

The contributions plus residual reconcile to the total scenario delta within the engine's tolerance.

Use Attribution to answer questions like:

- Was most of the improvement caused by lower housing cost or higher savings?
- Did the scenario work because of the intended decision, or because an unrelated assumption changed?
- Which scenario changes are actually material?

Attribution explains the model delta; it does not prove causality in the real world.

## 54. Ledger

### 54.1 Why the ledger exists

Financial models become misleading when every cash movement is treated as an expense or when assets and liabilities are updated inconsistently.

Financial Decision Studio therefore journals financial movements and checks balance-sheet reconciliation.

The Ledger screen reports:

- Assets;
- Liabilities;
- Net Worth;
- number of journal entries;
- reconciliation status.

### 54.2 Double-entry logic

Each journal entry contains balanced debit and credit postings. The objective is not to teach bookkeeping—it is to preserve economic identities.

The core balance-sheet identity is:

**Assets − Liabilities = Net Worth**.

### 54.3 Fundamental examples

**Investment contribution**  
Cash decreases; investments increase. No wealth is created simply by moving the money.

**Mortgage principal repayment**  
Cash decreases; mortgage liability decreases. Principal is not a consumed expense.

**Mortgage interest**  
Cash decreases; interest is a consumed expense.

**Property purchase**  
Cash/down payment and financing are exchanged for a property asset; acquisition costs are separate consumed costs.

**Investment gain**  
The investment asset value changes. It is a valuation change, not a cash contribution.

**Security deposit**  
Cash may decrease when paid, but a recoverable deposit asset is created. Loss becomes expense only when the deposit is actually lost.

This is why “cash outflow” and “expense” are not interchangeable concepts.

### 54.4 Journal explorer

The on-screen **Journal explorer** displays the latest 250 entries. **Export CSV** exports the complete audit trail.

The CSV exporter neutralizes common spreadsheet formula prefixes in user-controlled text to reduce formula-injection risk when the file is opened in spreadsheet software.

## 55. Data

**Lab → Data** is the advanced configuration center.

It includes:

- **Assumptions & tax pack**;
- **Expert plan JSON**;
- Household members;
- Financial policies;
- Other liabilities;
- Additional properties;
- Life events;
- Insurance & protection;
- Plan health.

This is where advanced users can inspect model structure without forcing all fields into the normal Plan interface.

### Plan health

Validation issues are classified as:

- **blocking** — the plan cannot be simulated safely;
- **warning** — the plan can run, but an assumption or limitation deserves attention;
- **informational** — useful model information.

Do not treat a green headline result as trustworthy if the plan contains unresolved validation concerns that materially affect interpretation.

## 56. Audit

**Lab → Audit** provides embedded diagnostics and runtime/reproducibility information.

### Embedded diagnostics

The application runs fast production-core invariants and reports pass/fail status. These checks cover important mathematical and accounting behaviors, but they are not a proof that every possible plan is correct.

### Reproducibility & capabilities

The Audit screen includes items such as:

- build ID;
- engine version;
- schema version;
- app version;
- plan fingerprint;
- storage mode;
- IndexedDB detection;
- localStorage availability;
- Web Worker availability;
- Web Crypto availability;
- File API availability;
- Share capability;
- Risk seed and path count;
- network dependency status.

The **Plan fingerprint** helps identify a specific plan configuration for reproducibility. Where Web Crypto is available, the application can use SHA-256; a deterministic non-cryptographic fallback may be used when cryptographic hashing is unavailable.

---

# Part IX — Actual vs Plan

## 57. Why use Actual vs plan

A financial plan becomes less useful if it is never compared with reality.

**Actual vs plan** lets you record what actually happened and compare it with the forecast for the same calendar month.

This turns the model from a one-time projection into a living planning process.

## 58. Actual Snapshot

Use **Record snapshot** to capture an observed checkpoint.

A component-level snapshot can include:

- month;
- cash;
- investments;
- property;
- debt;
- Net Worth.

The interface then shows:

- **Latest actual**;
- **Projected at that month**;
- **Variance**;
- observed composition.

### Interpreting variance

Variance is approximately:

**Actual Net Worth − Projected Net Worth**.

A positive variance means you are ahead of the old projection on that metric. A negative variance means you are behind.

Do not immediately conclude that a positive variance means better financial behavior. It may be caused by asset prices, delayed spending, an omitted liability, or a one-time event. Investigate the composition.

Similarly, a negative variance may be perfectly acceptable if it reflects a deliberate life decision that was not in the old plan.

## 59. Rebase Plan

**Rebase future plan from this snapshot** changes the projection opening state to an observed snapshot.

Conceptually, the selected snapshot becomes the new starting point for the future model. Cash, investments, property, and debt are replaced by the observed values, while future timing references are shifted so their calendar intent is preserved where possible.

The action is deliberately explicit and asks for confirmation.

A component-level snapshot is required; a legacy snapshot containing only aggregate Net Worth is not sufficient for a proper rebase.

## 60. Updating the future does not mean rewriting the past

A good rebase process has two responsibilities:

1. use reality as the new opening state for future planning;
2. preserve the historical forecast so that you can still evaluate how the original plan performed.

Financial Decision Studio stores forecast archives/checkpoints when rebasing. This protects the distinction between:

- “what we expected then”;
- “what actually happened”;
- “what we now expect going forward.”

Do not delete historical meaning merely because the new forecast is more current.

---

# Part X — Saving, privacy, and sharing

## 61. Persistence hierarchy

The application attempts persistence in this order:

1. **IndexedDB**;
2. **localStorage** fallback;
3. **memory / Session only** fallback.

The current status is shown in the interface with labels such as:

- **Saved · IndexedDB**;
- **Saved · localStorage**;
- **Unsaved**;
- **Session only**.

If persistence falls back to memory, the application deliberately avoids pretending that the plan is durably saved.

## 62. Why `file://` requires caution

When an HTML application is opened directly from local storage, browser policies around storage, origins, privacy modes, cleanup, or device behavior can vary.

A plan that persists on one browser/device may behave differently on another.

Therefore browser storage should be treated as convenience persistence—not the only durable backup contract.

> **Recommended practice —** Keep periodic copies of **Plan JSON** or **Portable HTML**, especially before major edits or browser/device changes.

## 63. Checkpoint

The **Checkpoint** button requests an explicit save of the current plan.

If durable browser storage is unavailable, the application warns that the session is memory-only and recommends exporting a backup.

A checkpoint is useful before a major scenario-editing session, but it does not replace an external backup file.

## 64. Plan JSON

**Plan JSON** exports the plan data in a structured format.

Advantages:

- compact;
- easy to archive;
- suitable for re-import;
- useful for advanced inspection and versioned plan storage.

Limitations:

- it is data, not the application itself;
- it is normally human-readable, so anyone with the file can inspect its contents;
- it should not be treated as encrypted unless specifically protected outside the app.

Plan imports are migrated and validated before activation. Unsupported future schemas and unsafe prototype-related keys are rejected rather than silently accepted.

## 65. Portable HTML

A **Portable HTML** combines the application shell and the plan payload into a self-contained shareable HTML file.

This is often the most convenient durable backup because the recipient can open the file and reproduce the deterministic plan without installing Financial Decision Studio separately.

A portable copy can include relevant plan, scenario, and reproducibility metadata.

Treat it as sensitive if the embedded plan contains personal financial information.

## 66. Encrypted Portable HTML

**Encrypted Portable HTML** protects the embedded plan payload with password-based authenticated encryption when Web Crypto is available.

The implementation uses modern browser cryptography, including:

- PBKDF2-HMAC-SHA-256 for password-based key derivation;
- a high iteration count;
- random salt;
- AES-256-GCM authenticated encryption;
- random IV/nonce.

### What happens when you open it

The application detects the encrypted embedded payload and asks for the password. With the correct password, the plan is decrypted in the browser and loaded into memory.

### If the password is wrong

Authenticated decryption fails and the plan is not loaded as valid plaintext.

### If you lose the password

There is no “forgot password” server because the product is local-first and does not store a recovery copy of your encryption key.

> **Critical —** If you lose the password to an encrypted portable file and do not have another backup, the plan may be unrecoverable. Keep the password in a secure password manager and maintain an independent backup policy.

## 67. Share and Web Share

**Share** uses browser/device sharing capabilities where available. If file sharing is not supported, the product falls back to a download/export workflow.

Whether the operating system shows a native share sheet depends on browser capabilities.

Before sharing, choose intentionally between:

- plain plan data;
- plain Portable HTML;
- encrypted Portable HTML.

Do not send a plain portable file through an untrusted channel merely because the app itself runs locally.

## 68. Privacy mode

When the application is operating in privacy/memory-only mode, the plan remains in the current session and is not presented as durably persisted.

This can be useful on a temporary or restricted environment, but closing the tab or browser may discard the session.

Export before leaving.

## 69. Recovery mode

The application includes a top-level recovery boundary to avoid turning a runtime/storage/migration problem into a blank white screen.

The recovery interface can offer actions such as:

- **Export recoverable plan**;
- **Open safe example**;
- **Clear local storage & reload**.

If recovery mode appears:

1. export recoverable data first if possible;
2. do not immediately clear storage unless you have a backup;
3. open the safe example only if you need to confirm that the application engine itself still works;
4. re-import a known-good Plan JSON or Portable HTML afterward.


---

# Part XI — How to make decisions with Financial Decision Studio

## 70. A practical 10-step method

### 1. Build a realistic baseline

Start with the world as it is, not the world you hope to reach.

Use current cash, investments, debt, housing, income, and recurring expenses. Avoid “solving” the baseline by entering optimistic returns or hypothetical future income before you have modeled the actual starting position.

A baseline is useful only if it is a credible reference state.

### 2. Check liquidity first

Before asking which option produces the highest terminal wealth, ask:

- Is **Liquid Net Worth** healthy?
- Is **Liquidity Runway** sufficient?
- Does the deterministic path encounter a funding failure?
- Does the plan rely on selling investments at an inconvenient time to meet mandatory obligations?

A plan that is theoretically wealthy at year 30 but cannot fund year 3 is not a viable plan.

### 3. Define the goals

State what the plan is trying to achieve.

Separate:

- non-negotiable minimums (**Hard**);
- normal objectives (**Target**);
- stretch ambitions (**Aspirational**).

Make the target date and value basis explicit.

### 4. Create alternatives

Use scenarios to represent actual choices—not arbitrary bundles of unrelated changes.

For example:

- Buy vs Rent;
- 60% LTV vs 80% LTV;
- retire in 2038 vs 2042;
- prepay €500/month vs invest €500/month.

Keep common household resources constant unless the decision itself changes them.

### 5. Compare the deterministic result

Use the deterministic engine to understand the mechanics before introducing randomness.

Compare:

- terminal Net Worth;
- Liquid Net Worth;
- goal status;
- minimum liquidity runway;
- debt path;
- timing of large costs or events.

If the deterministic model itself does not make economic sense, Monte Carlo will not rescue it.

### 6. Look for break-even points

A decision is more useful when you know what would reverse it.

Examples:

- mortgage-rate break-even;
- rent level at which Buy and Rent become equal;
- home price at which liquidity becomes unacceptable;
- additional monthly capacity required to fund a goal.

Break-even analysis converts “A wins” into “A wins as long as X remains below/above Y.”

### 7. Run Monte Carlo

Once the deterministic baseline is coherent, use **Lab → Risk**.

Focus on:

- liquidity failure;
- goal success;
- lower percentiles;
- drawdowns;
- distribution width;
- fan-chart evolution.

Do not focus only on the median.

### 8. Test robustness

For a Rent-vs-Buy decision, use **Robustness** to see whether the conclusion survives plausible assumption error.

A large base-case advantage with a 52% win rate across nearby assumptions is fragile. A smaller base-case advantage that survives most tested assumptions may be more decision-relevant.

### 9. Identify decisive assumptions

Use **Sensitivity** and **Attribution** to understand what drives the result.

Ask:

- Which input has the strongest influence?
- Is that input knowable with reasonable confidence?
- Is the result driven by the intended decision or by an accidental side change?

If the conclusion depends almost entirely on one speculative assumption, treat the decision as uncertain even if the central number looks precise.

### 10. Choose using financial and personal constraints

Financial optimization does not capture every reason people make decisions.

A home may provide stability or reduce flexibility. Paying off debt may provide psychological value. Holding more cash may be rational for a household with uncertain income even when expected terminal wealth falls.

> **Core principle —** The option with the highest terminal Net Worth is not automatically the best decision.

A sound choice combines model evidence with liquidity needs, risk tolerance, flexibility, personal preferences, and constraints the model does not fully represent.

---

# Part XII — Practical examples

## 71. Case 1 — Rent vs Buy

**Question:** Should a household keep renting or buy a €280,000 home?

Example assumptions:

- rent: €950/month;
- home price: €280,000;
- mortgage rate: 3.2%;
- LTV: 80%;
- home appreciation: 2%;
- investment return: 6%;
- purchase/sale/ownership costs entered realistically.

### Procedure

1. Start with **Quick Decision** or open **Decisions → Rent vs Buy**.
2. Enter the controlled inputs.
3. Compare **Rent + invest** and **Buy with mortgage**.
4. Check the monthly mortgage payment. A terminal advantage is not useful if the monthly cash-flow burden is unacceptable.
5. Open **Sensitivity**.
6. Inspect the mortgage-rate × rent heatmap and the mortgage-rate break-even.
7. Run **Robustness** and inspect Buy win rate and the critical assumptions.
8. Use **Create Rent / Buy scenarios**.
9. In the full scenarios, compare **Liquid Net Worth**, goal status, and minimum runway.
10. Run Monte Carlo on the serious candidates.

**Reasoning:**

Suppose the deterministic focused model shows Buy ahead by €55,000 after 30 years. That alone is not enough.

If the full Buy scenario leaves only 3 months of liquidity after closing costs and the Rent scenario maintains 12 months, the liquidity difference is material.

If the sensitivity boundary shows Buy loses when the mortgage rate rises from 3.2% to 3.5%, the central result is fragile.

If Buy still wins across a broad range and does not compromise the reserve, the financial case is stronger.

## 72. Case 2 — Prepay the mortgage vs invest

**Question:** A homeowner has €500/month available above the protected reserve. Should it go toward mortgage principal or investments?

### Procedure

1. Make sure the active plan uses **Own / buy** and the mortgage details are current.
2. Open **Decisions → Prepay vs Invest**.
3. Set or verify the extra-principal amount.
4. Compare:
   - scheduled mortgage only;
   - extra principal;
   - invest same cash allocation.
5. Check that the reserve remains protected.
6. Compare debt-free timing and terminal wealth.
7. Create explicit scenarios if you want deeper analysis.
8. Run **Risk** on the investment branch because its future return is uncertain.

**Reasoning:**

If the mortgage costs 2% and the investment portfolio is assumed to earn 7%, the deterministic investment branch may look superior. But that is not a guaranteed 5% spread.

Mortgage prepayment produces a much more certain reduction in financing cost. Investment returns are stochastic and may be poor exactly when liquidity matters.

The right interpretation is not “7% is greater than 2%, therefore invest.” It is “what additional expected wealth am I being compensated with for taking market, sequence, tax, and liquidity risk?”

## 73. Case 3 — Is a home truly affordable?

**Question:** The bank may approve a €400,000 purchase. Is it financially sustainable for the household?

### Procedure

1. Build a realistic household baseline.
2. Include purchase costs, maintenance, insurance, taxes/assumptions, and the mortgage—not just the monthly payment.
3. Set a sensible minimum reserve.
4. Open **Optimize → Affordable home price**.
5. Treat the result as a model ceiling, not a spending target.
6. Create a scenario below that ceiling.
7. Inspect **Liquidity Runway** through time, especially immediately after purchase.
8. Run Monte Carlo.
9. Use a more conservative home-appreciation or income assumption to see whether the plan remains feasible.

**Reasoning:**

A household can qualify for a mortgage and still have an unsafe plan. The key difference is that “bank affordability” focuses on credit underwriting, while household sustainability also includes reserves, goals, other debt, investment opportunity cost, and future uncertainty.

If the model says €400,000 is technically feasible but a €340,000 home preserves 12 months of liquidity and materially increases goal success, the lower price may be a better decision even though it is not the maximum possible purchase.

## 74. Case 4 — Probability of reaching a wealth target

**Question:** What is the probability of reaching a €1,000,000 wealth goal in 25 years?

### Procedure

1. Create the goal with the correct target month and value basis.
2. Check the deterministic funding ratio in **Goals**.
3. Confirm that expected returns and inflation are not overly optimistic.
4. Open **Lab → Risk**.
5. Start with around 2,000 paths.
6. Run the simulation.
7. Read **Goal success** and its 95% confidence interval.
8. Inspect **Liquidity failure** separately.
9. Inspect P10/P90 and the fan chart.
10. If success is too low, create a scenario with a realistic change—higher external savings, lower goal, longer horizon, or different spending—and rerun.

**Reasoning:**

Suppose the deterministic plan reaches €1.08 million but Monte Carlo goal success is only 63%. The correct conclusion is not “the model says I will reach €1.08 million.” It is that the central path meets the goal but the target is exposed to stochastic uncertainty under the current assumptions.

A higher monthly saving rate that raises goal success to 85% while keeping liquidity healthy may be a more robust plan.

## 75. Case 5 — Update the plan after one year

**Question:** A year has passed. Cash, investments, and debt differ from the original forecast. How should the plan be updated?

### Procedure

1. Open **Plan → Detailed → Actual vs plan**.
2. Use **Record snapshot** for the current month.
3. Enter observed cash, investments, property, and debt carefully.
4. Compare **Latest actual** with **Projected at that month**.
5. Review the variance and composition.
6. Decide whether the difference is temporary or represents a new reality.
7. If the new state should become the planning starting point, use **Rebase future plan from this snapshot**.
8. Confirm the action.
9. Review the new baseline and future timing.
10. Keep the archived forecast so you can still compare original expectations with reality.

**Reasoning:**

Suppose the original plan projected €80,000 Net Worth after one year, but actual Net Worth is €74,000 because markets fell while savings behavior was on target.

Rebasing does not mean the original plan was “wrong” in a useless sense. It means the current opening state is €74,000 rather than €80,000. The archived forecast remains valuable evidence about the difference between expectation and realized path.

---

# Part XIII — Common mistakes

## 76. Using overly optimistic returns

A 10% expected return makes almost every long-horizon plan look better.

That does not make the plan realistic.

Use assumptions you can defend, test lower-return cases, and use Monte Carlo instead of treating the expected-return path as destiny.

## 77. Confusing Net Worth with Liquid Net Worth

A €500,000 home with a large mortgage can create substantial gross assets while leaving little accessible wealth.

Always ask both:

- “How wealthy is the balance sheet?”
- “How much financial capacity is actually liquid after taxes and debt?”

## 78. Ignoring Liquidity Runway

Liquidity is a timing problem. A household can be solvent in the long run and still fail to fund a near-term obligation.

Do not optimize terminal wealth while accepting an unrealistic short-term liquidity path.

## 79. Treating Monte Carlo as a prediction

Monte Carlo does not discover the future probability distribution of markets. It explores the consequences of the distributional assumptions you gave the model.

If expected returns, volatility, correlations, inflation, taxes, or property assumptions are wrong, the output distribution can also be wrong.

## 80. Comparing scenarios with different starting resources

If one scenario starts with more money, a higher salary, or a different initial investment balance for no decision-related reason, the comparison is contaminated.

Use the same baseline and change only what the alternative actually changes.

## 81. Forgetting real-estate costs

Do not compare rent only with the mortgage payment.

Consider, where relevant:

- purchase costs;
- maintenance;
- property taxes;
- insurance;
- sale costs;
- financing costs;
- disposal tax assumptions;
- opportunity cost of equity/down payment;
- security-deposit treatment for renting.

## 82. Treating the tax pack like an official tax return

The tax packs are planning approximations.

The Italy 2026 pack intentionally omits or simplifies several tax components. Never use its result as the sole basis for a tax filing or a legal tax position.

## 83. Ignoring inflation

A future €1,000,000 is not automatically equivalent to €1,000,000 of purchasing power today.

Check whether a goal is nominal at target or expressed in current purchasing power.

Also remember that not every income or expense necessarily grows exactly with general inflation.

## 84. Looking only at the terminal result

Two plans can end with the same wealth and have very different experiences:

- one may suffer severe drawdowns;
- one may nearly exhaust liquidity;
- one may remain heavily leveraged for decades;
- one may require much higher monthly sacrifice.

Review the path, not just the endpoint.

## 85. Changing too many variables at once

If a scenario changes return, salary, spending, housing, and goal simultaneously, you cannot easily identify the driver.

Change one decision at a time when possible, then use **Attribution** and **Sensitivity**.

## 86. Using Additional net cash flow to make the plan “work”

**Additional net cash flow** is external wealth entering the household. It is not free money and not merely a bookkeeping transfer.

Use it only when you are deliberately asking “what if the household earns or receives this extra net cash?”

For reallocating existing resources, use the appropriate investment, mortgage, or policy controls.

## 87. Ignoring warnings and blocking issues

A blocking validation issue exists because the engine cannot safely interpret the plan as configured.

Do not bypass validation by assuming the output is “probably close enough.”

Warnings may indicate simplified tax behavior, horizon assumptions, unsupported model semantics, or another limitation that can materially affect interpretation.

---

# Part XIV — Real model limitations

## 88. Tax engine

The tax engine is a **planning model**, not tax-filing software.

The Italy 2026 tax pack contains simplified national income-tax, generic financial-tax, securities-stamp, and mortgage-interest-credit assumptions. It does not represent every legal rule, deduction, local surtax, instrument classification, property-tax rule, or eligibility condition.

Future-year law is not known. A hold-last assumption is a modeling convention, not a legal forecast.

## 89. Account types

The current simulated account semantics are intentionally constrained to supported types such as:

- cash;
- taxable investment.

The application does not pretend that every account label has distinct tax or withdrawal semantics.

Unsupported account structures are blocked rather than silently treated as equivalent.

## 90. Multi-currency

The model is effectively base-currency only. Accounts/assets in a different currency are not silently converted using invented FX assumptions.

If you need true multi-currency planning, this version does not provide a full FX engine.

## 91. Tax lots

Positions retain separate cost basis, which is materially better than collapsing all holdings into one number.

However, the product is not a full transaction-level tax-lot engine. It does not implement every jurisdiction-specific lot-selection method, wash-sale rule, carried loss, wrapper, or withdrawal-order regime.

## 92. Monte Carlo

The implemented stochastic mode is **parametric Monte Carlo**.

The product does not present the following as implemented:

- historical sequence simulation;
- block bootstrap;
- regime-switching simulation;
- historical resampling as a separate risk mode.

Parametric Monte Carlo is useful for controlled risk analysis but remains assumption-dependent.

## 93. Optimization

Optimize uses bounded deterministic searches/root solves/grid search.

It is not a stochastic optimizer, Pareto engine, global evolutionary optimizer, or formal Value-of-Information system.

A candidate found by Optimize should be validated separately under Risk and sensitivity analysis.

## 94. Retirement

Retirement is represented through scenario mechanics such as income ending and pension income beginning.

This version does not implement a full actuarial system for:

- longevity distributions;
- survivor benefits;
- long-term care;
- annuity pricing;
- detailed pension-wrapper taxation;
- dynamic spending rules across mortality states.

## 95. Insurance

Insurance can be represented through premiums and configured benefits, but the model does not assess policy adequacy, exclusions, underwriting, claims probabilities, or optimal coverage design.

## 96. Real estate

Property modeling includes meaningful cash-flow, financing, appreciation, transaction-cost, debt-linkage, and sale-tax assumptions.

It does not automatically know every jurisdiction-specific legal, tax, condominium, maintenance, transaction, vacancy, tenant, or financing rule.

Rental/property inputs remain assumptions you must validate.

## 97. Rent vs Buy Robustness and Sensitivity

These tools are deliberately focused on the controlled Rent-vs-Buy model. They are not generic full-household robust-optimization or universal sensitivity engines for every plan parameter.

## 98. Attribution

Attribution decomposes scenario patch effects in the model.

Exact Shapley is used only within the implemented group threshold; larger problems use permutation sampling.

Counterfactual contribution analysis is explanatory, not proof of real-world causation.

## 99. Market data and legislation

Financial Decision Studio does not automatically fetch live market prices, forecasts, tax laws, mortgage offers, inflation releases, or regulatory updates.

Your assumptions may become stale. Update them deliberately when the decision warrants it.

## 100. Browser and storage

Local browser behavior can differ by operating system, browser, privacy settings, and whether the application is opened via `file://`.

IndexedDB or localStorage availability does not guarantee indefinite retention.

Portable HTML and Plan JSON are the explicit durable backup mechanisms.

## 101. Numerical precision vs real-world precision

The engine can perform calculations to high numerical precision. That does not mean the economic inputs deserve the same precision.

A terminal result displayed to the euro may depend on assumptions that are uncertain by tens of thousands of euros.

Use numerical precision for consistency, not as a substitute for humility about forecasts.

---

# Glossary

| Term | Meaning |
|---|---|
| **Accessible Wealth** | Cash plus after-tax accessible value of liquid investments. |
| **Actual Snapshot** | Observed financial state recorded at a real calendar month. |
| **Actual vs plan** | Comparison between observed outcomes and the earlier projection. |
| **Aspirational goal** | Stretch objective that does not define required-plan failure. |
| **Asset** | Investment type with return, volatility, fee, and class assumptions. |
| **Attribution** | Decomposition of a scenario's modeled difference into contributing patch groups. |
| **Baseline** | Reference scenario from which alternatives are compared. |
| **Branch** | Scenario inheriting from another scenario while storing selected differences. |
| **Break-even** | Input value where the compared decision difference crosses zero. |
| **Common Random Numbers (CRN)** | Technique that gives compared scenarios the same exogenous random shocks for fairer comparison. |
| **Correlation** | Statistical relationship assumed between stochastic drivers. |
| **Cost basis** | Tax basis used to estimate gain on a taxable sale. |
| **Deterministic simulation** | Projection using the entered expected assumptions without random shocks. |
| **Drawdown** | Decline from a prior wealth peak. |
| **Expense** | Consumed cost that reduces wealth. |
| **Fan chart** | Time-series display of stochastic percentile bands. |
| **Funding waterfall** | Ordered process used to fund obligations from eligible resources. |
| **Goal success** | Fraction of Monte Carlo paths satisfying required goal semantics. |
| **Hard goal** | Non-negotiable goal requirement. |
| **Holding / Position** | Specific investment holding with account, asset, value, basis, and target weight. |
| **LTV** | Loan-to-value: mortgage amount relative to property value for a financed purchase. |
| **Liquidity failure** | A simulated path cannot fund a mandatory obligation under the model rules. |
| **Liquidity Runway** | Accessible wealth expressed in months of essential outflow. |
| **Liquid Net Worth** | Accessible wealth less remaining liabilities. |
| **Monte Carlo** | Repeated stochastic simulation under specified probability assumptions. |
| **Net Worth** | Assets minus liabilities. |
| **Nominal** | Expressed in future currency units without converting back to today's purchasing power. |
| **Percentile** | Position within a simulated outcome distribution. |
| **Plan fingerprint** | Identifier derived from plan configuration for reproducibility. |
| **Policy** | Financial rule such as reserve protection, surplus investing, or rebalancing. |
| **Portable HTML** | Self-contained copy of the application carrying an embedded plan. |
| **Rebase** | Start future planning from an observed Actual Snapshot while retaining historical forecast context. |
| **Rebalancing** | Adjusting portfolio holdings toward target allocation. |
| **Reserve** | Protected liquidity buffer. |
| **Robustness** | Analysis of whether a decision survives changes in uncertain assumptions. |
| **Scenario** | Alternative branch of the financial plan. |
| **Seed** | Value controlling reproducible pseudo-random simulation. |
| **Sensitivity** | Analysis of how the result changes as selected inputs vary. |
| **Target goal** | Normal planning objective, potentially with a lower acceptable minimum. |
| **Terminal liquidation** | Valuing the final state after modeled taxes/costs of liquidating assets rather than simply keeping them. |
| **Transfer** | Balance-sheet movement that is not, by itself, a consumed expense. |
| **Wilson confidence interval** | Statistical interval for a simulated binary proportion such as goal success. |

---

# FAQ

## Do I need to be online?

No. The definitive application is designed to work offline in a single self-contained HTML file.

## If I close the browser, will I lose everything?

Not necessarily. The application tries IndexedDB and then localStorage. But local-file persistence is browser-dependent, and either storage mechanism can be unavailable, restricted, or cleared. If the status says **Session only**, assume the plan can disappear when the session ends.

Maintain an external backup.

## What is the best backup?

For most users, keep both:

- a **Portable HTML** for convenient reopening;
- a **Plan JSON** for compact structured backup.

For sensitive plans that must be shared or stored in less trusted locations, use **Encrypted Portable HTML** and protect the password separately.

## Can I use Italy 2026 to prepare my tax return?

No. It is a planning approximation, not tax-filing software. Use official tax tools or a qualified professional for filing and legal tax positions.

## Why is my Net Worth high but Liquid Net Worth low?

Because much of your wealth may be illiquid or offset by debt. A valuable mortgaged home can increase Net Worth while leaving limited accessible financial capacity.

## Why is an investment contribution not shown as an expense?

Because buying an investment moves value from cash to an investment asset. Wealth is not consumed simply because cash leaves the checking account.

## Why is mortgage principal not an expense?

Because principal repayment reduces cash and reduces the liability. Interest is the consumed financing expense; principal is a balance-sheet transfer.

## Does Monte Carlo tell me the real probability that markets will do X?

No. It tells you the frequency of outcomes generated by the model under its stochastic assumptions. Real-world probability may differ because the assumptions themselves are uncertain.

## How many paths should I use?

Use enough to stabilize the decision without making iteration unnecessarily slow. Around 500 is useful for quick exploration, around 2,000 for normal analysis, and 5,000+ for deeper checks when your device handles it comfortably.

If a decision changes because success moves from 71.2% to 71.8%, you are probably demanding more precision than the model supports.

## Why doesn't Optimize give me an “optimal portfolio”?

Because this release implements bounded financial solvers such as affordable-home price, LTV search, and required external monthly capacity. It does not claim to be a general portfolio optimizer.

## Can I model a pension account with different taxation?

Not as a fully distinct tax-wrapper/account type in this version. Retirement cash flows can be modeled, but account-specific pension tax and withdrawal-order semantics are not implemented as a complete subsystem.

## Can I use multiple currencies?

Not with a true FX model. The product is base-currency oriented and blocks unsupported currency mismatches rather than silently converting them.

## Can I model multiple properties?

Yes. Use **Lab → Data → Additional properties**. Enter property-specific assumptions carefully, including sale and debt linkage where relevant.

## Can I model an event with several actions?

Yes, through advanced **Life events**. Multi-action events can represent combined inflow/outflow/investment/debt actions. Mandatory funding is handled with atomic/preflight logic where appropriate.

## Why does my scenario change when I edit the baseline?

Because scenarios are **branches**, not frozen copies. A child inherits fields from its parent unless the scenario explicitly overrides them.

If you need a truly fixed historical comparison, export/archive the relevant plan state rather than assuming live scenario inheritance is immutable.

## What happens if a mandatory payment cannot be funded?

The engine follows its funding waterfall through eligible cash and liquid resources. If the obligation cannot be funded, the path fails instead of silently creating an unconfigured loan or hiding an overdraft.

## Does an Aspirational goal reduce Goal success?

Aspirational goals do not define required-goal failure. Hard and Target semantics are what matter for required success.

## Can I see forecast archives after a Rebase?

The underlying plan preserves forecast archives so historical projection context is not rewritten. The normal Actual-vs-plan interface emphasizes current snapshots and variance; deeper archive structure can require Expert/Data inspection.

## Can the password of an Encrypted Portable HTML be recovered?

There is no product recovery service or server-side copy. If you lose the password and have no other backup, the encrypted plan may be unrecoverable.

## Why does Risk sometimes show a survivor-only median as well as the main median?

When some stochastic paths fail, the unconditional distribution still accounts for those paths. A survivor-only statistic answers a separate question: “among paths that survived, what did terminal wealth look like?” Never substitute the survivor-only figure for the overall failure-aware result.

## Should I use terminal liquidation?

Use it when the decision question requires a final after-tax/disposal view—for example comparing strategies as if assets were liquidated at the horizon. Keep mode is more appropriate when you intend to value assets as still held. The same interpretation should be used consistently across scenarios.

## Why can two holdings of the same asset remain separate?

Because they can have different cost bases or account context. The model can apply the same asset return shock while preserving position-level tax and liquidation information.

---

# Checklist — Before making an important decision

- [ ] The baseline reflects my actual current cash, investments, debts, and housing.
- [ ] Income is not inflated by hypothetical resources unless that is the scenario being tested.
- [ ] Essential expenses are realistic and include irregular costs where material.
- [ ] I checked whether values are nominal or inflation-linked.
- [ ] Investment return, volatility, fee, and correlation assumptions are defensible.
- [ ] I did not double-count distributions in a total-return asset.
- [ ] Investment cost basis is reasonable where taxable liquidation matters.
- [ ] Property purchase, maintenance, insurance, sale, and financing costs are represented.
- [ ] I checked both **Net Worth** and **Liquid Net Worth**.
- [ ] **Liquidity Runway** is acceptable, not merely terminal wealth.
- [ ] The decision scenarios start from comparable household resources.
- [ ] I changed only the variables required by the decision, where possible.
- [ ] Required goals have the correct priority and target date.
- [ ] I reviewed deterministic goal status before running Monte Carlo.
- [ ] I reran Monte Carlo after material plan changes.
- [ ] I looked at failure probability and lower percentiles, not only median wealth.
- [ ] I checked break-even or sensitivity where the decision has uncertain inputs.
- [ ] I tested robustness for an important Rent-vs-Buy conclusion.
- [ ] I used Attribution to verify that the scenario delta comes from the intended changes.
- [ ] I read all blocking issues and relevant warnings.
- [ ] I understand which tax assumptions are simplified.
- [ ] I considered important personal constraints that the model does not quantify.
- [ ] I saved/exported the plan before committing to major edits.

---

# Checklist — Data backup and security

- [ ] I know whether the status says **Saved · IndexedDB**, **Saved · localStorage**, **Unsaved**, or **Session only**.
- [ ] I do not treat local browser storage as my only backup.
- [ ] I periodically export a **Plan JSON**.
- [ ] I periodically export a **Portable HTML**.
- [ ] Before a major Rebase or restructuring, I create a fresh external backup.
- [ ] Sensitive Portable HTML files are stored or transmitted appropriately.
- [ ] If I use **Encrypted Portable HTML**, the password is stored in a secure password manager.
- [ ] I understand that a lost encryption password may make the file unrecoverable.
- [ ] I keep at least one backup separate from the device/browser that contains the working copy.
- [ ] Before clearing browser storage in Recovery mode, I export recoverable data if possible.
- [ ] After moving to another device/browser, I verify that the imported plan produces the expected deterministic headline result.
- [ ] For an important analysis, I record the build/version, plan fingerprint, seed, and path count shown in **Audit**.

---

# Conclusion

Financial Decision Studio is most useful when treated as a disciplined decision process rather than a calculator that outputs one final number.

Build a credible baseline. Protect liquidity. State goals clearly. Compare fair alternatives. Understand the deterministic mechanics. Find the break-even. Add stochastic risk only after the model is coherent. Test whether the conclusion survives assumption error. Identify what actually drives the result. Then combine the financial evidence with the personal constraints the model cannot decide for you.

The quality of the answer depends not only on the engine, but on the quality of the question and the honesty of the assumptions.

For important decisions, the most valuable output is often not “Scenario A ends €47,000 ahead.” It is:

**“Scenario A remains feasible, preserves the reserve, achieves the required goal across a satisfactory range of stochastic paths, and remains preferable until these specific assumptions cross these identifiable boundaries.”**

That is the level at which Financial Decision Studio should be used.
