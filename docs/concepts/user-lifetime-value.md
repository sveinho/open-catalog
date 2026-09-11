---
type: metric
title: User Lifetime Value (LTV)
status: verified
trust_tier: authoritative
owner: finance-analytics@acme.com
tags: [finance, marketing, revenue]
see_also: [docs/metrics/churn-rate.md, docs/engineering/revenue-schema.md]
---

# User Lifetime Value (LTV)

User Lifetime Value predicts the net profit attributed to the entire future relationship with a single customer segment.

## Mathematical Formula
We calculate LTV by multiplying the average revenue per user by the average customer lifespan:

$$LTV = ARPU \times \text{Customer Lifespan}$$

Where:
*   **ARPU**: Average Revenue Per User (Monthly).
*   **Customer Lifespan**: $1 / \text{Monthly Churn Rate}$.

## Core Constraints & Guardrails
*   **Segment Limitations**: This calculation should *never* be applied globally to combined B2B and B2C cohorts, as B2B contracts skew the lifespan averages.
*   **Data Source**: Query the `fact_mrr_user_daily` table in the data warehouse.

## Related Concepts
*   Monitor this alongside the [Churn Rate](churn-rate.md) to ensure lifespan metrics are accurate.
*   For technical implementation details, view the pipeline schema in the [Revenue Schema definition](../engineering/revenue-schema.md).
