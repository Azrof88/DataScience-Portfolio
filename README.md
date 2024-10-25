# <span style="font-size: 18px; font-weight: bold;">Numerical Methods Solver</span>

## <span style="font-size: 18px; font-weight: bold;">Table of Contents</span>
- [Introduction](#introduction)  
- [Algorithms](#algorithms)  
  - [1. Solutions for Linear Equations](#1-solutions-for-linear-equations)  
    - [a. Jacobi Iterative Method](#a-jacobi-iterative-method)  
    - [b. Gauss-Seidel Iterative Method](#b-gauss-seidel-iterative-method)  
    - [c. Gauss Elimination](#c-gauss-elimination)  
    - [d. Gauss-Jordan Elimination](#d-gauss-jordan-elimination)  
    - [e. LU Factorization](#e-lu-factorization)  
  - [2. Solutions for Non-linear Equations](#2-solutions-for-non-linear-equations)  
    - [a. Bisection Method](#a-bisection-method)  
    - [b. False Position Method](#b-false-position-method)  
    - [c. Secant Method](#c-secant-method)  
    - [d. Newton-Raphson Method](#d-newton-raphson-method)  
  - [3. Solutions for Differential Equations](#3-solutions-for-differential-equations)  
    - [a. Runge-Kutta Method](#a-runge-kutta-method)  
  - [4. Matrix Inversion](#4-matrix-inversion)  
- [Conclusion](#conclusion)  

## <span style="font-size: 18px; font-weight: bold;">Introduction</span>  
The Numerical Methods Solver is an application designed to provide solutions for various mathematical problems, including linear equations, non-linear equations, differential equations, and matrix inversion. This README file outlines the algorithms used in the application, providing detailed explanations for each method, including their workings, applications, advantages, and disadvantages.  

#### <span style="font-size: 12px; font-weight: bold;">e. LU Factorization</span>  
**Overview:** LU factorization decomposes a square matrix \(A\) into a product of a lower triangular matrix \(L\) and an upper triangular matrix \(U\).  

**Steps:**  
1. Start with a square matrix \(A\).  
2. Initialize \(L\) as an identity matrix and \(U\) as a copy of \(A\).  
3. Perform Gaussian elimination to convert \(U\) to upper triangular form while updating \(L\) with multipliers.  
4. The result is \(A = LU\), where \(L\) contains the multipliers and \(U\) is upper triangular.  

**Applications:**  
- Solving linear systems with the same coefficient matrix.  
- Matrix inversion.  
- Calculating determinants.  

**Advantages:**  
- Efficient for multiple systems with the same matrix.  
- Simplifies the solution process into triangular systems.  
- More stable than some direct methods.  

**Disadvantages:**  
- Requires additional storage for \(L\) and \(U\).  
- Can be unstable for singular or nearly singular matrices.  
- Partial pivoting may be needed for better stability, complicating the process.  

### <span style="font-size: 18px; font-weight: bold;">3. Solutions for Differential Equations</span>  
#### <span style="font-size: 12px; font-weight: bold;">a. Runge-Kutta Method</span>  
1. **Define Initial Conditions:** Start with the initial condition \(y(x_0) = y_0\) and step size \(h\).  
2. **Calculate the Four Slopes:** For each step \(x_n\), calculate the following slopes:  
   - \(k_1\)  
   - \(k_2\)  
   - \(k_3\)  
   - \(k_4\)  

3. **Update Solution Estimate:** Use these slopes to estimate the next value:  
   - \(y_{n+1} = y_n + \frac{1}{6}(k_1 + 2k_2 + 2k_3 + k_4)\)  

4. **Repeat for Each Interval:** Move to the next interval by setting \(x_{n+1} = x_n + h\) and repeat the process.  

**Applications:**  
- Widely used in engineering, physics, and biological modeling for solving ODEs.  
- Useful in simulations, where high accuracy over many intervals is essential.  

**Advantages:**  
- **High Accuracy:** The fourth-order version is highly accurate for many ODEs.  
- **Balanced Efficiency:** Good trade-off between computational cost and accuracy.  

**Disadvantages:**  
- **Fixed Step Size:** Standard RK4 can be inefficient for problems that need variable step sizes for better accuracy.  
- **Computationally Intensive:** More calculations per step than simpler methods like Euler's method.  

### <span style="font-size: 18px; font-weight: bold;">4. Matrix Inversion</span>  
1. **LU Decomposition:** Decompose matrix \(A\) into \(A = LU\), where:  
   - \(L\) is a lower triangular matrix with ones on its diagonal.  
   - \(U\) is an upper triangular matrix.  
   - This decomposition can be done using techniques like Gaussian elimination.  

2. **Set up Identity Matrix:** To find the inverse let \(I\) be the identity matrix.  

3. **Solve for Inverse Columns:**  
   - Solve \(LY = I\) to find matrix \(Y\) (intermediate matrix).  
   - Solve \(UX = Y\) to get \(X\).  
   - These are solved by considering each column of \(I\) and finding the corresponding column in \(X\).  

4. **Combine Solutions:** The columns from step 3 form the inverse matrix \(A^{-1}\).  

**Applications:**  
- System of Linear Equations: Used for efficiently solving linear systems where multiple right-hand sides need to be solved.  
- Engineering and Science: Common in numerical simulations and modeling where inversion of large matrices is required.  

**Advantages:**  
- Efficient for Repeated Solutions: LU decomposition can be reused for multiple right-hand sides, saving computation.  
- Simplifies Calculations: Once \(L\) and \(U\) are computed, inverting becomes a set of straightforward linear solves.  

**Disadvantages:**  
- Not Always Stable: LU decomposition may be numerically unstable for certain matrices (e.g., singular or near-singular matrices).  
- Inapplicable for Singular Matrices: LU decomposition and inversion cannot be used if \(A\) is singular (determinant is zero).  

## <span style="font-size: 18px; font-weight: bold;">Conclusion</span>  
This Numerical Methods Solver provides essential tools for solving linear and non-linear equations, differential equations, and matrix inversion, facilitating various applications. Each algorithm has strengths and weaknesses, making it crucial to choose the appropriate method based on the specific problem requirements.  
