# Constraints Satisfaction Problems

> Standard Search Problems vs CSPs
>
> - **Standard Search Problems**:
>   - State is a "black box". i.e., algorithm is state independent.
>   - Algorithm uses problem-specific functions to access the state. e.g., `successors`, `actions`, `goal_test`.
> - **CSPs**:
>   - State and goal test follows a standard form.
>   - Uses general-purpose heuristics that works with any CSP.

## Definitions

- A CSP is defined by:
  - A set of variables `X[i]`.
  - A domain `D[i]` for each variable `X[i]`.
  - A set of constraints that specify allowable combinations of values.
    - Each constraint involves some subset of the variables.
    - E.g. $\langle(X_1, X_2), X_1 > X_2\rangle$
- **Consistent Assignment**: An assignment that does not violate any constraints.
- **Complete Assignment**: An assignment that includes all variables.
- **Solution**: A consistent and complete assignment.

## Advantages

- **Modelling**: CSPs are a natural way to model many problems.
- **Structure Exploitation**:
  - CSPs can be solved more efficiently than general search problems.
  - E.g. Large portions of the search space can be eliminated by considering constraints.

## Variants

### Type of Variables

- **Discrete Variables**: 
  -  **Finite Domains**: E.g. Boolean
  - **Infinite Domains**: E.g. Integers
- **Continuous Variables**: E.g. Real numbers (time, distance).
  - Needs linear programming or other techniques.

### Type of Constraints

- **Unary Constraints**: Involves a single variable.
- **Binary Constraints**: Involves two variables.
- **Global Constraints**: Involves arbitrary number of variables.

## Algorithms

- Typically using, hill climbing, simulated annealing, or other local search algorithms.
- **Initial state**: Assign a value to each variable. (e.g. randomly)
- **Successor function**: Change the value of a single variable.
  - **Variable Selection**: Choose a variable to change.
  - **Value Selection**: Choose a value for the variable.
    - E.g. using `min-conflicts` heuristic. (Choose the value that violates the fewest constraints.)

```python
def min_conflicts(csp, max_steps):
    # Initialize with a random complete assignment
    current = {}
    for var in csp.variables:
        current[var] = random.choice(csp.domains[var])

    for i in range(max_steps):
        if csp.is_solution(current):
            return current

        # Choose a random conflicted variable
        conflicted_var = random.choice(csp.get_conflicted_vars(current))

        # Find the value that minimizes conflicts
        best_value, min_conflicts = None, float('inf')
        for value in csp.domains[conflicted_var]:
            num_conflicts = csp.num_conflicts(conflicted_var, value, current)
            if num_conflicts < min_conflicts:
                best_value, min_conflicts = value, num_conflicts

        # Assign the best value to the variable
        current[conflicted_var] = best_value

    return None  # Failed to find a solution within max_steps
```
