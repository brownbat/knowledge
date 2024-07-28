### Combinations and Permutations

#### Definitions

1. **Combinations (_C(n, k)_)**: The number of ways to choose _k_ elements from a set of _n_ elements without regard to the order.
   
   ```math
   C(n, k) = \frac{n!}{k!(n - k)!}
   ```

2. **Permutations (_P(n, k)_)**: The number of ways to choose _k_ elements from a set of _n_ elements with regard to the order.
   
   ```math
   P(n, k) = \frac{n!}{(n - k)!}
   ```

### Examples

#### Example 1: Combinations

**Problem**: How many ways can you choose 3 elements from a set of 5 elements?

1. **Total elements (_n_)**: 5
2. **Chosen elements (_k_)**: 3

**Solution**:
```math
C(5, 3) = \frac{5!}{3!(5 - 3)!} 
= \frac{5!}{3! \cdot 2!} 
= \frac{5 \times 4 \times 3!}{3! \cdot 2 \times 1} 
= \frac{5 \times 4}{2 \times 1} 
= 10
```

#### Example 2: Permutations

**Problem**: How many ways can you arrange 3 elements from a set of 5 elements?

1. **Total elements (_n_)**: 5
2. **Chosen elements (_k_)**: 3

**Solution**:
```math
P(5, 3) = \frac{5!}{(5 - 3)!} = \frac{5!}{2!} = \frac{5 \times 4 \times 3 \times 2!}{2!} = 5 \times 4 \times 3 = 60
```

### Summary

1. **Combinations (_C(n, k)_)**: 
   ```math
   C(n, k) = \frac{n!}{k!(n - k)!}
   ```

2. **Permutations (_P(n, k)_)**: 
   ```math
   P(n, k) = \frac{n!}{(n - k)!}
   ```

#### Example Problems:

1. **Combinations**:
   - **Problem**: How many ways can you choose 4 elements from a set of 10 elements?
   - **Solution**:
     ```math
     C(10, 4) = \frac{10!}{4!(10 - 4)!} = \frac{10!}{4! \cdot 6!} = 210
     ```

2. **Permutations**:
   - **Problem**: How many ways can you arrange 2 elements from a set of 8 elements?
   - **Solution**:
     ```math
     P(8, 2) = \frac{8!}{(8 - 2)!} = \frac{8!}{6!} = 8 \times 7 = 56
     ```

### Special Cases and Shortcuts

1. **Choosing 0 or All Items**:
    - $\binom{n}{0} = 1$ and $\binom{n}{n} = 1$ because there is only one way to choose none or all items.

2. **Choosing 1 item**: 
   - _n_ when there are _n_ items.

3. **Simplifying Factorials**:
    - Cancel common factorials to quickly simplify. For example,

```math
\frac{8!}{5! \cdot 3!}
```
We can cancel the _5!_ from top and bottom.

That leaves:

```math
\frac{8 \cdot 7 \cdot 6}{3 \cdot 2} = 8 \cdot 7 = 56
```
Doing the full calculation of _8!_ first, it would expand to 40320, a five-digit number and much slower to manipulate than multiplication of two single-digit numbers.

   - You can also commonly cancel common multiplicands.

```math
      \[
      15 \cdot 14 \cdot 13 \cdot 12 \cdot 11 \cdot 10 \ldots
      \]
```
Shares abundant factors from 2 to 9.

Avoid premature canceling of 10, instead pulling 2 from other even numbers, to preserve simple mental math later.

   - Ignore 1s. You can, of course, always ignore the final 1 term in factorials.

4. **Symmetry Property**:
```math
\( \binom{n}{r} = \binom{n}{n - r} \). Use this to reduce the number of calculations when \( r \) is larger than \( \frac{n}{2} \).
```

5. If you know the number of permutations \( P(n,r) \), you can find the number of combinations \( \binom{n}{r} \) by dividing permutations by \( r! \). Every combination will have \( r! \) orderings, so divide that out to get back down to combinations without regard to order.

### Formula Relationship

1. **Permutations**:
    \[
    P(n, r) = \frac{n!}{(n - r)!}
    \]

2. **Combinations**:
    \[
    \binom{n}{r} = \frac{n!}{r!(n - r)!}
    \]

