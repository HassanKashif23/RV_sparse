# RV_sparse
RV-Sparse Coding Challenge: Sparse Matrix Multiplication using CSR

# RV-Sparse: Sparse Matrix Multiplication using CSR

## Overview
This project implements a sparse matrix-vector multiplication using Compressed Sparse Row (CSR) format in C.

Given a dense matrix A and vector x, the program:
1. Extracts non-zero elements of A into CSR format
2. Computes y = A * x using the CSR representation

## Key Features
- CSR (Compressed Sparse Row) representation
- Efficient sparse matrix-vector multiplication
- No dynamic memory allocation (all buffers pre-allocated by caller)
- Works with random sparse matrices of varying size and density

## Implementation Details

The CSR format consists of:
- values[]: stores non-zero elements of matrix A
- col_indices[]: stores column index of each value
- row_ptrs[]: stores starting index of each row in values[]

Matrix-vector multiplication is performed using:
for each row i:
    sum = Σ (values[k] * x[col_indices[k]])
    for k in row_ptrs[i] to row_ptrs[i+1]

## Constraints
- No malloc/calloc/free used
- All memory is managed by caller (test harness)
- Works on double precision floating point values

## Build & Run
```bash
gcc challenge.c -o run -lm
./run
