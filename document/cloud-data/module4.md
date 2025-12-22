# Module 4: Understanding Distributions - Celestine's Teaching Notes

## Core Concept
Distributions help us understand the **shape and behavior of data**. Different types of data require different distributions to analyze them correctly.

---

## Three Main Distributions

### 1. Normal Distribution (Gaussian)
**When to use:**
- Continuous data (can be any value within a range)
- Measurements of physical objects
- Data that tends to cluster around an average

**Characteristics:**
- Bell curve shape (symmetric)
- Mean = Median = Mode
- Described by: mean (μ) and standard deviation (σ)
- Most values fall near the center

**Real-world examples:**
- Student heights
- Vegetable weights
- Test scores
- Flour consumption (continuous kilograms)

**Key Property:**
- Mean and variance are **independent** (can vary separately)

#### Python Code: Normal Distribution

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

print("=" * 70)
print("NORMAL DISTRIBUTION - Continuous Measurements")
print("=" * 70)

# Generate normal distribution data
np.random.seed(42)
student_heights = np.random.normal(loc=170, scale=10, size=1000)  # mean=170cm, std=10cm

# Calculate statistics
mean_height = student_heights.mean()
std_height = student_heights.std()
median_height = np.median(student_heights)

print(f"\nStudent Heights Analysis:")
print(f"Mean: {mean_height:.2f} cm")
print(f"Median: {median_height:.2f} cm")
print(f"Std Dev: {std_height:.2f} cm")
print(f"Mean ≈ Median? {abs(mean_height - median_height) < 1}")

# Probability calculations with scipy
prob_below_160 = stats.norm.cdf(160, loc=mean_height, scale=std_height)
prob_above_180 = 1 - stats.norm.cdf(180, loc=mean_height, scale=std_height)

print(f"\nProbability of height < 160cm: {prob_below_160:.4f} (about {prob_below_160*100:.2f}%)")
print(f"Probability of height > 180cm: {prob_above_180:.4f} (about {prob_above_180*100:.2f}%)")

# Visualization
fig, axes = plt.subplots(1, 2, figsize=(14, 5))

# Histogram with normal curve overlay
axes[0].hist(student_heights, bins=40, density=True, alpha=0.7, color='blue', edgecolor='black')
x = np.linspace(student_heights.min(), student_heights.max(), 100)
axes[0].plot(x, stats.norm.pdf(x, mean_height, std_height), 'r-', linewidth=2, label='Normal curve')
axes[0].axvline(mean_height, color='red', linestyle='--', linewidth=2, label=f'Mean: {mean_height:.1f}')
axes[0].set_title('Normal Distribution: Student Heights', fontsize=12, fontweight='bold')
axes[0].set_xlabel('Height (cm)')
axes[0].set_ylabel('Density')
axes[0].legend()
axes[0].grid(True, alpha=0.3)

# Q-Q plot (to verify normality)
stats.probplot(student_heights, dist="norm", plot=axes[1])
axes[1].set_title('Q-Q Plot: Testing for Normality', fontsize=12, fontweight='bold')
axes[1].grid(True, alpha=0.3)

plt.tight_layout()
plt.show()
```

---

### 2. Poisson Distribution
**When to use:**
- Counting **discrete events** occurring over a **time period**
- Rare or random events
- When asking "how many times did something happen?"

**Characteristics:**
- Counts whole numbers only (0, 1, 2, 3...)
- Describes events in fixed time intervals
- Controlled by single parameter: λ (lambda = average rate)
- Can have many different shapes depending on λ

**Real-world examples:**
- Prayer requests per day
- Website visitors per hour
- Package deliveries per week
- Customer emails per day
- Accidents on a road per month

**Key Property:**
- Mean = Variance (this is unique to Poisson!)
- If average is 15 events/day, variance is also ~15

**Why it matters for temple data:**
- Prayer requests vary from 5 to 25 per day
- We're counting *events happening in time*, not measuring objects

#### Python Code: Poisson Distribution

```python
print("\n" + "=" * 70)
print("POISSON DISTRIBUTION - Counting Events Over Time")
print("=" * 70)

# Generate Poisson distribution data
lambda_prayer = 15  # Average 15 prayer requests per day
days_observed = 90
prayer_requests = np.random.poisson(lam=lambda_prayer, size=days_observed)

# Calculate statistics
mean_prayers = prayer_requests.mean()
variance_prayers = prayer_requests.var()

