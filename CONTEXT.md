# FREEDOM Fraud Prevention

Fraud risk scoring for FREEDOM's e-commerce/payments transactions: judging the model already in production and challenging it with a new one, where the business outcome is profit, not classification accuracy.

## Language

### Data

**Transaction**:
One labelled row of the sample: a single purchase with its amount (`monto`), timestamp (`fecha`), 16 anonymized attributes (`a`–`p`), the Incumbent Score and the Fraud Label.
_Avoid_: Order, payment, event, record

**Amount**:
The value of a Transaction (`monto`), in a single currency shared across countries (assumed USD). The unit of all Profit calculations.
_Avoid_: Value, price, ticket

**Amount**:
The value of a Transaction (`monto`), in a single currency shared across countries (assumed USD). The unit of all Profit calculations.
_Avoid_: Value, price, ticket

**Fraud Label**:
The ground truth for a Transaction (`fraude`): 1 = confirmed fraud, 0 = legitimate.
_Avoid_: Target, chargeback, class

### Models

**Incumbent Model**:
The fraud model currently in production. We only see its output, never its internals.
_Avoid_: Current model, old model, baseline model

**Incumbent Score**:
The Incumbent Model's integer risk score (`score`, 0–100) for a Transaction. Higher means riskier.
_Avoid_: Prod score, probability

**Challenger Model**:
The new model trained in this project to replace the Incumbent Model.
_Avoid_: New model, candidate

**Challenger Iteration**:
One trained version of the Challenger Model. The first one is the starting point that later iterations are compared against.
_Avoid_: Baseline (the baseline is the Incumbent Model)

**Fraud Probability**:
The Challenger Model's calibrated probability (0–1) that a Transaction is fraud. Unlike the Incumbent Score, it can be read as a likelihood.
_Avoid_: Score (reserved for the Incumbent), risk

### Decision

**Cutoff**:
The score threshold at or above which a Transaction is Declined. Every other Transaction is Approved.
_Avoid_: Threshold, ponto de corte (in code/prose use Cutoff)

**Approved / Declined**:
The only two outcomes a Transaction can get under the Cutoff policy.
_Avoid_: Accepted/rejected, blocked

**Decline Rate**:
The share of Transactions Declined under a given Cutoff. It is the proxy for friction on legitimate customers that Profit alone ignores.
_Avoid_: Block rate, rejection rate

**Profit**:
10% of `monto` for each Approved legitimate Transaction, minus 100% of `monto` for each Approved fraudulent Transaction. Declined Transactions contribute 0.
_Avoid_: Revenue, savings, loss avoided
