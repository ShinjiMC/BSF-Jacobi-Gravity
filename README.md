# BSF Implementation Test

By Braulio Nayap Maldonado Casilla of DEXO Corp.

## Overview

This repository contains the source codes for two parallel implementations using the BSF-skeleton in C++:

1. **Jacobi Method Implementation**  
   A parallel implementation of the iterative Jacobi method for solving systems of linear algebraic equations using higher-order functions Map and Reduce.

   GitHub Repository: [BSF-Jacobi](https://github.com/leonid-sokolinsky/BSF-Jacobi)

2. **Gravity Problem Implementation**  
   A parallel implementation of an iterative algorithm solving a simplified n-body problem, describing how a small body moves under the influence of gravitational forces from large, stationary bodies.

   GitHub Repository: [BSF-Gravity](https://github.com/leonid-sokolinsky/BSF-gravity)

Both implementations are based on the BSF-skeleton framework. For detailed documentation on BSF-skeleton, visit its [GitHub repository](https://github.com/leonid-sokolinsky/BSF-skeleton).

## Compilation and Execution

To compile the programs, use the following commands:

### Jacobi Method

```bash
cd JacobiMR
mpic++ -o BSF_Jacobi BSF-Code.cpp Problem-bsfCode.cpp Problem-Forwards.h Problem-Data.h
```

Run the compiled program with the desired number of nodes:

```bash
mpirun -np <number_of_nodes> ./BSF_Jacobi
```

### Gravity Method

```bash
cd Gravity
mpic++ -o BSF_Gravity BSF-Code.cpp Problem-bsfCode.cpp Problem-Forwards.h Problem-Data.h
```

Run the compiled program with the desired number of nodes:

```bash
mpirun -np <number_of_nodes> ./BSF_Gravity
```

## Customization for Data Size and Output

### Jacobi Method

To modify data size and enable terminal output, edit `Problem-Parameters.h`:

- Increase this value for larger datasets:

  ```c++
  #define PP_N 1500
  ```

- Modify these lines to enable terminal prints:
  ```c++
  // #define PP_MAX_ITER_COUNT 10
  // #define PP_MATRIX_OUTPUT
  #define PP_OUTPUT_LIMIT 0
  ```

### Gravity Method

To modify data size and enable terminal output, edit `Problem-Parameters.h`:

- Increase this value for larger datasets:

  ```c++
  #define PP_NUNBER_OF_LARGE_MASS_POINTS_PER_DIMENSION 500
  ```

- Modify these lines to enable terminal prints:
  ```c++
  // #define PP_LARGE_MASS_POINTS_OUTPUT
  #define PP_OUTPUT_LIMIT 0
  ```

Additionally, edit `Problem-bsfParameters.h` to enable iteration output:

```c++
// #define PP_BSF_ITER_OUTPUT
```

## Credits

All credits for the BSF-skeleton and algorithmic implementations go to:

**Leonid B. Sokolinsky**

For more details, refer to the associated paper: [arXiv:2008.03485](https://arxiv.org/abs/2008.03485).