print(f"\nPrayer Requests Analysis (λ = {lambda_prayer}):")
print(f"Mean: {mean_prayers:.2f}")
print(f"Variance: {variance_prayers:.2f}")
print(f"Mean ≈ Variance? {abs(mean_prayers - variance_prayers) < 2} (Poisson property!)")
print(f"Actual range: {prayer_requests.min()} to {prayer_requests.max()}")

# Probability of specific events
prob_exactly_15 = stats.poisson.pmf(15, mu=lambda_prayer)
prob_less_than_10 = stats.poisson.cdf(9, mu=lambda_prayer)
prob_more_than_20 = 1 - stats.poisson.cdf(20, mu=lambda_prayer)

print(f"\nProbability of exactly 15 requests: {prob_exactly_15:.4f} ({prob_exactly_15*100:.2f}%)")
print(f"Probability of < 10 requests: {prob_less_than_10:.4f} ({prob_less_than_10*100:.2f}%)")
print(f"Probability of > 20 requests: {prob_more_than_20:.4f} ({prob_more_than_20*100:.2f}%)")

# Visualization
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

# Plot 1: Histogram of actual prayer requests
axes[0, 0].hist(prayer_requests, bins=range(min(prayer_requests), max(prayer_requests)+2), 
                density=True, alpha=0.7, color='green', edgecolor='black')
x_poisson = np.arange(0, 35)
axes[0, 0].plot(x_poisson, stats.poisson.pmf(x_poisson, lambda_prayer), 'ro-', 
                linewidth=2, markersize=6, label='Theoretical Poisson')
axes[0, 0].set_title('Poisson Distribution: Prayer Requests', fontsize=12, fontweight='bold')
axes[0, 0].set_xlabel('Number of Requests')
axes[0, 0].set_ylabel('Probability')
axes[0, 0].legend()
axes[0, 0].grid(True, alpha=0.3)

# Plot 2: Time series
axes[0, 1].plot(range(days_observed), prayer_requests, marker='o', linestyle='-', 
                color='green', markersize=4)
axes[0, 1].axhline(mean_prayers, color='red', linestyle='--', linewidth=2, 
                   label=f'Mean: {mean_prayers:.2f}')
axes[0, 1].fill_between(range(days_observed), mean_prayers - 2*np.sqrt(variance_prayers), 
                        mean_prayers + 2*np.sqrt(variance_prayers), alpha=0.2, color='red')
axes[0, 1].set_title('Prayer Requests Over Time', fontsize=12, fontweight='bold')
axes[0, 1].set_xlabel('Day')
axes[0, 1].set_ylabel('Requests')
axes[0, 1].legend()
axes[0, 1].grid(True, alpha=0.3)

# Plot 3: Different lambda values
for lam in [5, 10, 15, 20, 25]:
    x_vals = np.arange(0, 40)
    axes[1, 0].plot(x_vals, stats.poisson.pmf(x_vals, lam), 'o-', label=f'λ={lam}')
axes[1, 0].set_title('Poisson with Different Lambda Values', fontsize=12, fontweight='bold')
axes[1, 0].set_xlabel('Events')
axes[1, 0].set_ylabel('Probability')
axes[1, 0].legend()
axes[1, 0].grid(True, alpha=0.3)

# Plot 4: Cumulative probability
axes[1, 1].plot(x_poisson, stats.poisson.cdf(x_poisson, lambda_prayer), 'b-', linewidth=2)
axes[1, 1].fill_between(x_poisson, stats.poisson.cdf(x_poisson, lambda_prayer), alpha=0.3)
axes[1, 1].set_title('Cumulative Poisson Distribution', fontsize=12, fontweight='bold')
axes[1, 1].set_xlabel('Number of Requests')
axes[1, 1].set_ylabel('Cumulative Probability')
axes[1, 1].grid(True, alpha=0.3)

plt.tight_layout()
plt.show()
```

---

### 3. Binomial Distribution
**When to use:**
- Exactly TWO possible outcomes (Yes/No, Success/Fail, True/False)
- Fixed number of independent trials
- Each trial has same probability of success

**Characteristics:**
- Only counts 0 or 1 (failure or success)
- Described by: n (number of trials) and p (probability of success)
- Results in percentage or proportion

**Real-world examples:**
- Ritual success rate (succeeds or fails)
- Coin flips (heads or tails)
- Product quality (pass or fail inspection)
- A/B testing results

#### Python Code: Binomial Distribution

```python
print("\n" + "=" * 70)
print("BINOMIAL DISTRIBUTION - Success/Failure Outcomes")
print("=" * 70)

