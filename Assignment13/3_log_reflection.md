# Log & Reflection — Assignment 3

## 1. Interpretation Auditor Table

| Claim | Colour | How You Checked | Accepted or Rejected |
| :--- | :---: | :--- | :--- |
| Sweetener D had the largest percentage increase at +19.41%, rising by 29.50 PKR/kg from 152.00 to 181.50 PKR/kg. | Green | Recomputed `(181.50 - 152.00) = 29.50` and `(29.50 / 152.00) * 100 = 19.41%` in `2_work.ipynb`. | Accepted |
| Pulse C recorded the smallest rise at +3.69%, while Oil B's mean exceeded its median by 1.83 PKR/kg. | Green | Recomputed Pulse C `((210.50 - 203.00) / 203.00) * 100 = 3.69%`, but Oil B `324.83 - 324.00 = 0.83 PKR/kg` (not 1.83). | Rejected (arithmetic error on Oil B difference) |
| Because the mean and median are nearly identical for all four items, prices likely increased steadily rather than spiking in a single week. | Amber | Checked against summary table; consistent with close mean/median values, though not directly proven without weekly rows. | Rejected for factual note (plausible explanation only) |
| Supply-chain disruptions and fuel inflation caused Oil B and Sweetener D to climb faster than Pulse C. | Red | Checked dataset columns (`date`, `item`, `city`, `price`, `unit`, `data_label`); no fuel or supply variables exist. | Rejected (unsupported causal claim) |
| These increases reflect broader national retail inflation across Pakistan in early 2026. | Red | Checked `data_label` (`ILLUSTRATIVE TEACHING DATA - NOT ACTUAL PBS OBSERVATIONS`) and city count (only `City 1` and `City 2`). | Rejected (refers to external data not in file) |

---

## 2. Confused Classmate Transcript Excerpt

> **Classmate (AI):** The mean uses every price in the dataset, so it is always the most accurate typical price. Why wouldn't you always use it?
>
> **Me:** Because one extreme value pulls the mean away from what most people actually pay. Suppose four shops sell an item for 100 PKR and one shop enters 600 PKR by mistake. The mean becomes 200 PKR—double what four out of five shoppers paid—while the median stays 100 PKR.
>
> **Classmate (AI):** Okay, the outlier moves the mean, but why is the median allowed to ignore that 600 PKR price? Isn't ignoring data worse?
>
> **Me:** It does not ignore it; it counts its position in the sorted list (`100, 100, 100, 100, 600`) and picks the middle entry. When data has spikes or typos, the middle position reflects a normal shop's price, whereas the mean blends the error into every unit.
>
> **Classmate (AI):** That makes sense—the mean shifts with the size of extreme values, while the median only depends on order, so the median better represents a typical price when outliers exist.

---

## 3. Reflection: Where My First Draft Said More Than the Data Allowed

In `1_attempt.md`, my final sentence (`[C] Higher transport costs caused Oil B and Sweetener D to rise faster than Pulse C`) went beyond what the data allows. `teaching_prices_clean.csv` only records `date`, `item`, `city`, `price`, `unit`, and `data_label`, so it contains no transport or wholesale cost variables to support a causal claim. In addition, the file covers only two unnamed cities (`City 1` and `City 2`) over 12 weeks and is explicitly labelled as illustrative teaching data, so the results cannot be generalized to actual market prices elsewhere.