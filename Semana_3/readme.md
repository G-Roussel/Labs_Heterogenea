# Lab 2 — Multiplicación de Matrices (Scalar vs AVX2)

## Archivos
- matmul_scalar.c
- matmul_avx2.c

## Intel Intrinsics Guide (AVX2)
https://www.intel.com/content/www/us/en/docs/intrinsics-guide/index.html#techs=AVX2

## Funciones agregadas en versión AVX2

### Carga
static inline __m256 simd_loadu_ps(const float *values)
{
    return _mm256_loadu_ps(values);
}

### Multiplicación
static inline __m256 simd_mul_ps(__m256 a, __m256 b)
{
    return _mm256_mul_ps(a, b);
}

### Reducción horizontal
static inline float simd_reduce_add_ps(__m256 value)
{
    __m128 low  = _mm256_extractf128_ps(value, 0);
    __m128 high = _mm256_extractf128_ps(value, 1);
    __m128 sum = _mm_add_ps(low, high);
    sum = _mm_hadd_ps(sum, sum);
    sum = _mm_hadd_ps(sum, sum);
    return _mm_cvtss_f32(sum);
}

### Producto punto AVX2
float dot_product_avx2(const float a[VECTOR_SIZE], const float b[VECTOR_SIZE])
{
    float result = 0.0f;
    for (int i = 0; i < VECTOR_SIZE; i += AVX_FLOATS) {
        __m256 a_vec = simd_loadu_ps(&a[i]);
        __m256 b_vec = simd_loadu_ps(&b[i]);
        __m256 product = simd_mul_ps(a_vec, b_vec);
        result += simd_reduce_add_ps(product);
    }
    return result;
}

## Resultados

### Scalar (2048×2048, rep=1)
Tiempo: 20.385959 s  
GFLOP/s: 0.842730  
Checksum: 86972906452.000000  
C[0][0]: 26800.500000  
C[1023][1023]: 26836.500000  

### AVX2 (2048×2048, rep=1)
Tiempo: 4.727659 s  
GFLOP/s: 3.633906  
Checksum: 86972906452.000000  
C[0][0]: 26800.500000  
C[1023][1023]: 26836.500000  

### Comparativa
| Versión | Tiempo (s) | GFLOP/s | Speedup |
|--------|------------|---------|---------|
| Scalar | 20.385959  | 0.842730 | 1× |
| AVX2   | 4.727659   | 3.633906 | 4.31× |

## Cálculo de operaciones
FLOPs = 2 * N^3 = 17179869184  
GFLOP/s = FLOPs / tiempo / 1e9  

## Compilación
gcc -O3 matmul_scalar.c -o matmul_scalar  
gcc -O3 -mavx2 matmul_avx2.c -o matmul_avx2  
