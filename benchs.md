mod cooperative ./scripts/bench-all.sh 4 0 0
Usage: ./bench.sh [n_threads] [encoder-only] [flash-attn]

Running memcpy benchmark

memcpy:    3.72 GB/s (heat-up)
memcpy:    3.72 GB/s ( 1 thread)
memcpy:    3.72 GB/s ( 1 thread)
memcpy:    4.90 GB/s ( 2 thread)
memcpy:    5.10 GB/s ( 3 thread)
memcpy:    5.50 GB/s ( 4 thread)
sum:    783359998621.000000

Running ggml_mul_mat benchmark with 4 threads

  64 x   64: Q4_0     3.0 GFLOPS (128 runs) | Q4_1     2.9 GFLOPS (128 runs)
  64 x   64: Q5_0     2.9 GFLOPS (128 runs) | Q5_1     2.7 GFLOPS (128 runs) | Q8_0     0.3 GFLOPS (128 runs)
  64 x   64: F16      0.7 GFLOPS (128 runs) | F32      0.6 GFLOPS (128 runs)
 128 x  128: Q4_0     4.1 GFLOPS (128 runs) | Q4_1     4.6 GFLOPS (128 runs)
 128 x  128: Q5_0     4.9 GFLOPS (128 runs) | Q5_1     5.2 GFLOPS (128 runs) | Q8_0     4.1 GFLOPS (128 runs)
 128 x  128: F16      4.6 GFLOPS (128 runs) | F32      4.2 GFLOPS (128 runs)
 256 x  256: Q4_0    10.6 GFLOPS (128 runs) | Q4_1    10.1 GFLOPS (128 runs)
 256 x  256: Q5_0     9.4 GFLOPS (128 runs) | Q5_1     8.1 GFLOPS (128 runs) | Q8_0    11.1 GFLOPS (128 runs)
 256 x  256: F16      6.7 GFLOPS (128 runs) | F32     12.6 GFLOPS (128 runs)
 512 x  512: Q4_0    12.0 GFLOPS ( 45 runs) | Q4_1    11.3 GFLOPS ( 42 runs)
 512 x  512: Q5_0    10.4 GFLOPS ( 39 runs) | Q5_1     9.0 GFLOPS ( 34 runs) | Q8_0    12.4 GFLOPS ( 47 runs)
 512 x  512: F16      7.3 GFLOPS ( 28 runs) | F32     10.3 GFLOPS ( 39 runs)
1024 x 1024: Q4_0    12.6 GFLOPS (  6 runs) | Q4_1    11.9 GFLOPS (  6 runs)
1024 x 1024: Q5_0    10.9 GFLOPS (  6 runs) | Q5_1     9.5 GFLOPS (  5 runs) | Q8_0    13.0 GFLOPS (  7 runs)
1024 x 1024: F16      7.5 GFLOPS (  4 runs) | F32      7.9 GFLOPS (  4 runs)
2048 x 2048: Q4_0    12.9 GFLOPS (  3 runs) | Q4_1    12.3 GFLOPS (  3 runs)
2048 x 2048: Q5_0    11.2 GFLOPS (  3 runs) | Q5_1     9.8 GFLOPS (  3 runs) | Q8_0    13.5 GFLOPS (  3 runs)
2048 x 2048: F16      7.7 GFLOPS (  3 runs) | F32      8.0 GFLOPS (  3 runs)
4096 x 4096: Q4_0    13.0 GFLOPS (  3 runs) | Q4_1    12.5 GFLOPS (  3 runs)
4096 x 4096: Q5_0    11.3 GFLOPS (  3 runs) | Q5_1     9.9 GFLOPS (  3 runs) | Q8_0    13.7 GFLOPS (  3 runs)
4096 x 4096: F16      7.6 GFLOPS (  3 runs) | F32      7.7 GFLOPS (  3 runs)

Running benchmark for all models
This can take a while!

