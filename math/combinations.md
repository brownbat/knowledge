### Combinations and Permutations

#### Definitions

1. **Combinations (_C(n, k)_)**: The number of ways to choose _k_ elements from a set of _n_ elements without regard to the order.
   
   Formula:
```math
C(n, k) = \frac{n!}{k!(n - k)!}
```

2. **Permutations (_P(n, k)_)**: The number of ways to choose _k_ elements from a set of _n_ elements with regard to the order.
   
   Formula:
   $$
   P(n, k) = \frac{n!}{(n - k)!}
   $$

### Examples

#### Example 1: Combinations

**Problem**: How many ways can you choose 3 elements from a set of 5 elements?

1. **Total elements (_n_)**: 5
2. **Chosen elements (_k_)**: 3

**Solution**:
$$
C(5, 3) = \frac{5!}{3!(5 - 3)!} = \frac{5!}{3! \cdot 2!} = \frac{5 \times 4 \times 3!}{3! \cdot 2 \times 1} = \frac{5 \times 4}{2 \times 1} = 10
$$

#### Example 2: Permutations

**Problem**: How many ways can you arrange 3 elements from a set of 5 elements?

1. **Total elements (_n_)**: 5
2. **Chosen elements (_k_)**: 3

**Solution**:
$$
P(5, 3) = \frac{5!}{(5 - 3)!} = \frac{5!}{2!} = \frac{5 \times 4 \times 3 \times 2!}{2!} = 5 \times 4 \times 3 = 60
$$

### Summary

1. **Combinations (_C(n, k)_)**: 
   $$
   C(n, k) = \frac{n!}{k!(n - k)!}
   $$

2. **Permutations (_P(n, k)_)**: 
   $$
   P(n, k) = \frac{n!}{(n - k)!}
   $$

#### Example Problems:

1. **Combinations**:
   - **Problem**: How many ways can you choose 4 elements from a set of 10 elements?
   - **Solution**:
     $$
     C(10, 4) = \frac{10!}{4!(10 - 4)!} = \frac{10!}{4! \cdot 6!} = 210
     $$

2. **Permutations**:
   - **Problem**: How many ways can you arrange 2 elements from a set of 8 elements?
   - **Solution**:
     $$
     P(8, 2) = \frac{8!}{(8 - 2)!} = \frac{8!}{6!} = 8 \times 7 = 56
     $$
