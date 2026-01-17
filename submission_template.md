# AI Code Review Assignment (Python)

## Candidate
- Name: Fransi Ayele
- Approximate time spent: 75 minutes

---

# Task 1 — Average Order Value

## 1) Critical bugs

- Divides the sum of non-cancelled orders by the total number of orders, producing incorrect averages.
- Can raise ZeroDivisionError for empty input or when all orders are cancelled.

### Edge cases & risks

- Empty order list.
- All orders cancelled.
- Missing keys or non-numeric order amounts.

### Code quality / design issues

- Inconsistent logic between total calculation and divisor.
- Assumes well-formed input without validation.

## 2) Proposed Fixes / Improvements
### Summary of changes
- Count only non-cancelled orders.
- Guard against division by zero.
- Use safer dictionary access.

### Corrected code
See `correct_task1.py`

> Note: The original AI-generated code is preserved in `task1.py`.

### Testing Considerations
If i were to test this function, I would test mixed cancelled/ non-cancelled orders, empty input, all-cancelled cases, and malformed order entries to ensure correctness and stability.

## 3) Explanation Review & Rewrite
### AI-generated explanation (original)
- This function calculates average order value by summing the amounts of all non-cancelled orders and dividing by the number of orders. 
- It correctly excludes cancelled orders from the calculation.

### Issues in original explanation
- Incorrectly claims cancelled orders are excluded from the divisor.
- Ignores failure cases.

### Rewritten explanation
- Calculates the average value of non-cancelled orders by dividing their total amount by the count of such orders. 
- Returns 0 if no valid orders exist. 

## 4) Final Judgment
- Decision: Request Changes
- Justification: Produces incorrect results and can fail on valid input.
- Confidence & unknowns: High confidence; behavior depends on upstream data quality.

---

# Task 2 — Count Valid Emails

### 1) Code Review Findings
#### Critical bugs

- Treats any value containing "@" as a valid email.
- Raises TypeError for non-string inputs.

#### Edge cases & risks

- Inputs like "@", "abc@", or "@domain".
- Mixed-type lists containing None or numbers.

#### Code quality / design issues

- Misleading function behavior relative to its name.
- Overly simplistic validation logic.

### 2) Proposed Fixes / Improvements
#### Summary of changes

- Validate input type.
- Require exactly one "@" with non-empty local and domain parts.
- Safely ignore invalid entries.

#### Corrected code

See `correct_task2.py`

> Note: The original AI-generated code is preserved in `task2.py`.

### Testing Considerations

If I were to test this function, I would focus on valid emails, common invalid formats, mixed-type inputs, and empty lists.

### 3) Explanation Review & Rewrite
#### AI-generated explanation (original)

- This function counts the number of valid email addresses in the input list. 
- It safely ignores invalid entries and handles empty input correctly.

#### Issues in original explanation

- Does not reflect actual validation logic.
- Overstates safety and correctness.

#### Rewritten explanation

- Counts email strings that contain exactly one "@" with non-empty parts on both sides, ignoring invalid and non-string values.

### 4) Final Judgment

- Decision: Request Changes
- Justification: Does not truly validate emails and can crash on realistic input.
- Confidence & unknowns: High confidence; RFC-level validation intentionally excluded.

---

# Task 3 — Aggregate Valid Measurements

## 1) Code Review Findings
### Critical bugs
- Divides by total input length instead of count of valid values.
- Can raise ZeroDivisionError.
- Unsafe float conversion.

### Edge cases & risks
- Empty list.
- All values None.
- Non-numeric strings.

### Code quality / design issues
- Mismatch between filtered values and divisor.
- Assumes numeric-convertible inputs.

## 2) Proposed Fixes / Improvements
### Summary of changes
- Track only successfully converted numeric values.
- Skip invalid entries safely.
- Handle no-valid-data case.

### Corrected code
See `correct_task3.py`

> Note: The original AI-generated code is preserved in `task3.py`.

### Testing Considerations
- If I were to test this function, I would focus on numeric inputs, mixed types, invalid strings, all-None lists, and empty input.


## 3) Explanation Review & Rewrite
### AI-generated explanation (original)
> This function calculates the average of valid measurements by ignoring missing values (None) and averaging the remaining values. It safely handles mixed input types and ensures an accurate average

### Issues in original explanation
- Incorrect averaging logic.
- Overstates safety for mixed input types.

### Rewritten explanation
- Computes the average of values that can be safely converted to floats, ignoring None and invalid entries, and returns 0 if no valid measurements exist.

## 4) Final Judgment
- Decision: Request Changes
- Justification: Produces incorrect averages and may fail on realistic datasets.
- Confidence & unknowns: High confidence; behavior aligns with common data-processing expectations.