|    CPU |     OS |           Config |         Model |  Th |  FA |    Enc. |    Dec. |    Bch5 |      PP |  Commit |
|    --- |    --- |              --- |           --- | --- | --- |     --- |     --- |     --- |     --- |     --- |
| <todo> | <todo> |   NEON BLAS CUDA |          tiny |   4 |   0 |  502.26 |   14.22 |    7.68 |    0.67 | 82203afc |
| <todo> | <todo> |   NEON BLAS CUDA |     tiny-q5_1 |   4 |   0 |  500.92 |   19.35 |    7.28 |    0.67 | 82203afc |
| <todo> | <todo> |   NEON BLAS CUDA |          base |   4 |   0 | 1047.88 |   22.24 |   12.92 |    1.16 | 82203afc |
| <todo> | <todo> |   NEON BLAS CUDA |     base-q5_1 |   4 |   0 | 1048.36 |   31.57 |   12.23 |    1.15 | 82203afc |
| <todo> | <todo> |   NEON BLAS CUDA |         small |   4 |   0 | 3554.22 |   60.95 |   35.94 |    3.21 | 82203afc |
| <todo> | <todo> |   NEON BLAS CUDA |    small-q5_1 |   4 |   0 | 3557.15 |   85.85 |   34.08 |    3.17 | 82203afc |
| <todo> | <todo> |   NEON BLAS CUDA |        medium |   4 |   0 |      ms |  168.00 |   96.69 |    8.81 | 82203afc |
| <todo> | <todo> |   NEON BLAS CUDA |   medium-q5_0 |   4 |   0 |      ms |  222.36 |   90.77 |    8.70 | 82203afc |
usr1@ubuntu:~/coding/whisper.cpp$ 

usr1@ubuntu:~/coding/whisper.cpp$ ./main -f samples/jfk.wav -m models/ggml-small.bin
whisper_init_from_file_with_params_no_state: loading model from 'models/ggml-small.bin'
whisper_init_with_params_no_state: use gpu    = 1
whisper_init_with_params_no_state: flash attn = 0
whisper_init_with_params_no_state: gpu_device = 0
whisper_init_with_params_no_state: dtw        = 0
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
whisper_backend_init: using CUDA backend
ggml_cuda_init: GGML_CUDA_FORCE_MMQ:   no
ggml_cuda_init: CUDA_USE_TENSOR_CORES: yes
ggml_cuda_init: found 1 CUDA devices:
  Device 0: NVIDIA Tegra X1, compute capability 5.3, VMM: no
whisper_model_load:    CUDA0 total size =   487.01 MB
whisper_model_load: model size    =  487.01 MB
whisper_backend_init: using CUDA backend
whisper_init_state: kv self size  =   56.62 MB
whisper_init_state: kv cross size =   56.62 MB
whisper_init_state: kv pad  size  =    4.72 MB
whisper_init_state: compute buffer (conv)   =   22.54 MB
whisper_init_state: compute buffer (encode) =  280.20 MB
whisper_init_state: compute buffer (cross)  =    6.31 MB
whisper_init_state: compute buffer (decode) =   97.40 MB

system_info: n_threads = 4 / 4 | AVX = 0 | AVX2 = 0 | AVX512 = 0 | FMA = 0 | NEON = 1 | ARM_FMA = 1 | METAL = 0 | F16C = 0 | FP16_VA = 0 | WASM_SIMD = 0 | BLAS = 1 | SSE3 = 0 | SSSE3 = 0 | VSX = 0 | CUDA = 1 | COREML = 0 | OPENVINO = 0

main: processing 'samples/jfk.wav' (176000 samples, 11.0 sec), 4 threads, 1 processors, 5 beams + best of 5, lang = en, task = transcribe, timestamps = 1 ...


[00:00:00.000 --> 00:00:11.000]   And so my fellow Americans, ask not what your country can do for you, ask what you can do for your country.


whisper_print_timings:     load time =  1633.48 ms
whisper_print_timings:     fallbacks =   0 p /   0 h
whisper_print_timings:      mel time =    42.23 ms
whisper_print_timings:   sample time =   420.67 ms /   139 runs (    3.03 ms per run)
whisper_print_timings:   encode time =  4976.15 ms /     1 runs ( 4976.15 ms per run)
whisper_print_timings:   decode time =   120.17 ms /     2 runs (   60.08 ms per run)
whisper_print_timings:   batchd time =  5075.35 ms /   135 runs (   37.60 ms per run)
whisper_print_timings:   prompt time =     0.00 ms /     1 runs (    0.00 ms per run)
whisper_print_timings:    total time = 12793.65 ms
usr1@ubuntu:~/coding/whisper.cpp$ 
