#### Run libfuzzer_lcms_kscheduler
1. Open a terminal to run fuzzer:
    ```sh
    cd [path to K-Scheduler_llvm14_Benchmark repo]/lcms/kscheduler 
    # clean fuzzer corpus and other meta data generated by fuzzer
    rm -rf tmp_seeds/ cov_stats cur_coverage dyn_katz_cent 
    mkdir tmp_seeds
    # reset signal file for graph computation module
    echo 0 > signal
    # run libfuzzer_kscheduler
    ./cms_transform_fuzzer -entropic=0 -kscheduler=1 -dict=cms_transform_fuzzer.dict ./tmp_seeds/ seeds/
    ```
2. Open another terminal to run graph computation module:
    ```sh
    python3 ./gen_dyn_weight.py
    ```

#### Run libfuzzer_lcms_entropic
1. Open a terminal to run fuzzer:
    ```sh
    cd [path to K-Scheduler_llvm14_Benchmark repo]/lcms/entropic 
    # clean fuzzer corpus and other meta data generated by fuzzer
    rm -rf tmp_seeds/ cov_stats  
    mkdir tmp_seeds
    # run libfuzzer_entropic
    ./cms_transform_fuzzer -entropic=1 -dict=cms_transform_fuzzer.dict ./tmp_seeds/ seeds/
    ```

#### Run libfuzzer_lcms_vanilla
1. Open a terminal to run fuzzer:
    ```sh
    cd [path to K-Scheduler_llvm14_Benchmark repo]/lcms/vanilla 
    # clean fuzzer corpus and other meta data generated by fuzzer
    rm -rf tmp_seeds/ cov_stats  
    mkdir tmp_seeds
    # run libfuzzer_entropic
    ./cms_transform_fuzzer -entropic=0 -dict=cms_transform_fuzzer.dict ./tmp_seeds/ seeds/
    ```
