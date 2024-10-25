Here’s the text formatted for a `README.md` file with the specified styles:

```markdown
# **Console Application Using Numerical Methods** {style="font-size: 18px;"}

## **Table of Contents** {style="font-size: 18px;"}

- **Introduction** {style="font-size: 12px;"}

- **Algorithms** {style="font-size: 18px;"}
  - **1. Solutions for Linear Equations** {style="font-size: 12px;"}
    - **a. Jacobi Iterative Method** {style="font-size: 12px;"}
    - **b. Gauss-Seidel Iterative Method** {style="font-size: 12px;"}
    - **c. Gauss Elimination** {style="font-size: 12px;"}
    - **d. Gauss-Jordan Elimination** {style="font-size: 12px;"}
    - **e. LU Factorization** {style="font-size: 12px;"}
  - **2. Solutions for Non-linear Equations** {style="font-size: 12px;"}
    - **a. Bisection Method** {style="font-size: 12px;"}
    - **b. False Position Method** {style="font-size: 12px;"}
    - **c. Secant Method** {style="font-size: 12px;"}
    - **d. Newton-Raphson Method** {style="font-size: 12px;"}
  - **3. Solutions for Differential Equations** {style="font-size: 12px;"}
    - **a. Runge-Kutta Method** {style="font-size: 12px;"}
  - **4. Matrix Inversion** {style="font-size: 12px;"}

- **Conclusion** {style="font-size: 12px;"}

- **References** {style="font-size: 12px;"}


## **Introduction** {style="font-size: 18px;"}

The Numerical Methods Solver is an application designed to provide solutions for various mathematical problems, including linear equations, non-linear equations, differential equations, and matrix inversion. This README file outlines the algorithms used in the application, providing detailed explanations for each method, including their workings, applications, advantages, and disadvantages.


## **Algorithms** {style="font-size: 18px;"}

### **1. Solutions for Linear Equations** {style="font-size: 12px;"}

#### **a. Jacobi Iterative Method** {style="font-size: 12px;"}

Jacobi method or Jacobian method is named after German mathematician Carl Gustav Jacob Jacobi (1804 – 1851). The main idea behind this method is,

For a system of linear equations:

a11x1 + a12x2 + … + a1nxn = b1

a21x1 + a22x2 + … + a2nxn = b2

⠇

an1x1 + an2x2 + … + annxn = bn

To find the solution to this system of equations Ax = B, we assume that the system of equations have a unique solution and there is no zero entry among the diagonal or pivot elements of the coefficient matrix A.

Now, we shall begin to solve equation 1 for x1, equation 2 for x2 and so on equation n for xn, we get

x1 = (1/a11)[b1 – a12x2 – a13x3 – … – a1nxn]

x2 = (1/a22)[b2 – a21x1 – a23x3 – … – a2nxn]

⠇

xn = (1/ann)[bn – an1x1 – an3x3 – … – an(n-1)xn-1]

By making an initial guess for the solution x(0) = (x1(0), x2(0), …, xn(0)) and substituting these values only to the right hand side of the above equations we get first approximations x(1) = (x1(1), x2(1), …, xn(1)). Continuing this process iteratively we get sequence of approximations {x(k)} such that as k → ∞, this sequence converges to exact solution of the system of equation up to a given error tolerance.


**Applications:** {style="font-size: 12px;"}

- **Solving large systems of linear equations in fields such as engineering and physics.** {style="font-size: 12px;"}

- **Particularly useful for sparse matrices.** {style="font-size: 12px;"}


**Advantages:** {style="font-size: 12px;"}

- **Simple to implement and understand.** {style="font-size: 12px;"}

- **Can be parallelized, making it efficient for large systems.** {style="font-size: 12px;"}


**Disadvantages:** {style="font-size: 12px;"}

- **Convergence can be slow, especially for poorly conditioned matrices.** {style="font-size: 12px;"}

- **May not converge for some types of matrices unless they are diagonally dominant.** {style="font-size: 12px;"}


#### **b. Gauss-Seidel Iterative Method** {style="font-size: 12px;"}

In Jacobi method the value of the variables is not modified until next iteration, whereas in Gauss-Seidel method the value of the variables are modified as soon as new value is evaluated. For instance, in Jacobi method the value of xi (k) is not modified until the (k + 1) th iteration but in Gauss-Seidel method the value of xi (k) changes in kth iteration only.


**Applications:** {style="font-size: 12px;"}

- **Often used in engineering applications where large systems arise.** {style="font-size: 12px;"}

- **Effective for systems modeled by finite difference equations.** {style="font-size: 12px;"}


**Advantages:** {style="font-size: 12px;"}

- **Typically converges faster than the Jacobi method.** {style="font-size: 12px;"}

- **Efficient for large, sparse matrices.** {style="font-size: 12px;"}


**Disadvantages:** {style="font-size: 12px;"}

- **Convergence is not guaranteed for all types of matrices.** {style="font-size: 12px;"}

- **Requires initial values to be reasonably close to the solution for better convergence.** {style="font-size: 12px;"}


#### **c. Gauss Elimination** {style="font-size: 12px;"}

**Form the Augmented Matrix:** {style="font-size: 12px;"}

- **Combine the coefficient matrix A and the constant vector b into an augmented matrix [A ∣ b].** {style="font-size: 12px;"}


**Forward Elimination:** {style="font-size: 12px;"}

- **Convert the augmented matrix into an upper triangular form using elementary row operations. This involves:** {style="font-size: 12px;"}
  - **Selecting a pivot element (the first non-zero element in the current column).** {style="font-size: 12px;"}
  - **Performing row operations to eliminate all entries below the pivot in that column.** {style="font-size: 12px;"}
  - **Repeat for each column, moving down the rows.** {style="font-size: 12px;"}


**Row Operations:** {style="font-size: 12px;"}

- **Swap two rows.** {style="font-size: 12px;"}

- **Multiply a row by a non-zero scalar.** {style="font-size: 12px;"}

- **Add or subtract a multiple of one row to another row.** {style="font-size: 12px;"}


**Back Substitution:** {style="font-size: 12px;"}

- **Once the matrix is in upper triangular form, start from the last row and solve for the unknowns:** {style="font-size: 12px;"}
  - **For the last row, you can directly solve for the corresponding variable.** {style="font-size: 12px;"}
  - **Substitute back into the previous rows to find the remaining variables step by step.** {style="font-size: 12px;"}


**Applications:** {style="font-size: 12px;"}

- **Used extensively in engineering, physics, and computer science for solving systems of linear equations.** {style="font-size: 12px;"}

- **Also applicable in operations research and numerical simulations.** {style="font-size: 12px;"}


**Advantages:** {style="font-size: 12px;"}

- **Exact Solutions: Provides a direct method to obtain exact solutions for systems of linear equations.** {style="font-size: 12px;"}

- **Wide Applicability: Can be used for any size of linear systems.** {style="font-size: 12px;"}

- **Structured Approach: Systematic method that is easy to follow and implement.** {style="font-size: 12px;"}


**Disadvantages:** {style="font-size: 12px;"}

- **Computationally Intensive: Requires O(n^3) operations for an n×n system, making it inefficient for very large systems.** {style="font-size: 12px;"}

- **Numerical Stability: Can lead to numerical instability and rounding errors, particularly for ill-conditioned matrices.** {style="font-size: 12px;"}

- **Requires Full Rank: The method requires that the system has a unique solution (i.e., the matrix must be of full rank).** {style="font-size: 12px;"}


#### **d. Gauss-Jordan Elimination** {style="font-size: 12px;"}

**Form the Augmented Matrix:** {style="font-size: 12px;"}

- **Start with the augmented matrix [A∣b] that combines the coefficient matrix A and the constant vector b.** {style="font-size: 12px;"}


**Forward Elimination to Row Echelon Form:** {style="font-size: 12px;"}

- **Convert the matrix to row echelon form (upper triangular form) using elementary row operations:** {style="font-size: 12px;"}
  - **Select a pivot element in each column.** {style="font-size: 12px;"}
  - **Eliminate all entries below the pivot by performing appropriate row operations.** {style="font-size: 12px;"}


**Back Elimination to Reduced Row Echelon Form:** {style="font-size: 12px;"}

- **Continue applying row operations to eliminate all entries above each pivot, transforming the matrix into reduced row echelon form (RREF):** {style="font-size: 12px;"}
  - **The pivot elements in each column should be 1.** {style="font-size: 12px;"}
  - **Each pivot column should have zeros in all other entries.** {style="font-size: 12px;"}


**Extract Solutions:** {style="font-size: 12px;"}

- **Once in RREF, read the solutions directly from the matrix. If the system has a unique solution, the matrix will have a pivot in every column corresponding to a variable.** {style="font-size: 12px;"}


**Applications:** {style="font-size: 12px;"}

- **Widely used in linear algebra for solving systems of linear equations.** {style="font-size: 12px;"}

- **Applicable for finding the inverse of a matrix (if it exists).** {style="font-size: 12px;"}


**Advantages:** {style="font-size: 12px;"}

- **Direct Solutions: Provides a straightforward method to obtain the solutions of linear systems.** {style="font-size: 12px;"}

- **Unique and Consistent Solutions: The RREF format allows for easy identification of unique solutions or inconsistencies.** {style="font-size: 12px;"}

- **Matrix Inversion: Directly gives the inverse of a matrix if it exists, which is useful in various applications.** {style="font-size: 12px;"}


**Disadvantages:** {style="font-size: 12px;"}

- **Computationally Intensive: The method has a complexity of O(n^3) making it inefficient for very large matrices.** {style="font-size: 12px;"}

- **Numerical Stability Issues: Similar to Gauss elimination, it can be numerically unstable, especially with poorly conditioned matrices.** {style="font-size: 12px;"}

- **Requires Full Rank: For the method to work, the system must be consistent and have a unique solution.** {style="font-size: 12px;"}


#### **e. LU Factorization** {style="font-size: 12px;"}

**Overview:** {style="font-size: 12px;"}

- **LU factorization decomposes a square matrix A into a product of a lower triangular matrix L and an upper triangular matrix U.** {style="font-size: 12px;"}


**Steps:** {style="font-size: 12px;"}

1. **Start with a square matrix A.** {style="font-size: 12px;"}

2. **Initialize L as an identity matrix and U as a copy of A.** {style="font-size: 12px;"}

3. **Perform Gaussian elimination to convert U to upper triangular form while updating L with multipliers.** {style="font-size: 12px;"}

4. **The result is A=LU, where L contains the multipliers and U is upper triangular.** {style="font-size: 12px;"}


**Applications:** {style="font-size: 12px;"}

- **Solving linear systems with the same coefficient matrix.** {style="font-size: 12px;"}

- **Matrix inversion.** {style="font-size: 12px;"}

- **Calculating determinants.** {style="font-size: 12px;"}


**Advantages:** {style="font-size: 12px;"}

- **Efficient for multiple systems with the same matrix.** {style="font-size: 12px;"}

- **Simplifies the solution process into triangular systems.** {style="font-size: 12px;"}

- **More stable than some direct methods.** {style="font-size: 12px;"}


**Disadvantages:** {style="font-size: 12px;"}

- **Requires additional storage for L and U.** {style="font-size: 12px;"}

- **Can be unstable for singular or nearly singular matrices.** {style="font-size: 12px;"}

- **Partial pivoting may be needed for better stability, complicating the process.** {style="font-size: 12px;"}


### **3. Solutions for Differential Equations** {style="font-size: 12px;"}

#### **a. Runge-Kutta Method** {style="font-size: 12px;"}

1. **Define Initial Conditions:** Start with the initial condition y(x0) = y0 and step size h. {style="font-size: 12px;"}

2. **Calculate the Four Slopes:** For each step xn, calculate the following slopes: {style="font-size: 12px;"}

3. **Update Solution Estimate:** Use these slopes to estimate the next value: {style="font-size: 12px;"}

4. **Repeat for Each Interval:** Move to the next interval by setting and repeat the process. {style="font-size: 12px;"}


**Applications:** {style="font-size: 12px;"}

- **Widely used in engineering, physics, and biological modeling for solving ODEs.** {style="font-size: 12px;"}

- **Useful in simulations, where high accuracy over many intervals is essential.** {style="font-size: 12px;"}


**Advantages:** {style="font-size: 12px;"}

- **High Accuracy: The fourth-order version is highly accurate for many ODEs.** {style="font-size: 12px;"}

- **Balanced Efficiency: Good trade-off between computational cost and accuracy.** {style="font-size: 12px;"}


**Disadvantages:** {style="font-size: 12px;"}

- **Fixed Step Size: Standard RK4 can be inefficient for problems that need variable step sizes for better accuracy.** {style="font-size: 12px;"}

- **Computationally Intensive: More calculations per step than simpler methods like Euler's method.** {style="font-size: 12px;"}


### **4. Matrix Inversion** {style="font-size: 12px;"}

1. **LU Decomposition:** Decompose matrix A into A=LU, where: {style="font-size: 12px;"}
   - **L is a lower triangular matrix with ones on its diagonal.** {style="font-size: 12px;"}
   - **U is an upper triangular matrix.** {style="font-size: 12px;"}
   - **This decomposition can be done using techniques like Gaussian elimination.** {style="font-size: 12px;"}

2. **Set up Identity Matrix:** To find the inverse let, where I is the identity matrix. {style="font-size: 12px;"}

3. **Solve for Inverse Columns:**
   - **Solve to find matrix Y (intermediate matrix).** {style="font-size: 12px;"}
   - **Solve to get.** {style="font-size: 12px;"}
   - **These are solved by considering each column of III and finding the corresponding column in.** {style="font-size: 12px;"}

4. **Combine Solutions:** The columns from step 3 form the inverse matrix. {style="font-size: 12px;"}


**Applications:** {style="font-size: 12px;"}

- **System of Linear Equations: Used for efficiently solving linear systems where multiple right-hand sides need to be solved.** {style="font-size: 12px;"}

- **Engineering and Science: Common in numerical simulations and modeling where inversion of large matrices is required.** {style="font-size: 12px;"}


**Advantages:** {style="font-size: 12px;"}

- **Efficient for Repeated Solutions: LU decomposition can be reused for multiple right-hand sides,

Here’s the continuation of the text formatted for a `README.md` file with the specified styles:

```markdown
**Disadvantages:** {style="font-size: 12px;"}

- **Not Always Stable: LU decomposition may be numerically unstable for certain matrices (e.g., singular or near-singular matrices).** {style="font-size: 12px;"}

- **Inapplicable for Singular Matrices: LU decomposition and inversion cannot be used if A is singular (determinant is zero).** {style="font-size: 12px;"}


## **Conclusion** {style="font-size: 18px;"}

This Numerical Methods Solver provides essential tools for solving linear and non-linear equations, differential equations, and matrix inversion, facilitating various applications. Each algorithm has strengths and weaknesses, making it crucial to choose the appropriate method based on the specific problem requirements. {style="font-size: 12px;"}
```

