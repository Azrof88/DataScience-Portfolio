# **Numerical Methods Solver**

## **Table of Contents**

- **Introduction**

- **Algorithms**
  - **1. Solutions for Linear Equations**
    - **a. Jacobi Iterative Method**
    - **b. Gauss-Seidel Iterative Method**
    - **c. Gauss Elimination**
    - **d. Gauss-Jordan Elimination**
    - **e. LU Factorization**
  - **2. Solutions for Non-linear Equations**
    - **a. Bisection Method**
    - **b. False Position Method**
    - **c. Secant Method**
    - **d. Newton-Raphson Method**
  - **3. Solutions for Differential Equations**
    - **a. Runge-Kutta Method**
  - **4. Matrix Inversion**

- **Conclusion**




## **Introduction**

The Numerical Methods Solver is an application designed to provide solutions for various mathematical problems, including linear equations, non-linear equations, differential equations, and matrix inversion. This README file outlines the algorithms used in the application, providing detailed explanations for each method, including their workings, applications, advantages, and disadvantages.


## **Algorithms**

### **1. Solutions for Linear Equations**

#### **a. Jacobi Iterative Method**

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


**Applications:**

- **Solving large systems of linear equations in fields such as engineering and physics.**

- **Particularly useful for sparse matrices.**


**Advantages:**

- **Simple to implement and understand.**

- **Can be parallelized, making it efficient for large systems.**


**Disadvantages:**

- **Convergence can be slow, especially for poorly conditioned matrices.**

- **May not converge for some types of matrices unless they are diagonally dominant.**


#### **b. Gauss-Seidel Iterative Method**

In Jacobi method the value of the variables is not modified until next iteration, whereas in Gauss-Seidel method the value of the variables are modified as soon as new value is evaluated. For instance, in Jacobi method the value of xi (k) is not modified until the (k + 1) th iteration but in Gauss-Seidel method the value of xi (k) changes in kth iteration only.


**Applications:**

- **Often used in engineering applications where large systems arise.**

- **Effective for systems modeled by finite difference equations.**


**Advantages:**

- **Typically converges faster than the Jacobi method.**

- **Efficient for large, sparse matrices.**


**Disadvantages:**

- **Convergence is not guaranteed for all types of matrices.**

- **Requires initial values to be reasonably close to the solution for better convergence.**


#### **c. Gauss Elimination**

**Form the Augmented Matrix:**

- **Combine the coefficient matrix A and the constant vector b into an augmented matrix [A ∣ b].**


**Forward Elimination:**

- **Convert the augmented matrix into an upper triangular form using elementary row operations. This involves:**
  - **Selecting a pivot element (the first non-zero element in the current column).**
  - **Performing row operations to eliminate all entries below the pivot in that column.**
  - **Repeat for each column, moving down the rows.**


**Row Operations:**

- **Swap two rows.**

- **Multiply a row by a non-zero scalar.**

- **Add or subtract a multiple of one row to another row.**


**Back Substitution:**

- **Once the matrix is in upper triangular form, start from the last row and solve for the unknowns:**
  - **For the last row, you can directly solve for the corresponding variable.**
  - **Substitute back into the previous rows to find the remaining variables step by step.**


**Applications:**

- **Used extensively in engineering, physics, and computer science for solving systems of linear equations.**

- **Also applicable in operations research and numerical simulations.**


**Advantages:**

- **Exact Solutions: Provides a direct method to obtain exact solutions for systems of linear equations.**

- **Wide Applicability: Can be used for any size of linear systems.**

- **Structured Approach: Systematic method that is easy to follow and implement.**


**Disadvantages:**

- **Computationally Intensive: Requires O(n^3) operations for an n×n system, making it inefficient for very large systems.**

- **Numerical Stability: Can lead to numerical instability and rounding errors, particularly for ill-conditioned matrices.**

- **Requires Full Rank: The method requires that the system has a unique solution (i.e., the matrix must be of full rank).**


#### **d. Gauss-Jordan Elimination**

**Form the Augmented Matrix:**

- **Start with the augmented matrix [A∣b] that combines the coefficient matrix A and the constant vector b.**


**Forward Elimination to Row Echelon Form:**

- **Convert the matrix to row echelon form (upper triangular form) using elementary row operations:**
  - **Select a pivot element in each column.**
  - **Eliminate all entries below the pivot by performing appropriate row operations.**


**Back Elimination to Reduced Row Echelon Form:**

- **Continue applying row operations to eliminate all entries above each pivot, transforming the matrix into reduced row echelon form (RREF):**
  - **The pivot elements in each column should be 1.**
  - **Each pivot column should have zeros in all other entries.**


