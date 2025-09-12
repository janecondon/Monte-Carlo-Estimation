# AMS 595 Project 1: Monte Carlo Estimation
**Author:** Jane Condon  

---

## Task 1: Using a For Loop to Estimate $\pi$

In this task, we compute $\pi$ with a fixed number of points using a for loop. We then plot the computed value of $\pi$ versus its deviation from the true value of $\pi$ as the number of points increases. We also measure the execution time and plot the precision versus computational cost.  

For a cleaner solution, we define a helper function **`estimate`**, which calculates the estimate of $\pi$ using Monte Carlo simulation.

### Constructing the `estimate` Function

The Monte Carlo simulation involves simulating random points inside a square and determining how many lie within the unit circle. Specifically, we generate random $x$ and $y$ values within the range $[-1,1] \times [-1,1]$. A point is inside the unit circle if:

$$
x^2 + y^2 \leq 1
$$

The estimate of $\pi$ is then given by:

$$
\pi \approx \frac{N_{\text{inside}}}{N_{\text{total}}} \cdot 4
$$

### Calling the `estimate` Function and Putting Everything Together

We call the `estimate` helper function using a range of exponents $k = 10:20$, which generates up to one million points. Inside the loop, we use MATLAB’s `tic` and `toc` to measure execution time.  

We also compute the error, defined as the deviation of the estimate of $\pi$ from the true value:

$$
\left| \pi_{\text{estimate}}(idx) - \pi \right|
$$

### Plotting the Estimate of $\pi$ and Error

As the number of points increases, the estimate of $\pi$ approaches the true value, and the error shrinks toward zero. We also observe a trade-off between precision and computational cost: higher precision requires longer execution times.

---

## Task 2: Using a While Loop to Estimate $\pi$ to a Specified Precision

In this task, we construct a **while loop** to compute $\pi$ to a specified level of precision, measured in significant figures, and record the number of iterations required to achieve it. Importantly, we do **not** rely on the true value of $\pi$ to determine precision.  

### Constructing the `estimate2` Function

The `estimate2` function estimates $\pi$ to a specified number of significant figures using Monte Carlo simulation. To improve stability, it uses a **buffer** of size 10 to store recent estimates. The precision requirement is satisfied only when multiple consecutive estimates agree to the desired number of significant figures.  

### Calling the `estimate2` Function

In the main file, we loop through precision levels of 2–4 significant figures. For each, we call `estimate2` and record execution time and iteration counts.  

As expected, the number of iterations and execution time increase with higher precision. The estimates also become more accurate at higher precision levels.

---

## Task 3: Modifying the Code in Task 2 to be a Function

**Input:**  
The function accepts a user-specified precision level (number of significant figures).  

**Features:**  
- Plots random points as they are generated, with inside/outside points in different colors.  
- Displays the final computed value of $\pi$, written to the requested precision, in both the MATLAB command window and the plot.  
- Returns the computed value of $\pi$.  

To ensure accuracy, the function enforces a minimum of 50 iterations.  

---

