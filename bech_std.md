./main -f samples/jfk.wav -m models/ggml-small.bin
whisper_init_from_file_with_params_no_state: loading model from 'models/ggml-small.bin'
whisper_model_load: loading model
whisper_model_load: n_vocab       = 51865
whisper_model_load: n_audio_ctx   = 1500
whisper_model_load: n_audio_state = 768
whisper_model_load: n_audio_head  = 12
whisper_model_load: n_audio_layer = 12
whisper_model_load: n_text_ctx    = 448
whisper_model_load: n_text_state  = 768
whisper_model_load: n_text_head   = 12
whisper_model_load: n_text_layer  = 12
whisper_model_load: n_mels        = 80
whisper_model_load: ftype         = 1
whisper_model_load: qntvr         = 0
whisper_model_load: type          = 3 (small)
whisper_model_load: adding 1608 extra tokens
whisper_model_load: n_langs       = 99
ggml_init_cublas: GGML_CUDA_FORCE_MMQ:   no
ggml_init_cublas: CUDA_USE_TENSOR_CORES: yes
ggml_init_cublas: found 1 CUDA devices:
  Device 0: NVIDIA Tegra X1, compute capability 5.3, VMM: no
whisper_backend_init: using CUDA backend
whisper_model_load:    CUDA0 total size =   487.01 MB
whisper_model_load: model size    =  487.01 MB
whisper_backend_init: using CUDA backend
whisper_init_state: kv self size  =   49.55 MB
whisper_init_state: kv cross size =   55.30 MB
whisper_init_state: compute buffer (conv)   =   22.54 MB
whisper_init_state: compute buffer (encode) =  280.20 MB
whisper_init_state: compute buffer (cross)  =    6.31 MB
whisper_init_state: compute buffer (decode) =   97.40 MB

system_info: n_threads = 4 / 4 | AVX = 0 | AVX2 = 0 | AVX512 = 0 | FMA = 0 | NEON = 1 | ARM_FMA = 1 | METAL = 0 | F16C = 0 | FP16_VA = 0 | WASM_SIMD = 0 | BLAS = 1 | SSE3 = 0 | SSSE3 = 0 | VSX = 0 | CUDA = 1 | COREML = 0 | OPENVINO = 0

main: processing 'samples/jfk.wav' (176000 samples, 11.0 sec), 4 threads, 1 processors, 5 beams + best of 5, lang = en, task = transcribe, timestamps = 1 ...


[00:00:00.000 --> 00:00:11.000]   And so my fellow Americans, ask not what your country can do for you, ask what you can do for your country.


whisper_print_timings:     load time =  2641.59 ms
whisper_print_timings:     fallbacks =   0 p /   0 h
whisper_print_timings:      mel time =    43.99 ms
whisper_print_timings:   sample time =   385.45 ms /   139 runs (    2.77 ms per run)
whisper_print_timings:   encode time =  3786.17 ms /     1 runs ( 3786.17 ms per run)
whisper_print_timings:   decode time =   121.44 ms /     2 runs (   60.72 ms per run)
whisper_print_timings:   batchd time =  5061.58 ms /   135 runs (   37.49 ms per run)
whisper_print_timings:   prompt time =     0.00 ms /     1 runs (    0.00 ms per run)
whisper_print_timings:    total time = 12487.15 ms



./extra/bench-all.sh 4 0
Usage: ./bench.sh [n_threads] [encoder-only]

Running memcpy benchmark

memcpy:    3.33 GB/s (heat-up)
memcpy:    3.38 GB/s ( 1 thread)
memcpy:    3.38 GB/s ( 1 thread)
memcpy:    4.62 GB/s ( 2 thread)
memcpy:    4.93 GB/s ( 3 thread)
memcpy:    5.19 GB/s ( 4 thread)
sum:    783359997189.000000

Running ggml_mul_mat benchmark with 4 threads

