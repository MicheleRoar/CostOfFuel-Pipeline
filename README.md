# CombSAFE-Pipeline

## About
This repository contains the implementation of the combinatorial and Semantic Analysis of Functional Elements (CombSAFE) pipeline presented in the paper: ```Leone M., Galeota E., Ceri S., Masseroli M., and Pellizzola M. "Identification, semantic annotation and comparison of chromatin regulatory state combinations in multiple biological condiions", 2021 ```. This pipeline is a flexible computational method to identify combinations of static and dynamic functional elements, and how they change among biological conditions. 
Given as input a set of ChIP-seq samples and the functional elements to be considered, the ```CombSAFE``` pipeline allow to:

- consider histone modifications, transcription factors and any other type of dynamic and static genomic features (e.g., CpG islands, transposable elements, ecc.). 
- rely on public repositories to identify from their metadata the biological conditions in which the dynamic functional elements of interest were charted
- identify combinations throughout the genome of the corresponding homogeneously analysed omic data using hidden Markov models. 
- focus on specific genomic regions, applying clustering to explore how significant combinations of the functional elements compare among cells and conditions. 
- perform functional enrichment analyses based on the genes found in regions with similar combinations of functional elements.

## Cookbook

### Load input files
```combsafe.import_path(filepath)```<br/>
Parameters: 
* filepath, path object or file-like object

### Generate semantic annotations
```combsafe.generate_semantic_df(separator, encode_convert)```<br/>
Parameters: <br/>
  separator: str, default '\t' <br/>
Delimiter to use
* encode_convert: bool, default False
  * If true, id encode IDs are searched to be converted to GSM <br/>
Returns: 
  - DataFrame or TextParser
    - A comma-separated values (csv) file is returned as two-dimensional data structure with labeled axes.

### Data Analysis
```combsafe.plot_factor_freq(merged_df, n)```<br/>

![alt text](https://drive.google.com/uc?export=download&id=1WyFjK1eYM9nSbMKLht0dXp6ouscZ381P)

```combsafe.generate_fixed_factor_pool(semantic_df, ["H3K27ac", "H3K4me3", "H3K27me3"], 5)```

![alt text](https://drive.google.com/uc?export=download&id=1TD-wc-4rJ0DDagZebLu0BgFeLVJ8SwW0)

```combsafe.get_semantic_annotation_list(semantic_df, ["H3K27ac", "H3K4me3", "H3K27me3", "H3K4me1", "H3K36me3"])```

![alt text](https://drive.google.com/uc?export=download&id=1llQnJyeJku6evCgDaOymWuiIgCE5dYXO)


### Select features and combine samples

```combsafe.run_gmql(["H3K27ac", "H3K4me3", "H3K27me3", "H3K4me1", "H3K36me3"])```

### [Optional] Add custom tracks

```combsafe.run_gmqladd_custom_tracks(track_lable, path_to_custom_track, index)```

### Identify Chromatin States

```combsafe.identify_chromatin_states(number_of_states, n_core)```

### Single Gene Analysis



### Whole Genome Analysis

### [Optional] Semantic Analysis
