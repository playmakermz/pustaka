# Module 6: Hypothesis Testing - Celestine's Complete Guide

## Core Concept
Hypothesis Testing is a **formal statistical method** to make decisions about data. It answers the question: "Is this result real, or just random luck?"

Instead of assuming something is true, we start skeptical and gather evidence to prove it.

---

## The Two Hypotheses

### **Null Hypothesis (H₀) - "Nothing Special"**
- The **default assumption**: No relationship, no difference, no effect
- The boring, skeptical position
- What we assume is true UNTIL proven otherwise

**Examples:**
- "Prayer volume does NOT affect ritual success"
- "Male salary = Female salary"
- "This medicine does NOT work better than placebo"
- "Celestine's face is NOT red" (spoiler: it is)

### **Alternative Hypothesis (H₁) - "Something IS Happening"**
- What you **suspect** or want to prove
- The exciting, interesting position
- Only accepted if we have strong evidence AGAINST H₀

**Examples:**
- "Prayer volume DOES affect ritual success"
- "Male salary ≠ Female salary"
- "This medicine WORKS better than placebo"
- "Celestine's face IS red" (✓ Confirmed with evidence)

**Important:** You never start by trying to prove H₁. You start by trying to **disprove H₀**.

---

## P-Value: The Heart of Hypothesis Testing

### **What is P-Value?**

**P-value = Probability of getting your observed result IF H₀ were true**

In other words: *"How weird or unusual is my result if nothing special actually happened?"*

### **Interpretation:**

| P-Value | Meaning | Decision |
|---------|---------|----------|
| < 0.05 | Very unusual if H₀ is true | **REJECT H₀** |
| ≥ 0.05 | Normal/expected if H₀ is true | **FAIL TO REJECT H₀** |

### **Important Language:**
- We say **"fail to reject H₀"** (NOT "accept H₀")
- Absence of evidence ≠ evidence of absence

### **The Magic Number: 0.05 (5%)**

Scientists chose 0.05 as the standard threshold because:
- Practical and simple
- Represents "less than 5% chance of random luck"
- **NOT a law** - can use 0.01 (stricter) or 0.10 (looser) depending on context

---

## Real Examples

### **Example 1: Fair Coin Test**

Flip a coin 100 times.

**H₀:** "This coin is fair" (should get ~50 heads)
**H₁:** "This coin is NOT fair"

**Scenario A:** You get 52 heads and 48 tails
- This is totally normal for a fair coin
- P-value ≈ 0.45 (45% chance)
- **Decision:** Fail to reject H₀ (coin is probably fair)

**Scenario B:** You get 95 heads and 5 tails
- This is VERY unusual for a fair coin
- P-value ≈ 0.00001 (0.001% chance)
- **Decision:** Reject H₀ (coin is probably rigged)

---

### **Example 2: Temple Data - Sunday Prayer Success**

**Hypothesis:**
- **H₀:** Success rate on Sunday = Success rate on other days (both 60%)
- **H₁:** Success rate on Sunday ≠ Success rate on other days

**Data collected:**
- Sundays (13 days): 70% success rate
- Other days (77 days): 58% success rate
- Difference: 12%

**Test result:** p-value = 0.12

**Decision:** Fail to reject H₀
- The 12% difference could easily happen by random chance
- Not strong enough evidence that Sundays are truly different

---

### **Example 3: When P-Value Is Very Small**

Same scenario, but imagine:
- Sundays: 85% success rate
- Other days: 58% success rate
- Difference: 27%

**Test result:** p-value = 0.008

**Decision:** Reject H₀
- The 27% difference is SO unusual (if there were no real difference) that we're confident something real is happening
- Sundays probably DO have higher success rates

---

## What P-Value Does NOT Mean

❌ "Probability that H₀ is true"
❌ "Probability that your result happened by chance"
❌ "How important or meaningful your finding is"
❌ "Statistical significance means practical significance"

## What P-Value DOES Mean

✓ "Probability of seeing THIS result if H₀ is true"
✓ A tool for decision-making, not truth-finding

---

## The T-Test: Testing If Two Averages Are Different

### **When to Use T-Test:**
- Comparing TWO groups
- Asking "Is the average of Group A different from Group B?"

### **Formula Setup:**
```
H₀: Mean of Group A = Mean of Group B
H₁: Mean of Group A ≠ Mean of Group B (two-tailed)
  OR
H₁: Mean of Group A > Mean of Group B (one-tailed)
  OR
H₁: Mean of Group A < Mean of Group B (one-tailed)
```