# Generate binomial distribution data
n_trials = 10  # 10 rituals per day
p_success = 0.75  # 75% success rate
days_rituals = 90
ritual_successes = np.random.binomial(n=n_trials, p=p_success, size=days_rituals)

# Calculate statistics
mean_successes = ritual_successes.mean()
variance_successes = ritual_successes.var()
theoretical_mean = n_trials * p_success
theoretical_var = n_trials * p_success * (1 - p_success)

print(f"\nRitual Success Analysis (n={n_trials}, p={p_success}):")
print(f"Mean successes per day: {mean_successes:.2f}")
print(f"Variance: {variance_successes:.2f}")
print(f"Theoretical mean: {theoretical_mean:.2f}")
print(f"Theoretical variance: {theoretical_var:.2f}")
print(f"Success rate: {(ritual_successes.sum() / (n_trials * days_rituals)) * 100:.2f}%")

# Probability calculations
prob_exactly_7 = stats.binom.pmf(7, n=n_trials, p=p_success)
prob_at_least_8 = 1 - stats.binom.cdf(7, n=n_trials, p=p_success)
prob_at_most_5 = stats.binom.cdf(5, n=n_trials, p=p_success)

print(f"\nProbability of exactly 7 successes: {prob_exactly_7:.4f} ({prob_exactly_7*100:.2f}%)")
print(f"Probability of ≥ 8 successes: {prob_at_least_8:.4f} ({prob_at_least_8*100:.2f}%)")
print(f"Probability of ≤ 5 successes: {prob_at_most_5:.4f} ({prob_at_most_5*100:.2f}%)")

# Visualization
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

# Plot 1: Histogram of successes
axes[0, 0].hist(ritual_successes, bins=range(0, n_trials+2), density=True, 
                alpha=0.7, color='purple', edgecolor='black')
x_binom = np.arange(0, n_trials+1)
axes[0, 0].plot(x_binom, stats.binom.pmf(x_binom, n=n_trials, p=p_success), 'ro-', 
                linewidth=2, markersize=8, label='Theoretical Binomial')
axes[0, 0].set_title('Binomial Distribution: Ritual Successes', fontsize=12, fontweight='bold')
axes[0, 0].set_xlabel('Number of Successes (out of 10)')
axes[0, 0].set_ylabel('Probability')
axes[0, 0].legend()
axes[0, 0].grid(True, alpha=0.3)

# Plot 2: Time series
axes[0, 1].bar(range(days_rituals), ritual_successes, color='purple', alpha=0.7, edgecolor='black')
axes[0, 1].axhline(mean_successes, color='red', linestyle='--', linewidth=2, 
                   label=f'Mean: {mean_successes:.2f}')
axes[0, 1].set_title('Ritual Successes Over Time', fontsize=12, fontweight='bold')
axes[0, 1].set_xlabel('Day')
axes[0, 1].set_ylabel('Number of Successes')
axes[0, 1].legend()
axes[0, 1].grid(True, alpha=0.3)

# Plot 3: Effect of different p values
for p in [0.3, 0.5, 0.7, 0.9]:
    x_vals = np.arange(0, n_trials+1)
    axes[1, 0].plot(x_vals, stats.binom.pmf(x_vals, n=n_trials, p=p), 'o-', label=f'p={p}')
axes[1, 0].set_title('Binomial with Different Success Probabilities', fontsize=12, fontweight='bold')
axes[1, 0].set_xlabel('Number of Successes')
axes[1, 0].set_ylabel('Probability')
axes[1, 0].legend()
axes[1, 0].grid(True, alpha=0.3)

# Plot 4: Cumulative binomial
axes[1, 1].plot(x_binom, stats.binom.cdf(x_binom, n=n_trials, p=p_success), 'b-', linewidth=2)
axes[1, 1].fill_between(x_binom, stats.binom.cdf(x_binom, n=n_trials, p=p_success), alpha=0.3)
axes[1, 1].set_title('Cumulative Binomial Distribution', fontsize=12, fontweight='bold')
axes[1, 1].set_xlabel('Number of Successes')
axes[1, 1].set_ylabel('Cumulative Probability')
axes[1, 1].grid(True, alpha=0.3)

