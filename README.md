# *HSCA*: Towards High-strength Combinatorial Interaction Testing for Highly Configurable Software Systems

*HSCA* is a novel and effective algorithm for solving high-strength CCAG problem.
This repository includes the implementation of *HSCA*, the testing instances adopted in the experiments and the experimental results.

## How to Obtain *HSCA*

*HSCA* is [publicly available on Github](https://github.com/hsca-submission/HSCA). To obtain *HSCA*, a user may use `git clone` to get a local copy of the Github repository:

```
git clone https://github.com/hsca-submission/HSCA.git
```

## Instructions for Building *HSCA*

```
sh build.sh
```

By executing this script file, users can build both *SamplingCA* and *HSCA*. Note that both *SamplingCA* and *HSCA* should be built on a 64-bit GNU/Linux operating system.

**Tip**: Both *SamplingCA* and *HSCA* depend on *MiniSAT*, but *MiniSAT* may not compile successfully when using specific versions of gcc. In this case, users may seek for solutions on the Internet or in the Github page of [MiniSAT](https://github.com/niklasso/minisat).

## Instructions for Running *HSCA*

We provide a Python script `run.py` for users to run *HSCA* in an end-to-end manner. That is, by executing this Python script, users can obtain a 2-wise CA which is initially constructed by *SamplingCA*. Subsequently, a t-wise CA is produced through *HSCA*'s multi-round CA generation mechanism, which is then compressed through *HSCA*'s optimization approach.

**Note**: For running *SamplingCA* separately, users may refer to the instructions in [generate/SamplingCA/README.md](https://github.com/hsca-submission/HSCA/tree/main/generate/SamplingCA/README.md). For running *HSCA* separately, users may refer to the instructions in the above section.

The usage of `run.py` is as follows.
```
python3 run.py [MODEL_FILE] [CONSTRAINTS_FILE] <optional_parameters>
```

For the required parameters, we list them as follows. 

| Parameter | Allowed Values | Description |
| - | - | - |
| MODEL_FILE | string | path of the model file of the input instance |
| CONSTRAINTS_FILE | string | path of the constraint file of the input instance |

For the optional parameters, we list them as follows.

| Parameter | Allowed Values | Default Value | Description | 
| - | - | - | - |
| `-seed` | integer | 1 | random seed |
| `-use_group` | 0 or 1 | 1 | whether to use variable grouping strategy |
|  `-use_priority` | 0 or 1 | 1 | whether to use dynamic priority assigning technique |
| `-L` | positive integer | 5000 | used to control the termination criterion the first pass of *HSCA*'s optimization approach |
| `-cutoff_time` | positive integer | 1000 | used to control the termination criterion the second pass of *HSCA*'s optimization approach |

## Example Command for Running *HSCA*

An example of running `run.py`:
```
python3 run.py benchmarks/real-world/spins_4wise.model benchmarks/real-world/spins.constraints -seed 1
```

The command above calls *HSCA* to solve the instance `benchmarks/real-world/spins_4wise.model` with default hyper-parameter setting (L = 5,000). And here *HSCA* use the random seed of 1.

## Implementation of *HSCA*

The directory named `format_converter/` includes the implementation of model flattening 、.

The directory named `generate/` includes the implementation of multi-round CA generation mechanism and the first pass of the optimization approach.

The directory named `optimize/` includes the implementation of the second pass of the optimization approach.

## Testing Benchmarks for Evaluating *HSCA*

The directory named `benchmarks/real-world` contains all 5 real-world testing benchmarks and the directory named `benchmarks/synthetic` contains all 30 synthetic instances. We also provide `benchmark_information.csv` which shows the number of options and the number of constraints for each benchmark.

## Empirical Study on Measuring the t-wise Coverage of (t-1)-wise Covering Array

The experimental design and detailed results of the empirical study on measuring the t-wise coverage of (t-1)-wise covering array is available at:
[Empirical_Study.pdf](https://github.com/hsca-submission/HSCA/blob/main/Empirical_Study.pdf)

## Experimental Results

The directory `experimental_results/` contains 9 `.csv` files for presenting the experimental results.

+ [Results_of_HSCA_and_its_SOTA_competitors_on_2wise_CCAG.csv](https://github.com/hsca-submission/HSCA/blob/main/experimental_results/Results_of_HSCA_and_its_SOTA_competitors_on_2wise_CCAG.csv): Results of *HSCA* and its state-of-the-art competitors on all testing instance for 2-wise CCAG problem.

+ [Results_of_HSCA_and_its_SOTA_competitors_on_3wise_CCAG.csv](https://github.com/hsca-submission/HSCA/blob/main/experimental_results/Results_of_HSCA_and_its_SOTA_competitors_on_3wise_CCAG.csv): Results of *HSCA* and its state-of-the-art competitors on all testing instance for 3-wise CCAG problem.

+ [Results_of_HSCA_and_its_SOTA_competitors_on_4wise_CCAG.csv](https://github.com/hsca-submission/HSCA/blob/main/experimental_results/Results_of_HSCA_and_its_SOTA_competitors_on_4wise_CCAG.csv): Results of *HSCA* and its state-of-the-art competitors on all testing instance for 4-wise CCAG problem.

+ [Results_of_HSCA_and_its_SOTA_competitors_on_5wise_CCAG.csv](https://github.com/hsca-submission/HSCA/blob/main/experimental_results/Results_of_HSCA_and_its_SOTA_competitors_on_5wise_CCAG.csv): Results of *HSCA* and its state-of-the-art competitors on all testing instance for 5-wise CCAG problem.

+ [Results_of_HSCA_and_its_SOTA_competitors_on_6wise_CCAG.csv](https://github.com/hsca-submission/HSCA/blob/main/experimental_results/Results_of_HSCA_and_its_SOTA_competitors_on_6wise_CCAG.csv): Results of *HSCA* and its state-of-the-art competitors on all testing instance for 6-wise CCAG problem.

+ [Results_of_HSCA_and_its_alternative_versions_on_4wise_CCAG](https://github.com/hsca-submission/HSCA/blob/main/experimental_results/Results_of_HSCA_and_its_alternative_versions_on_4wise_CCAG.csv): Results of *HSCA* and its alternative versions on all testing instance for 4-wise CCAG problem.

+ [Results_of_HSCA_and_its_alternative_versions_on_5wise_CCAG](https://github.com/hsca-submission/HSCA/blob/main/experimental_results/Results_of_HSCA_and_its_alternative_versions_on_5wise_CCAG.csv): Results of *HSCA* and its alternative versions on all testing instance for 5-wise CCAG problem.

+ [Results_of_HSCA_with_different_L_settings_on_4wise_CCAG](https://github.com/hsca-submission/HSCA/blob/main/experimental_results/Results_of_HSCA_with_different_L_settings_on_4wise_CCAG.csv): Results of *HSCA* with different $L$ settings on all testing instance for 4-wise CCAG problem.

+ [Results_of_HSCA_with_different_L_settings_on_5wise_CCAG](https://github.com/hsca-submission/HSCA/blob/main/experimental_results/Results_of_HSCA_with_different_L_settings_on_5wise_CCAG.csv): Results of *HSCA* with different $L$ settings on all testing instance for 5-wise CCAG problem.
