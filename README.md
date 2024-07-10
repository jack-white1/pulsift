```
    .          .     .     *        .   .   .     .
         ___________      . __ .  .   *  .   .  .  .     .
    . *   _____  __ \__+ __/ /_____________ _____ .    *  .
  +    .   ___  /_/ / / / / / ___/ ___/ __ `/ __ \     + .
 .          _  ____/ /_/ / (__  ) /__/ /_/ / / / / .  *     . 
       .    /_/ *  \__,_/_/____/\___/\__,_/_/ /_/    
    *    +     .     .     . +     .     +   .      *   +

    J. White, K. Adámek, J. Roy, S. Ransom, W. Armour  2023
```

# Pulscan

Pulscan is a high-performance pulsar searching tool that can run on GPUs, CPUs and hybrid CPU/GPU systems such as NVIDIA Grace Hopper, making use of both CPU and GPU resources for different sections of the pipeline. Pulscan performs an acceleration search for the signature of binary pulsars using boxcar filters on FFT magnitude spectra. 

The input data is expected to be in .fft format, which can be produced using PRESTO's `realfft` program.

An .fft file is a binary file consisting of an even number of FP32 floats, where each pair represents the real and complex component of a single bin of an FFT spectrum. The first pair of floats represents the DC, or zero frequency component of the signal. The final pair of numbers should be the frequency component corresponding to sampling_frequency/2.

## Prerequisites

- GCC compiler for C code compilation
- OpenMP for parallel computing on the CPU
- NVIDIA CUDA Toolkit for compiling and running GPU and hybrid codes


## Installation

Clone the Pulscan repository to your local machine and run ```make all```:

```bash
git clone https://github.com/jack-white1/pulscan
cd pulscan
make all
```

If you just want the CPU version:

```bash
make cpu
```

If you just want the GPU version:

```bash
make gpu
```

## Usage

### Running the hybrid CPU/GPU version

```bash
./pulscan_hybrid sample_data/test_data.fft -tobs 602.112
```

### Running the GPU version

```bash
./pulscan_gpu sample_data/test_data.fft
```

### Running the CPU version

```bash
./pulscan sample_data/test_data.fft -tobs 602.112
```

### Getting help

Run the following to get a list and explanation of available options:

```bash
./pulscan
```

If you have any other questions: jack.white at eng.ox.ac.uk