**Extract Solutions:**

- **Once in RREF, read the solutions directly from the matrix. If the system has a unique solution, the matrix will have a pivot in every column corresponding to a variable.**


**Applications:**

- **Widely used in linear algebra for solving systems of linear equations.**

- **Applicable for finding the inverse of a matrix (if it exists).**


**Advantages:**

- **Direct Solutions: Provides a straightforward method to obtain the solutions of linear systems.**

- **Unique and Consistent Solutions: The RREF format allows for easy identification of unique solutions or inconsistencies.**

- **Matrix Inversion: Directly gives the inverse of a matrix if it exists, which is useful in various applications.**


**Disadvantages:**

- **Computationally Intensive: The method has a complexity of O(n^3) making it inefficient for very large matrices.**

- **Numerical Stability Issues: Similar to Gauss elimination, it can be numerically unstable, especially with poorly conditioned matrices.**

- **Requires Full Rank: For the method to work, the system must be consistent and have a unique solution.**


#### **e. LU Factorization**

**Overview:** 

- **LU factorization decomposes a square matrix A into a product of a lower triangular matrix L and an upper triangular matrix U.**


**Steps:**

1. **Start with a square matrix A.**

2. **Initialize L as an identity matrix and U as a copy of A.**

3. **Perform Gaussian elimination to convert U to upper triangular form while updating L with multipliers.**

4. **The result is A=LU, where L contains the multipliers and U is upper triangular.**


**Applications:**

- **Solving linear systems with the same coefficient matrix.**

- **Matrix inversion.**

- **Calculating determinants.**


**Advantages:**

- **Efficient for multiple systems with the same matrix.**

- **Simplifies the solution process into triangular systems.**

- **More stable than some direct methods.**


**Disadvantages:**

- **Requires additional storage for L and U.**

- **Can be unstable for singular or nearly singular matrices.**

- **Partial pivoting may be needed for better stability, complicating the process.**


### **3. Solutions for Differential Equations**

#### **a. Runge-Kutta Method**

1. **Define Initial Conditions:** Start with the initial condition y(x0) = y0 and step size h.

2. **Calculate the Four Slopes:** For each step xn, calculate the following slopes:

3. **Update Solution Estimate:** Use these slopes to estimate the next value:

4. **Repeat for Each Interval:** Move to the next interval by setting and repeat the process.


**Applications:**

- **Widely used in engineering, physics, and biological modeling for solving ODEs.**

- **Useful in simulations, where high accuracy over many intervals is essential.**


**Advantages:**

- **High Accuracy: The fourth-order version is highly accurate for many ODEs.**

- **Balanced Efficiency: Good trade-off between computational cost and accuracy.**


**Disadvantages:**

- **Fixed Step Size: Standard RK4 can be inefficient for problems that need variable step sizes for better accuracy.**

- **Computationally Intensive: More calculations per step than simpler methods like Euler's method.**


### **4. Matrix Inversion**

1. **LU Decomposition:** Decompose matrix A into A=LU, where:
   - **L is a lower triangular matrix with ones on its diagonal.**
   - **U is an upper triangular matrix.**
   - **This decomposition can be done using techniques like Gaussian elimination.**

2. **Set up Identity Matrix:** To find the inverse let, where I is the identity matrix.

3. **Solve for Inverse Columns:**
   - **Solve to find matrix Y (intermediate matrix).**
   - **Solve to get.**
   - **These are solved by considering each column of III and finding the corresponding column in.**

4. **Combine Solutions:** The columns from step 3 form the inverse matrix.


**Applications:**

- **System of Linear Equations: Used for efficiently solving linear systems where multiple right-hand sides need to be solved.**

- **Engineering and Science: Common in numerical simulations and modeling where inversion of large matrices is required.**


**Advantages:**

- **Efficient for Repeated Solutions: LU decomposition can be reused for multiple right-hand sides, saving computation.**

- **Simplifies Calculations: Once L and U are computed, inverting becomes a set of straightforward linear solves.**


**Disadvantages:**

- **Not Always Stable: LU decomposition may be numerically unstable for certain matrices (e.g., singular or near-singular matrices).**

- **Inapplicable for Singular Matrices: LU decomposition and inversion cannot be used if A is singular (determinant is zero).**


## **Conclusion**

This Numerical Methods Solver provides essential tools for solving linear and non-linear equations, differential equations, and matrix inversion, facilitating various applications. Each algorithm has strengths and weaknesses, making it crucial to choose the appropriate method based on the specific problem requirements.


