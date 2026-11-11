### Verdicts
Line 1 (Drop duplicates): KEEP. Evidence: Rows went from 97 to 96.
Line 2 (Fix 'oil b'): KEEP. Evidence: Restored balance to 24 records per item.A
Line 3 (Price string to float): MODIFY. Evidence: AI's `.astype(float)` fails on existing NaN strings; changed to `pd.to_numeric(..., errors='coerce')`.
Line 4 (Handle 9999.0): KEEP. Evidence: Fixed major skew in dataset mean shown via `describe()`.

### Reflection
Differences: I planned to just flag 9999.0; AI converted it to NaN.
Supported: AI's approach is better as it prevents mathematical skewing during downstream aggregation.
Missed: I completely missed the 9999.0 outlier manually until the string column was cast to float.