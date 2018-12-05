TODO: very WIP

## Challenges

1. There is no batched GEMM in OpenBLAS
2. BLIS and cublas strided GEMM supports arbitrary strides which avoids a copy to a contiguous tensor.
   but neither MKL or OpenBLAS supports it. Arbitrary strides are resolved during packing.
3. In deep learning, GEMMs and convolutions (which often use GEMM) are always followed by a non-linear activation which is memory-bound. Allowing non-linearity + GEMM fusion would probably increase throughput tremendously.

## Small GEMMs

- https://github.com/hfp/libxsmm
- High-Performance Matrix-Matrix Multiplications of
Very Small Matrices
    - https://hal.archives-ouvertes.fr/hal-01409286/document
- BLASFEO: basic linear algebra subroutines for embedded optimization
    - https://arxiv.org/pdf/1704.02457.pdf
    - https://github.com/giaf/blasfeo

## Links

- https://www.codeproject.com/Articles/1169319/Reducing-Packing-Overhead-in-Matrix-Matrix-Multipl
- https://www.icl.utk.edu/files/publications/2017/icl-utk-1032-2017.pdf
- https://devblogs.nvidia.com/cutlass-linear-algebra-cuda/
- Automatic Generation of Fast BLAS3-GEMM:
A Portable Compiler Approach,
    - http://www.cse.unsw.edu.au/~jingling/papers/cgo17.pdf
- http://www.cs.utexas.edu/users/flame/pubs/bamarker_thesis.pdf