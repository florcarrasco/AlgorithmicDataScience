# Similarity Algorithms Analysis

## Overview

This repository contains an analysis of various similarity algorithms and their performance under different scenarios. The project explores the implementation and impact of algorithmic optimizations on time complexity, with a specific focus on **Cosine Similarity** and **Jaccard Similarity**. Additionally, advanced computational techniques such as parallel computing and the **Strassen method of matrix multiplication** are utilized to enhance performance for large-scale data.

The report aims to empirically validate theoretical time complexities while showcasing practical implementations that improve efficiency for similarity computations.

---

## Key Objectives

1. **Evaluate Similarity Algorithms**:
   - Analyze the performance of Cosine and Jaccard similarity algorithms on datasets of varying sizes and configurations.
   - Compare theoretical time complexities with empirical results.

2. **Algorithm Optimization**:
   - Demonstrate performance improvements using:
     - NumPy's optimized linear algebra operations.
     - Parallel computing via Python’s `multiprocessing` library.
     - Strassen’s method for matrix multiplication.

3. **Practical Application**:
   - Highlight the suitability of these algorithms for large-scale similarity computations across datasets, such as document comparison or vector analysis.

---

## Features

### 1. **Similarity Algorithms**
- **Cosine Similarity**:
  - Measures the cosine of the angle between two vectors.
  - Implemented in both a traditional Python function and an optimized version using NumPy’s dot product for faster calculations.
  
- **Jaccard Similarity**:
  - Compares the intersection and union of two datasets (treated as lists).
  - Ideal for set-based similarity but implemented using lists for this project due to specific requirements.

### 2. **All-Pair Similarity**
- Extends similarity computations to all pairs of vectors in a dataset.
- Time complexities are validated empirically to demonstrate the growth in computational cost for increasing dataset sizes.

### 3. **Parallel Computing**
- Utilizes Python’s `multiprocessing` to distribute similarity calculations across multiple cores.
- Demonstrates significant runtime improvements for large datasets by leveraging parallelization.

### 4. **Strassen’s Method for Matrix Multiplication**
- Applies Strassen’s algorithm to improve the efficiency of Cosine Similarity calculations for square matrices.
- Shows measurable performance gains over traditional matrix multiplication.

---

## Methodology

1. **Theoretical and Empirical Validation**:
   - Each similarity algorithm is analyzed to determine its theoretical time complexity (e.g., \(O(n)\) for Cosine and Jaccard Similarity).
   - Empirical results (mean and standard deviation of runtimes) are calculated by repeatedly executing the algorithms on subsets of the data.

2. **Performance Benchmarking**:
   - Custom benchmarking functions (`timeit`) are used to measure execution times for various algorithms and optimizations.
   - Log-log plots and regression analyses are generated to evaluate slopes and constants for the time complexity equations.

3. **Optimization Techniques**:
   - **NumPy Implementation**: Replacing custom implementations with NumPy for faster linear algebra operations.
   - **Parallel Computing**: Distributing calculations across multiple processes to reduce runtime.
   - **Strassen’s Method**: Leveraging Strassen's algorithm for faster matrix multiplication in large datasets.

---

## Results

### Algorithm Performance
- **Cosine Similarity**:
  - Achieves a slope of ~0.99 for its time complexity, consistent with \(O(n)\).
  - NumPy optimizations further reduced runtime, with a higher constant (~\(2.84 \times 10^{-5}\)).
  
- **Jaccard Similarity**:
  - Exhibits a slope of ~0.98, aligning with \(O(n)\). Its implementation via list comprehension maintains linear growth without nested loops.

### All-Pair Similarity
- Empirical results confirmed quadratic growth (\(O(n^2)\)) for all-pair similarity computations due to nested loops over all vector pairs.
- Slope for **Cosine Similarity**: ~3.33; Constant: ~\(5.41 \times 10^{-6}\).
- Slope for **Jaccard Similarity**: ~3.23; Constant: ~\(5.39 \times 10^{-6}\).

### Parallel Computing
- Parallelized computations demonstrated significant runtime reductions, with an optimal performance observed at **21 cores**.

### Strassen’s Method
- Applying Strassen’s method for matrix multiplication reduced runtime for large datasets. 
  - **Cosine Similarity with Strassen**: ~250 seconds for the largest matrix.
  - **Traditional Cosine Similarity**: ~400 seconds for the same matrix.

---

## Conclusion

This repository demonstrates how thoughtful algorithm design and implementation can significantly impact computational efficiency. Key findings include:
- **Cosine Similarity** is faster and more efficient than **Jaccard Similarity** for large datasets.
- Leveraging optimizations like **NumPy**, **parallel computing**, and **Strassen’s method** can improve runtime dramatically.
- Empirical validation of theoretical complexities provides insights into the scalability of these algorithms for real-world applications.

---

## Repository Contents

- **`similarity_algorithms.py`**: Implementation of Cosine and Jaccard similarity functions.
- **`all_pair_similarity.py`**: Code for computing all-pair similarities.
- **`parallel_computing.py`**: Multiprocessing implementation for similarity calculations.
- **`strassen_cosine.py`**: Strassen method applied to Cosine Similarity.
- **`plots/`**: Visualizations of performance benchmarks.
- **`data/`**: Example datasets used for testing and analysis.

---

## Future Work
* Investigate additional similarity metrics, such as Euclidean distance and Hamming similarity.
* Extend optimizations to include GPU-based parallelization for even faster computations.
* Apply these methods to real-world datasets in fields like recommendation systems and natural language processing.
This repository serves as a resource for understanding and implementing efficient similarity algorithms and demonstrates the power of computational optimization for large-scale data analysis.