ggml_init_cublas: GGML_CUDA_FORCE_MMQ:   no
ggml_init_cublas: CUDA_USE_TENSOR_CORES: yes
ggml_init_cublas: found 1 CUDA devices:
  Device 0: NVIDIA Tegra X1, compute capability 5.3, VMM: no
  64 x   64: Q4_0     0.9 GFLOPS (128 runs) | Q4_1     0.3 GFLOPS (128 runs)
  64 x   64: Q5_0     0.4 GFLOPS (128 runs) | Q5_1     0.3 GFLOPS (128 runs) | Q8_0     0.3 GFLOPS (128 runs)
  64 x   64: F16      0.3 GFLOPS (128 runs) | F32      0.3 GFLOPS (128 runs)
 128 x  128: Q4_0     1.9 GFLOPS (128 runs) | Q4_1     1.3 GFLOPS (128 runs)
 128 x  128: Q5_0     1.5 GFLOPS (128 runs) | Q5_1     1.5 GFLOPS (128 runs) | Q8_0     1.6 GFLOPS (128 runs)
 128 x  128: F16      1.7 GFLOPS (128 runs) | F32      1.6 GFLOPS (128 runs)
 256 x  256: Q4_0     4.0 GFLOPS (119 runs) | Q4_1     4.0 GFLOPS (119 runs)
 256 x  256: Q5_0     4.2 GFLOPS (126 runs) | Q5_1     4.2 GFLOPS (126 runs) | Q8_0     4.1 GFLOPS (123 runs)
 256 x  256: F16      4.2 GFLOPS (125 runs) | F32      5.3 GFLOPS (128 runs)
 512 x  512: Q4_0    27.2 GFLOPS (102 runs) | Q4_1    27.4 GFLOPS (103 runs)
 512 x  512: Q5_0    30.4 GFLOPS (114 runs) | Q5_1    31.6 GFLOPS (118 runs) | Q8_0    30.5 GFLOPS (115 runs)
 512 x  512: F16     38.1 GFLOPS (128 runs) | F32     36.4 GFLOPS (128 runs)
1024 x 1024: Q4_0    94.1 GFLOPS ( 44 runs) | Q4_1   114.7 GFLOPS ( 54 runs)
1024 x 1024: Q5_0   118.1 GFLOPS ( 56 runs) | Q5_1   115.3 GFLOPS ( 54 runs) | Q8_0   119.1 GFLOPS ( 56 runs)
1024 x 1024: F16    116.8 GFLOPS ( 55 runs) | F32    109.0 GFLOPS ( 51 runs)
2048 x 2048: Q4_0   159.5 GFLOPS ( 10 runs) | Q4_1   158.0 GFLOPS ( 10 runs)
2048 x 2048: Q5_0   161.6 GFLOPS ( 10 runs) | Q5_1   160.2 GFLOPS ( 10 runs) | Q8_0   162.3 GFLOPS ( 10 runs)
2048 x 2048: F16    163.6 GFLOPS ( 10 runs) | F32    158.1 GFLOPS ( 10 runs)
4096 x 4096: Q4_0   187.9 GFLOPS (  3 runs) | Q4_1   187.5 GFLOPS (  3 runs)
4096 x 4096: Q5_0   189.1 GFLOPS (  3 runs) | Q5_1   189.9 GFLOPS (  3 runs) | Q8_0   190.0 GFLOPS (  3 runs)
4096 x 4096: F16    189.2 GFLOPS (  3 runs) | F32    187.7 GFLOPS (  3 runs)

Running benchmark for all models
This can take a while!

|    CPU |     OS |           Config |         Model |  Th |    Enc. |    Dec. |    Bch5 |      PP |  Commit |
|    --- |    --- |              --- |           --- | --- |     --- |     --- |     --- |     --- |     --- |
| <todo> | <todo> |   NEON BLAS CUDA |          tiny |   4 |  522.72 |   14.08 |    7.52 |    0.67 | 1558ec5a |
| <todo> | <todo> |   NEON BLAS CUDA |     tiny-q5_1 |   4 |  522.98 |   17.68 |    7.26 |    0.66 | 1558ec5a |
| <todo> | <todo> |   NEON BLAS CUDA |          base |   4 | 1094.38 |   21.97 |   12.85 |    1.17 | 1558ec5a |
| <todo> | <todo> |   NEON BLAS CUDA |     base-q5_1 |   4 | 1097.77 |   29.30 |   12.28 |    1.15 | 1558ec5a |
| <todo> | <todo> |   NEON BLAS CUDA |         small |   4 | 3700.90 |   60.90 |   35.44 |    3.22 | 1558ec5a |
| <todo> | <todo> |   NEON BLAS CUDA |    small-q5_1 |   4 | 3703.90 |   80.71 |   34.02 |    3.19 | 1558ec5a |
