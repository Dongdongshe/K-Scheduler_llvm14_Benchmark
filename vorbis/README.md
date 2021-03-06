#### Run libfuzzer_vorbis_kscheduler
1. Open a terminal to run fuzzer:
    ```sh
    cd [path to K-Scheduler_llvm14_Benchmark repo]/vorbis/kscheduler 
    # clean fuzzer corpus and other meta data generated by fuzzer
    rm -rf tmp_seeds/ cov_stats cur_coverage dyn_katz_cent 
    mkdir tmp_seeds
    # reset signal file for graph computation module
    echo 0 > signal
    # run libfuzzer_kscheduler
    ./decode_fuzzer -entropic=0 -kscheduler=1 ./tmp_seeds/ seeds/
    ```
2. Open another terminal to run graph computation module:
    ```sh
    python3 ./gen_dyn_weight.py
    ```

#### Run libfuzzer_vorbis_entropic
1. Open a terminal to run fuzzer:
    ```sh
    cd [path to K-Scheduler_llvm14_Benchmark repo]/vorbis/entropic 
    # clean fuzzer corpus and other meta data generated by fuzzer
    rm -rf tmp_seeds/ cov_stats  
    mkdir tmp_seeds
    # run libfuzzer_entropic
    ./decode_fuzzer -entropic=1 ./tmp_seeds/ seeds/
    ```

#### Run libfuzzer_vorbis_vanilla
1. Open a terminal to run fuzzer:
    ```sh
    cd [path to K-Scheduler_llvm14_Benchmark repo]/vorbis/vanilla 
    # clean fuzzer corpus and other meta data generated by fuzzer
    rm -rf tmp_seeds/ cov_stats  
    mkdir tmp_seeds
    # run libfuzzer_entropic
    ./decode_fuzzer -entropic=0 ./tmp_seeds/ seeds/
    ```
