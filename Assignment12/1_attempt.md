1. Duplicate row (Row 8 & 96)
Code: df[df.duplicated(keep=False)]
Decision: Exclude. Reason: Distorts counts.

2. Invalid type (Row 17, price "1,250")
Code: df.info()
Decision: Correct to float, flag. Reason: Needs numeric formatting, extreme outlier.

3. Mislabeled item (Row 40, "oil b")
Code: df['item'].value_counts()
Decision: Correct to "Staple A". Reason: Fills missing Staple A observation for 2026-02-05, price aligns.

4. Missing value (Row 5, NaN price)
Code: df.isnull().sum()
Decision: Flag. Reason: Prevent silent imputation.

5. Outlier/Placeholder (Row 30, price 9999.0)
Code: df['price'].max()
Decision: Exclude (NaN). Reason: Heavily skews statistics.