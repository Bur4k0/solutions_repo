# Problem 1

---

### Exploring the Central Limit Theorem Through Simulations

The Central Limit Theorem (CLT) tells us that, given a sufficiently large sample size, the distribution of sample means will approximate a normal distribution, regardless of the population’s original distribution. This simulation will demonstrate that phenomenon by generating data from different population distributions, sampling repeatedly, and visualizing the results.

#### Task 1: Simulating Sampling Distributions

We’ll simulate populations from three distinct distributions:

- **Uniform Distribution**: Equal probability across a range (e.g., 0 to 1).

- **Exponential Distribution**: Skewed, often modeling time between events (e.g., scale = 1).

- **Binomial Distribution**: Discrete, modeling successes in trials (e.g., n=10, p=0.5).

For each, we’ll generate a large population dataset (e.g., 10,000 points).

#### Task 2: Sampling and Visualization

We’ll draw random samples of sizes 5, 10, 30, and 50, compute their means, repeat this process 1,000 times to build a sampling distribution, and plot histograms to observe the shift toward normality.

#### Task 3: Parameter Exploration

We’ll examine how the original distribution’s shape and variance, along with sample size, affect convergence to normality.

#### Task 4: Practical Applications

We’ll discuss real-world relevance at the end.

---

### Python Implementation

Here’s a complete Python script using NumPy for data generation and Matplotlib/Seaborn for plotting:

```python
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Set random seed for reproducibility
np.random.seed(42)

# Parameters
population_size = 10000  # Size of the population
sample_sizes = [5, 10, 30, 50]  # Different sample sizes to test
num_samples = 1000  # Number of samples to draw for each size

# Step 1: Generate population data for different distributions
uniform_pop = np.random.uniform(low=0, high=1, size=population_size)
exponential_pop = np.random.exponential(scale=1, size=population_size)
binomial_pop = np.random.binomial(n=10, p=0.5, size=population_size)

populations = {
    "Uniform": uniform_pop,
    "Exponential": exponential_pop,
    "Binomial": binomial_pop
}

# Step 2: Simulate sampling distributions and plot
for dist_name, population in populations.items():
    plt.figure(figsize=(12, 8))
    plt.suptitle(f"Sampling Distribution of Means - {dist_name}", fontsize=16)
    
    for i, n in enumerate(sample_sizes, 1):
        # Generate sampling distribution of means
        sample_means = [np.mean(np.random.choice(population, size=n)) for _ in range(num_samples)]
        
        # Plot histogram
        plt.subplot(2, 2, i)
        sns.histplot(sample_means, bins=30, kde=True, stat="density")
        plt.title(f"Sample Size = {n}")
        plt.xlabel("Sample Mean")
        plt.ylabel("Density")
    
    plt.tight_layout(rect=[0, 0, 1, 0.95])
    plt.show()

# Step 3: Calculate population variance for exploration
for dist_name, population in populations.items():
    pop_variance = np.var(population)
    print(f"{dist_name} Population Variance: {pop_variance:.4f}")
```

[Exploring the Central Limit Theorem](statistic.html)

[Statistic_2](statistic21.html)
---

### Results and Observations

#### Plots
For each distribution:
- **Uniform**: Starts flat, becomes bell-shaped as sample size increases.

- **Exponential**: Highly skewed initially, approaches normality with larger samples.

- **Binomial**: Discrete steps smooth out into a normal curve.

As sample size grows from 5 to 50, the histograms tighten around the population mean and resemble a normal distribution, aligning with CLT.

#### Parameter Exploration

- **Shape Influence**: The exponential distribution (skewed) converges more slowly than the uniform (symmetric) due to its asymmetry. Binomial convergence depends on $n$ and $p$ symmetry (here, $p=0.5$ is symmetric).

- **Sample Size**: Larger samples (e.g., 50) show clearer normality than smaller ones (e.g., 5).

- **Variance Impact**: The sampling distribution’s spread is governed by $\sigma^2/n$, where $\sigma^2$ is the population variance and $n$ is the sample size. Higher variance (e.g., binomial here) results in wider initial spreads, which narrow as $n$ increases.

Sample output variances (approximate, based on parameters):

- Uniform: ~0.0833 (theoretical: $1/12$)

- Exponential: ~1.0 (theoretical: $scale^2$)

- Binomial: ~2.5 (theoretical: $np(1-p)$)

---

### Practical Applications

The CLT underpins many real-world statistical methods:
1. **Estimating Population Parameters**: Sample means estimate population means (e.g., polling averages), with confidence intervals relying on normality.
2. **Quality Control**: In manufacturing, average product weights are monitored; CLT ensures deviations are interpretable.
3. **Financial Models**: Stock returns, assumed normal over large samples, use CLT for risk predictions.

---

### Discussion

These simulations confirm the CLT: regardless of the population (uniform, exponential, binomial), sample means form a normal distribution as $n$ increases. The rate of convergence varies—skewed distributions take longer, and variance affects spread—but the theorem holds. This computational approach bridges theory and intuition, showing why CLT is a statistical powerhouse.

---

Feel free to tweak parameters (e.g., exponential scale, binomial $p$) or add distributions (e.g., normal) to deepen your exploration. Let me know if you’d like help refining this further!
