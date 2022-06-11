#### Run libfuzzer_libxml_kscheduler
1. Open a terminal to run fuzzer:
    ```sh
    cd [path to K-Scheduler_llvm14_Benchmark repo]/libxml/kscheduler 
    # clean fuzzer corpus and other meta data generated by fuzzer
    rm -rf tmp_seeds/ cov_stats cur_coverage dyn_katz_cent 
    mkdir tmp_seeds
    # reset signal file for graph computation module
    echo 0 > signal
    # run libfuzzer_kscheduler
    ./xml -entropic=0 -kscheduler=1 -dict=xml.dict ./tmp_seeds/ seeds/
    ```
2. Open another terminal to run graph computation module:
    ```sh
    python3 ./gen_dyn_weight.py
    ```

#### Run libfuzzer_libxml_entropic
1. Open a terminal to run fuzzer:
    ```sh
    cd [path to K-Scheduler_llvm14_Benchmark repo]/libxml/entropic 
    # clean fuzzer corpus and other meta data generated by fuzzer
    rm -rf tmp_seeds/ cov_stats  
    mkdir tmp_seeds
    # run libfuzzer_entropic
    ./xml -entropic=1 -dict=xml.dict ./tmp_seeds/ seeds/
    ```

#### Run libfuzzer_libxml_vanilla
1. Open a terminal to run fuzzer:
    ```sh
    cd [path to K-Scheduler_llvm14_Benchmark repo]/libxml/vanilla 
    # clean fuzzer corpus and other meta data generated by fuzzer
    rm -rf tmp_seeds/ cov_stats  
    mkdir tmp_seeds
    # run libfuzzer_entropic
    ./xml -entropic=0 -dict=xml.dict ./tmp_seeds/ seeds/
    ```