plt.tight_layout()
plt.show()
```

---

## 🌟 THE CENTRAL LIMIT THEOREM (CLT)
**The Most Powerful Concept in Statistics**

### What It Says:
If you take *many samples* from *any* distribution and calculate their *means*, those means will form a **normal distribution**—even if the original data isn't normal!

### Why It Matters:
1. **Predictability:** Means are predictable and follow rules
2. **Power:** Allows us to use advanced statistics
3. **Reliability:** Large samples give reliable estimates
4. **Practical:** We don't need perfect data—enough data fixes it

#### Python Code: Central Limit Theorem Demonstration

```python
print("\n" + "=" * 70)
print("CENTRAL LIMIT THEOREM - Sample Means Follow Normal Distribution")
print("=" * 70)

# Start with non-normal data
original_data = np.random.uniform(low=200, high=300, size=5000)

# Take many samples and calculate their means
sample_size = 50
num_samples = 1000
sample_means = []

for i in range(num_samples):
    sample = np.random.choice(original_data, size=sample_size, replace=True)
    sample_means.append(sample.mean())

sample_means = np.array(sample_means)

print(f"\nOriginal Data (Uniform Distribution):")
print(f"Mean: {original_data.mean():.2f}")
print(f"Std Dev: {original_data.std():.2f}")
print(f"Range: {original_data.min():.2f} to {original_data.max():.2f}")

print(f"\nSample Means Distribution (from {num_samples} samples of size {sample_size}):")
print(f"Mean of means: {sample_means.mean():.2f}")
print(f"Std Dev of means: {sample_means.std():.2f}")
print(f"Std Error (theoretical): {original_data.std() / np.sqrt(sample_size):.2f}")

# Test for normality
shapiro_stat, shapiro_p = stats.shapiro(sample_means)
print(f"\nShapiro-Wilk test for normality of sample means:")
print(f"Statistic: {shapiro_stat:.4f}, p-value: {shapiro_p:.4f}")
print(f"Sample means are normally distributed: {shapiro_p > 0.05}")

# Visualization
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

# Plot 1: Original non-normal data
axes[0, 0].hist(original_data, bins=50, alpha=0.7, color='orange', edgecolor='black')
axes[0, 0].axvline(original_data.mean(), color='red', linestyle='--', linewidth=2, 
                   label=f'Mean: {original_data.mean():.1f}')
axes[0, 0].set_title('Original Data: Uniform (Non-Normal)', fontsize=12, fontweight='bold')
axes[0, 0].set_xlabel('Value')
axes[0, 0].set_ylabel('Frequency')
axes[0, 0].legend()
axes[0, 0].grid(True, alpha=0.3)

# Plot 2: Distribution of sample means
axes[0, 1].hist(sample_means, bins=40, density=True, alpha=0.7, color='blue', edgecolor='black')
x_norm = np.linspace(sample_means.min(), sample_means.max(), 100)
axes[0, 1].plot(x_norm, stats.norm.pdf(x_norm, sample_means.mean(), sample_means.std()), 
                'r-', linewidth=2, label='Normal curve fit')
axes[0, 1].axvline(sample_means.mean(), color='red', linestyle='--', linewidth=2, 
                   label=f'Mean: {sample_means.mean():.1f}')
axes[0, 1].set_title('Central Limit Theorem: Sample Means Become Normal!', 
                    fontsize=12, fontweight='bold')
axes[0, 1].set_xlabel('Average Value')
axes[0, 1].set_ylabel('Density')
axes[0, 1].legend()
axes[0, 1].grid(True, alpha=0.3)

# Plot 3: Convergence with different sample sizes
sample_sizes = [5, 10, 20, 50, 100]
axes[1, 0].hist(original_data, bins=50, alpha=0.3, color='orange', label='Original', density=True)
colors = ['red', 'blue', 'green', 'purple', 'brown']
for sample_size, color in zip(sample_sizes, colors):
    means = [np.random.choice(original_data, size=sample_size).mean() for _ in range(1000)]
    axes[1, 0].hist(means, bins=30, alpha=0.5, color=color, label=f'n={sample_size}', density=True)
axes[1, 0].set_title('CLT: Convergence with Sample Size', fontsize=12, fontweight='bold')
axes[1, 0].set_xlabel('Value')
axes[1, 0].set_ylabel('Density')
axes[1, 0].legend()
axes[1, 0].grid(True, alpha=0.3)

# Plot 4: Q-Q plot of sample means
stats.probplot(sample_means, dist="norm", plot=axes[1, 1])
axes[1, 1].set_title('Q-Q Plot: Sample Means vs Normal Distribution', 
                     fontsize=12, fontweight='bold')
axes[1, 1].grid(True, alpha=0.3)

