---
tags:
  - cs
created: 2026-03-14
status: draft
type: concept
aliases:
  - ordinal data
---
---

>[!Definition]
>Ordinal data is a type of [[Qualitative Data|qualitative data]] that has a meaningful rank but the distance between these ranks is unknown or uninterpretable.

e.g. Customer Satisfaction: Poor < Fair < Good < Excellent 
	Severity of a disease: Mild, Moderate, Proliferative, Severe
	*Therefore, Order has meaning*
## Properties
1. Categories have a natural order.
2. Difference between ranks aren't uniform or are uninterpretable.

>[!NOTE] 
>In [[ML]], [[ordinal encoding]] is preferable to one-hot encoding when the order is meaningful.
>
## Intuition
Ordinal data has a natural order or rank of categories but there is no exact measure that can concretely distinguish where one rank starts and ends. 
e.g. The distance between "Mild" and "Moderate" might be smaller than "Proliferative" and "Severe". 
## Related Concepts
1. [[Qualitative Data]]