3. The relationship between permutations and combinations is given by:
    \[
    P(n, r) = \binom{n}{r} \cdot r!
    \]

4. To find the number of combinations from permutations:
    \[
    \binom{n}{r} = \frac{P(n, r)}{r!}
    \]

### Sample Word Problems

1. **Concert Lineup (simple combination)**
    - **Problem**: Emily is organizing a music concert and has a lineup of 8 bands. She needs to choose 5 bands to perform. How many different ways can she choose the bands?

2. **Book Club Selection (simple permutation)**
    - **Problem**: A book club has 12 members, and they need to form a ranked committee of three supervisors to organize the next event. How many different committees can be formed?

3. **Sports Team Selection (combination with constraint)**
    - **Problem**: A sports team has 10 players, including 4 seniors. They need to select 6 players to participate in an upcoming match, but at least 1 senior must be included in the selection. How many different ways can the team be selected?

### Combinations with Constraints

If groups require _n_ members of some special subgroup, you have to subtract out each case where the constraint is not met. For example:

**Problem**:

A company has 15 employees, including 5 managers. They need to form a project team of 8 members, but at least 3 members must be managers. How many different ways can the team be formed?

**Approach**:

1. **Total Ways to Choose 8 Members from 15**:
    \[
    \binom{15}{8}
    \]

2. **Subtract Cases with Fewer Than 3 Managers**:
    - **Zero Managers Case**: Total ways to choose 8 members from 10 non-managers.
        \[
        \binom{10}{8}
        \]
    - **One Manager Case**: Choose 1 manager from 5 and the remaining 7 from 10 non-managers.
        \[
        \binom{5}{1} \times \binom{10}{7}
        \]
    - **Two Managers Case**: Choose 2 managers from 5 and the remaining 6 from 10 non-managers.
        \[
        \binom{5}{2} \times \binom{10}{6}
        \]

**Calculations**:

1. **Total Ways to Choose 8 Members from 15**:
    \[
    \binom{15}{8} = \frac{15!}{8! \cdot 7!}
    \]
    Cancel \(8!\):
    \[
    = \frac{15 \cdot 14 \cdot 13 \cdot 12 \cdot 11 \cdot 10 \cdot 9}{7 \cdot 6 \cdot 5 \cdot 4 \cdot 3 \cdot 2}
    \]
    Simplify more like terms:
    \[
    = 13 \cdot 11 \cdot 9 \cdot 5 = 6435
    \]

2. **Zero Managers Case**:
    \[
    \binom{10}{8} = \frac{10!}{8! \cdot 2!} = \frac{10 \cdot 9}{2} = 45
    \]

3. **One Manager Case**:
    \[
    \binom{5}{1} \times \binom{10}{7} = 5 \times \frac{10!}{7! \cdot 3!} = 5 \times \frac{10 \cdot 9 \cdot 8}{3 \cdot 2}
    \]
    Remove like terms, preserve 10s:
    \[
    = 5 \times 10 \times (3 \times 4) = 5 \times 120 = 600
    \]

4. **Two Managers Case**:
    \[
    \binom{5}{2} \times \binom{10}{6} = \left( \frac{5 \cdot 4}{2} \right) \times \frac{10!}{6! \cdot 4!} = 10 \times \frac{10 \cdot 9 \cdot 8 \cdot 7}{4 \cdot 3 \cdot 2}
    \]
    Simplify:
    \[
    = 10 \times 3 \times 7 = 2100
    \]

**Total Valid Teams**:
    \[
    \binom{15}{8} - \left( \binom{10}{8} + \left( \binom{5}{1} \times \binom{10}{7} \right) + \left( \binom{5}{2} \times \binom{10}{6} \right) \right)
    \]

**Putting It All Together**:
    \[
    \binom{15}{8} = 6435
    \]
    \[
    \binom{10}{8} = 45
    \]
    \[
    \binom{5}{1} \times \binom{10}{7} = 600
    \]
    \[
    \binom{5}{2} \times \binom{10}{6} = 2100
    \]

**Subtracting the Invalid Cases**:
    \[
    6435 - (45 + 600 + 2100) = 6435 - 2745 = 3690
    \]

**Conclusion**:

The number of different ways the project team can be formed, ensuring at least 3 managers are included, is 3690.
