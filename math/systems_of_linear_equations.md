Systems of linear equations can be solved using various methods, including substitution, elimination, and matrix methods. One powerful matrix method is Gaussian elimination, which simplifies the system to make it easier to solve. This section covers the basics of solving systems of linear equations and provides a step-by-step guide to Gaussian elimination.

## Methods for Solving Systems of Linear Equations

### Substitution Method
* Solve one equation for one variable in terms of the other variables.
* Substitute this expression into the other equations to reduce the number of variables.
* Repeat until you have a single equation with one variable.
* Solve for this variable and back-substitute to find the other variables.

### Elimination Method
- Multiply or divide equations to align coefficients of one variable.
- Add or subtract equations to eliminate one variable.
- Solve the resulting system of equations.
- Repeat as necessary to solve for all variables.

### Gaussian Elimination (Row Reduction)
- Write the system of equations as an augmented matrix.
- Use row operations to transform the matrix into row-echelon form (upper triangular form).
- Back-substitute to find the solutions.

Step 1: Write the Augmented Matrix

Convert the system of equations into an augmented matrix. 

For example, consider the system of equations:
```math
\begin{cases}
2x + 3y - z = 1 \\
4x - y + 2z = 2 \\
-2x + y + 2z = -3
\end{cases}
```

The augmented matrix is:

```math
\begin{bmatrix}
2 & 3 & -1 & \mid & 1 \\
4 & -1 & 2 & \mid & 2 \\
-2 & 1 & 2 & \mid & -3
\end{bmatrix}
```

Step 2: Perform Row Operations to Reach Row-Echelon Form

Use the following row operations to simplify the matrix:

- Swap rows.
- Multiply a row by a nonzero scalar.
- Add or subtract multiples of one row from another row.

Example: Convert the augmented matrix from Step 1 to row-echelon form.

1. $$R_2←R_2−2\cdotR_1$$

```math
\begin{bmatrix}
2 & 3 & -1 & \mid & 1 \
0 & -7 & 4 & \mid & 0 \
-2 & 1 & 2 & \mid & -3
\end{bmatrix}
```

2. $$R3←R3+R1$$

```math
\begin{bmatrix}
2 & 3 & -1 & \mid & 1 \
0 & -7 & 4 & \mid & 0 \
0 & 4 & 1 & \mid & -2
\end{bmatrix}
```

3. $$R2←1−7R2$$

```math
\begin{bmatrix}
2 & 3 & -1 & \mid & 1 \
0 & 1 & -\frac{4}{7} & \mid & 0 \
0 & 4 & 1 & \mid & -2
\end{bmatrix}
```

4. $$R3←R3−4R2$$

```math
\begin{bmatrix}
2 & 3 & -1 & \mid & 1 \
0 & 1 & -\frac{4}{7} & \mid & 0 \
0 & 0 & \frac{15}{7} & \mid & -2
\end{bmatrix}
```
