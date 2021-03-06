# FifoIPCBenchmarkData

This git repo contains data gathered for various CPUs by the FifoIPCBenchmark benchmarking tool.

## About

This data for the AMD Ryzen 9 5950Xm AMD EPYC 7763, and Intel Xeon Platinum 8380 was gathered on bare metal severs. The data for the AMD EPYC 7R32, Amazon Graviton2, Intel Xeon Platinum 8124M, Intel Xeon Platinum 8252C, and Intel Xeon Platinum 8259CL were gathered through metal instances on Amazon Web Services.

For these experiments, the compiler used was `gcc-10` with the c++20 starndard. The benchmark was compiled in release mode.

The latency data was gathered by running setting the CPU governor to performance when applicable and running the benchmark with

```shell
sudo ./fifo-ipc-latency
```
and
```shell
sudo ./fifo-ipc-latency -i --cores 0
```

The throughput measurements running the executable `./fifo-ipc-throughput` with appropriate flags for the inidividual processors.

## Usage

To visualize this data, you can use the python scripts available in the `python` directory of the [FifoIPCBenchmark](https://github.com/AndreaBaretta/FifoIPCBenchmark) project. To see a heatmap of the latency data for a particular CPU, run
```shell
python3 /python/heatmap_avg.py ~/git/FifoIPCBenchmarkData/<CPU name>/data
```
To see the empirical cumulative density plot of the latency data of individual messages between two cores, run
```shell
python3 /python/dist_individual.py ~/git/FifoIPCBenchmarkData/<CPU name>/data
```
To specify the cores you are analyzing, you must edit the `cores` variable inside of `dist_individual.py`.

To visualize the distribution of throughput data, run:
```shell
python3 /python/throughput_plot.py ~/git/FifoIPCBenchmarkData/<CPU name>/data
```

## Disclaimer

    FifoIPCBenchmarkData is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

## Authors

[Andrea Baretta](https://github.com/AndreaBaretta)

Copyright © 2021 Andrea Baretta