plt.tight_layout()
plt.show()
```

### Real-World Application: Budget Prediction

```python
print("\n" + "=" * 70)
print("PRACTICAL APPLICATION: Using CLT for Budget Prediction")
print("=" * 70)

# BUDGET PREDICTION SCENARIO
# Your daily spending is chaotic and random
daily_spending = np.random.uniform(low=100, high=500, size=365)

# Method 1: Using MEAN (relies on CLT)
mean_daily = daily_spending.mean()
predicted_monthly_from_mean = mean_daily * 30

# Method 2: Using MEDIAN
median_daily = np.median(daily_spending)
predicted_monthly_from_median = median_daily * 30

# Actual total
actual_total = daily_spending.sum()

print(f"\nDaily Spending Statistics:")
print(f"Mean: ${mean_daily:.2f}")
print(f"Median: ${median_daily:.2f}")
print(f"Std Dev: ${daily_spending.std():.2f}")

print(f"\nAnnual Spending Predictions:")
print(f"Using MEAN method: ${predicted_monthly_from_mean * 12:.2f}")
print(f"Using MEDIAN method: ${predicted_monthly_from_median * 12:.2f}")
print(f"Actual total: ${actual_total:.2f}")

print(f"\nError Analysis:")
mean_error = abs((predicted_monthly_from_mean * 12) - actual_total)
median_error = abs((predicted_monthly_from_median * 12) - actual_total)
print(f"Mean prediction error: ${mean_error:.2f}")
print(f"Median prediction error: ${median_error:.2f}")
print(f"MEAN is better: {mean_error < median_error}")

# Visualization
fig, axes = plt.subplots(1, 2, figsize=(14, 5))

# Plot 1: Daily spending
axes[0].hist(daily_spending, bins=40, alpha=0.7, color='teal', edgecolor='black')
axes[0].axvline(mean_daily, color='red', linestyle='--', linewidth=2, label=f'Mean: ${mean_daily:.2f}')
axes[0].axvline(median_daily, color='green', linestyle='--', linewidth=2, label=f'Median: ${median_daily:.2f}')
axes[0].set_title('Daily Spending Distribution (Non-Normal)', fontsize=12, fontweight='bold')
axes[0].set_xlabel('Spending ($)')
axes[0].set_ylabel('Frequency')
axes[0].legend()
axes[0].grid(True, alpha=0.3)

# Plot 2: Annual predictions comparison
methods = ['Mean\nMethod', 'Median\nMethod', 'Actual\nTotal']
predictions = [predicted_monthly_from_mean * 12, predicted_monthly_from_median * 12, actual_total]
colors_bar = ['red', 'green', 'blue']
bars = axes[1].bar(methods, predictions, color=colors_bar, alpha=0.7, edgecolor='black')
axes[1].set_title('Annual Spending: Prediction vs Actual', fontsize=12, fontweight='bold')
axes[1].set_ylabel('Amount ($)')
axes[1].grid(True, alpha=0.3, axis='y')

# Add value labels on bars
for bar, pred in zip(bars, predictions):
    height = bar.get_height()
    axes[1].text(bar.get_x() + bar.get_width()/2., height,
                f'${pred:.0f}',
                ha='center', va='bottom', fontweight='bold')

plt.tight_layout()
plt.show()