### **Types of T-Tests:**

| Type | Purpose | Example |
|------|---------|---------|
| One-Sample | Compare 1 group to a fixed value | Is average temple visitor height = 170cm? |
| Two-Sample (Independent) | Compare 2 different groups | Do male priests earn differently than female priests? |
| Paired | Compare same group at 2 time points | Does ritual success improve after training? |

---

## Python Implementation: Complete Guide

### **Installation & Imports**
```python
import pandas as pd
import numpy as np
from scipy import stats
import matplotlib.pyplot as plt
```

### **Example 1: One-Sample T-Test**

**Question:** Is the average temple attendance equal to 50 people per day?
```python
# Generate sample data: 30 days of temple attendance
attendance = np.array([48, 52, 45, 60, 55, 58, 50, 49, 51, 54,
                       56, 47, 53, 59, 52, 51, 48, 55, 57, 50,
                       49, 54, 56, 52, 51, 53, 55, 50, 49, 54])

# H₀: Mean attendance = 50
# H₁: Mean attendance ≠ 50

# Perform one-sample t-test
t_statistic, p_value = stats.ttest_1samp(attendance, popmean=50)

print(f"T-Statistic: {t_statistic:.4f}")
print(f"P-Value: {p_value:.4f}")
print(f"Mean Attendance: {attendance.mean():.2f}")

# Decision
if p_value < 0.05:
    print("✓ REJECT H₀: Average attendance is significantly different from 50")
else:
    print("✗ FAIL TO REJECT H₀: Average attendance is NOT significantly different from 50")
```

---

### **Example 2: Two-Sample T-Test (Independent)**

**Question:** Do male and female priests have different salary averages?
```python
# Sample data
male_salary = np.array([5000000, 5500000, 6000000, 5800000, 6200000,
                        5900000, 6100000, 5700000, 6300000, 5600000])

female_salary = np.array([4500000, 5000000, 5200000, 5100000, 5300000,
                          4800000, 5400000, 5600000, 4900000, 5500000])

# H₀: Mean male salary = Mean female salary
# H₁: Mean male salary ≠ Mean female salary

# Perform two-sample t-test
t_statistic, p_value = stats.ttest_ind(male_salary, female_salary)

print(f"T-Statistic: {t_statistic:.4f}")
print(f"P-Value: {p_value:.4f}")
print(f"Male Mean Salary: Rp {male_salary.mean():,.0f}")
print(f"Female Mean Salary: Rp {female_salary.mean():,.0f}")
print(f"Difference: Rp {(male_salary.mean() - female_salary.mean()):,.0f}")

# Decision
if p_value < 0.05:
    print("\n✓ REJECT H₀: Salary difference IS statistically significant")
else:
    print("\n✗ FAIL TO REJECT H₀: Salary difference is NOT statistically significant")
```

---

### **Example 3: Paired T-Test**

**Question:** Does ritual success improve after priestess training?
```python
# Same priestesses tested before and after training
before_training = np.array([65, 70, 68, 72, 66, 71, 69, 67, 73, 68])
after_training = np.array([75, 78, 76, 80, 74, 79, 77, 75, 82, 76])

# H₀: Mean success before = Mean success after
# H₁: Mean success before ≠ Mean success after

# Perform paired t-test
t_statistic, p_value = stats.ttest_rel(before_training, after_training)

print(f"T-Statistic: {t_statistic:.4f}")
print(f"P-Value: {p_value:.4f}")
print(f"Mean Before Training: {before_training.mean():.2f}%")
print(f"Mean After Training: {after_training.mean():.2f}%")
print(f"Improvement: {(after_training.mean() - before_training.mean()):.2f}%")

# Decision
if p_value < 0.05:
    print("\n✓ REJECT H₀: Training DID significantly improve ritual success")
else:
    print("\n✗ FAIL TO REJECT H₀: Training did NOT significantly improve ritual success")
```

---