# The CLT tells us: Even though daily spending is messy,
# the AVERAGE daily spending is reliable for predictions!
print("\nKey Insight: CLT shows that means are predictable even with chaotic data!")
```

---

## The Key Distinction: How to Choose

| Question | Distribution | Example |
|----------|--------------|---------|
| "What is the *value* of this measurement?" | **Normal (No significant outlier)** | "How much flour in kg?" |
| "How *many times* does an event happen in a period?" | **Poisson (With significant outlier)** | "How many prayers per day?" |
| "Did it *succeed or fail*?" | **Binomial** | "Did the ritual work?" |

---

## Central Limit Theorem (Why We Trust Our Predictions)

Even if the underlying data doesn't perfectly follow a distribution, **if we take multiple samples and average them**, those averages will follow a Normal distribution.

**This means:**
- We can make reliable predictions about future months
- Outliers become less influential when we look at patterns
- We can trust statistical measures like mean and standard deviation

---

## Visualization Summary - Temple Data Application

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Create the actual temple data
np.random.seed(42)

days = pd.date_range('2025-01-01', periods=90, freq='D')

# Prayer requests: Average 15 per day, but varies (Poisson distribution)
prayer_requests = np.random.poisson(lam=15, size=90)

# Flour consumption: Depends on prayer requests (Normal distribution)
flour_kg = 2 * prayer_requests + np.random.normal(0, 3, size=90)
flour_kg = np.clip(flour_kg, 0, None)

# Ritual success rate: About 75% success (Binomial-like)
ritual_success_rate = np.random.binomial(n=10, p=0.75, size=90) / 10 * 100

temple_data = pd.DataFrame({
    'date': days,
    'prayer_requests': prayer_requests,
    'flour_consumed_kg': flour_kg,
    'ritual_success_rate': ritual_success_rate
})

print(temple_data.head(10))

# Visualization
plt.figure(figsize=(17, 12))

# 1A. Prayer Requests - Poisson Distribution
plt.subplot(3, 2, 1)
plt.plot(temple_data['date'], temple_data['prayer_requests'], marker='o', linestyle='-', linewidth=2)
plt.title('Prayer Requests Over Time (Poisson Distribution)', fontweight='bold')
plt.xlabel('Date')
plt.ylabel('Number of Requests')
plt.grid(True, alpha=0.3)
plt.xticks(rotation=45)

# 1B. Prayer Requests - Histogram
plt.subplot(3, 2, 2)
plt.hist(temple_data['prayer_requests'], bins=15, edgecolor='black', alpha=0.7, color='green')
plt.axvline(temple_data['prayer_requests'].mean(), color='red', linestyle='--', linewidth=2, 
            label=f'Mean: {temple_data["prayer_requests"].mean():.2f}')
plt.title('Prayer Requests Distribution (Poisson)', fontweight='bold')
plt.xlabel('Number of Requests')
plt.ylabel('Frequency')
plt.legend()
plt.grid(True, alpha=0.3)

# 2A. Ritual Success Rate - Binomial Distribution
plt.subplot(3, 2, 3)
plt.plot(temple_data['date'], temple_data['ritual_success_rate'], marker='o', linestyle='-', linewidth=2, color='purple')
plt.title('Ritual Success Rate Over Time (Binomial Distribution)', fontweight='bold')
plt.xlabel('Date')
plt.ylabel('Success Rate (%)')
plt.grid(True, alpha=0.3)
plt.xticks(rotation=45)

# 2B. Ritual Success Rate - Histogram
plt.subplot(3, 2, 4)
plt.hist(temple_data['ritual_success_rate'], bins=15, edgecolor='black', alpha=0.7, color='purple')
plt.axvline(temple_data['ritual_success_rate'].mean(), color='red', linestyle='--', linewidth=2, 
            label=f'Mean: {temple_data["ritual_success_rate"].mean():.2f}%')
plt.title('Ritual Success Rate Distribution (Binomial)', fontweight='bold')
plt.xlabel('Success Rate (%)')
plt.ylabel('Frequency')
plt.legend()
plt.grid(True, alpha=0.3)

# 3A. Flour Consumption - Normal Distribution
plt.subplot(3, 2, 5)
plt.plot(temple_data['date'], temple_data['flour_consumed_kg'], marker='o', linestyle='-', linewidth=2, color='brown')
plt.title('Flour Consumption Over Time (Normal Distribution)', fontweight='bold')
plt.xlabel('Date')
plt.ylabel('Flour (kg)')
plt.grid(True, alpha=0.3)
plt.xticks(rotation=45)

# 3B. Flour Consumption - Histogram
plt.subplot(3, 2, 6)
plt.hist(temple_data['flour_consumed_kg'], bins=20, edgecolor='black', alpha=0.7, color='orange')
plt.axvline(temple_data['flour_consumed_kg'].mean(), color='red', linestyle='--', linewidth=2, 
            label=f'Mean: {temple_data["flour_consumed_kg"].mean():.1f}kg')
plt.axvline(temple_data['flour_consumed_kg'].median(), color='green', linestyle='--', linewidth=2, 
            label=f'Median: {temple_data["flour_consumed_kg"].median():.1f}kg')
plt.title('Flour Consumed Distribution (Normal)', fontweight='bold')
plt.xlabel('Flour (kg)')
plt.ylabel('Frequency')
plt.legend()
plt.grid(True, alpha=0.3)

plt.tight_layout()
plt.show()

# Print statistics
print("\n" + "="*70)
print("TEMPLE DATA STATISTICS")
print("="*70)
print(f"\nPrayer Requests (Poisson):")
print(f"  Mean: {temple_data['prayer_requests'].mean():.2f}")
print(f"