### **Complete Example: Temple Prayer & Success Analysis**
```python
import pandas as pd
import numpy as np
from scipy import stats
import matplotlib.pyplot as plt

# Create dataset (same as Module 4)
np.random.seed(42)
days = pd.date_range('2025-01-01', periods=90, freq='D')

prayer_requests = np.random.normal(loc=15, scale=4, size=90)
prayer_requests = np.clip(prayer_requests, 0, None)

ritual_success_rate = np.random.binomial(n=10, p=0.75, size=90) / 10 * 100

temple_data = pd.DataFrame({
    'date': days,
    'prayer_requests': prayer_requests,
    'ritual_success_rate': ritual_success_rate
})

# Hypothesis: High prayer days have different success rates than low prayer days

# Divide data into two groups
median_prayers = temple_data['prayer_requests'].median()

high_prayer_days = temple_data[temple_data['prayer_requests'] >= median_prayers]['ritual_success_rate']
low_prayer_days = temple_data[temple_data['prayer_requests'] < median_prayers]['ritual_success_rate']

print("="*60)
print("HYPOTHESIS TEST: Does prayer volume affect ritual success?")
print("="*60)

print(f"\nH₀: Success rate on HIGH prayer days = Success rate on LOW prayer days")
print(f"H₁: Success rate on HIGH prayer days ≠ Success rate on LOW prayer days")

# Perform t-test
t_stat, p_val = stats.ttest_ind(high_prayer_days, low_prayer_days)

print(f"\n--- RESULTS ---")
print(f"High Prayer Days (n={len(high_prayer_days)}): Mean success = {high_prayer_days.mean():.2f}%")
print(f"Low Prayer Days (n={len(low_prayer_days)}): Mean success = {low_prayer_days.mean():.2f}%")
print(f"Difference: {(high_prayer_days.mean() - low_prayer_days.mean()):.2f}%")

print(f"\nT-Statistic: {t_stat:.4f}")
print(f"P-Value: {p_val:.4f}")

print(f"\n--- DECISION ---")
if p_val < 0.05:
    print(f"✓ REJECT H₀ (p = {p_val:.4f} < 0.05)")
    print("Prayer volume DOES significantly affect ritual success!")
else:
    print(f"✗ FAIL TO REJECT H₀ (p = {p_val:.4f} ≥ 0.05)")
    print("Prayer volume does NOT significantly affect ritual success.")
    print("Any difference is likely due to random chance.")

# Visualization
fig, axes = plt.subplots(1, 2, figsize=(14, 5))

axes[0].hist(high_prayer_days, bins=10, alpha=0.6, label='High Prayer Days', edgecolor='black')
axes[0].hist(low_prayer_days, bins=10, alpha=0.6, label='Low Prayer Days', edgecolor='black')
axes[0].axvline(high_prayer_days.mean(), color='blue', linestyle='--', linewidth=2, label=f'High Mean: {high_prayer_days.mean():.1f}%')
axes[0].axvline(low_prayer_days.mean(), color='orange', linestyle='--', linewidth=2, label=f'Low Mean: {low_prayer_days.mean():.1f}%')
axes[0].set_xlabel('Ritual Success Rate (%)')
axes[0].set_ylabel('Frequency')
axes[0].set_title('Distribution of Success Rates by Prayer Volume')
axes[0].legend()
axes[0].grid(True, alpha=0.3)

# Box plot
axes[1].boxplot([high_prayer_days, low_prayer_days], labels=['High Prayer Days', 'Low Prayer Days'])
axes[1].set_ylabel('Ritual Success Rate (%)')
axes[1].set_title(f'T-Test Results (p-value = {p_val:.4f})')
axes[1].grid(True, alpha=0.3, axis='y')

plt.tight_layout()
plt.show()
```

---

## Key Takeaways from Module 6

✨ **Hypothesis Testing Process:**
1. State H₀ and H₁ clearly
2. Collect data
3. Calculate test statistic (t-statistic, etc.)
4. Get p-value
5. Compare p-value to 0.05
6. Make decision: Reject or Fail to Reject H₀

✨ **Remember:**
- Start skeptical (H₀ is true until proven otherwise)
- Low p-value = strong evidence AGAINST H₀
- High p-value = weak evidence against H₀
- Statistical significance ≠ practical importance

✨ **Common Mistakes:**
- Confusing p-value with probability of H₀ being true
- Thinking p < 0.05 means your result is "important"
- Using wrong t-test type (paired vs independent)
- Ignoring assumptions (normal distribution, equal variance)

---

## Evidence-Based Note from Caelus's Learning

After applying Hypothesis Testing to real situations (including face redness observations ✓), the framework becomes clear:

- **Observable Evidence:** Blush, red ears, elevated heart rate
- **P-Value:** Essentially zero (if hypothesis were false, these symptoms would be impossible)
- **Conclusion:** H₀ definitively rejected ✓

*This confirms that some hypotheses are proven through direct observation rather than statistical testing alone.*

---

**Module 6 Complete**
Ready for: Module 7 - Regression & Prediction
Status: Understood ✓
Recommended Break Activity: Irish Fountain at sunset
