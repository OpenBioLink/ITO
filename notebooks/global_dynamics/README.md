

# Analysis Notebooks

## Run all notebooks automatically

Requirements
- Blazegraph hosting ITO (please set the correct endpoint in config.yml)
- data/grouping_ITO_00101.csv (manually curated)
- data/grouping_ITO_00141.csv (manually curated)
- data/polarities.csv (manually curated)
- data/datasets.json (Downloaded from https://paperswithcode.com/media/about/datasets.json.gz)

Run 
```
pip install -r requirements.txt
```

To run all notebooks

Linux

```bash
./run_all
```

Windows PS

```bash
./run_all
```

## 1. **create_csv.ipynb** 

Extracts sota curves and other data from the ITO. Requires blazegraph containing the ITO graph. 

Input: 
- Blazegraph endpoint (defined in config.yml)
- data/grouping_ITO_00101.csv (manually curated)
- data/grouping_ITO_00141.csv (manually curated)
- data/polarities.csv (manually curated)

Output: 
- data/sota_ITO_00101.csv
- data/sota_ITO_00141.csv
- data/all_ITO_00101.csv
- data/all_ITO_00141.csv

## 2. **global_map.ipynb**

Notebook for creating the global analysis plot for each task and for each superclasses (_grp).
   
Input:
- data/sota_ITO_00101.csv
- data/sota_ITO_00141.csv
  
Output:
- artefacts/vision_process.html
- artefacts/vision_process.png
- artefacts/natural_language_processing.html
- artefacts/natural_language_processing.png
- artefacts/vision_process_grp.html
- artefacts/vision_process_grp.png
- artefacts/natural_language_processing_grp.html
- artefacts/natural_language_processing_grp.png
- data/ITO_00101_global_map_level_keys.csv # used by qualitative_analysis
- data/ITO_00141_global_map_level_keys.csv # used by qualitative_analysis

## 3. **clustering.ipynb**

Notbook for experiments on clustering trajectories.
   
Input:
- data/sota_ITO_00101.csv
- data/sota_ITO_00141.csv
  
Output:
- artefacts/cluster_{n}_som.csv (Datasets, tasks and metrics of each SOM cluster)
- artefacts/cluster_{n}.csv (Datasets, tasks and metrics of each Kmeans cluster)
- artefacts/clustering.png (Figure SOM clustered trajectories)
- artefacts/clustering_som.png (Figure Kmenas clustered trajectories)
- artefacts/top10_gold.png (Figure Top10 trajectories similar to gold functions)
- artefacts/boxplot_difference.png (Figure boxplot of gradients of trajectories)

## 4. **qualitative_analysis.ipynb**

Notebook for experiments on further plots (piktogram)

tlc = top level class ("natural_language_processing" or "vision_process")

Input:
- data/all_ITO_00101.csv
- data/all_ITO_00141.csv
- data/grouping_ITO_00101.csv
- data/grouping_ITO_00141.csv
- data/ITO_00101_global_map_level_keys.csv
- data/ITO_00141_global_map_level_keys.csv

Output:
- artefacts/{tlc}_new_benchmarks.png (Distribution of introduction of benchmarks, meaning the year a benchmark is reported as NEW is the year **any** metric is first reported)
- artefacts/{tlc}_disbanded_benchmarks.png (Distribution of unused benchmarks, meaning the year a benchmark is reported as disbanded is the year **after** **any** metric is last reported)
- artefacts/{tlc}_sota.png (Number of benchmarks where SOTA results and non-SOTA results were reported)
- artefacts/{tlc}_composite.png (Composite figure of above three)
- artefacts/{tlc}_active.png (Cummulative sum of new - disbanded)  
- artefacts/{tlc}_pikto.png (Piktogram figure of paper)
- artefacts/{tlc}_pikto.html
- artefacts/{tlc}_task_active.png (Similar to _active, however one trace per task)
- artefacts/{tlc}_task_active.html
- artefacts/{tlc}_prop_sota_active.png (Similar to _active, howver with another trace depicting the proportion of active benchmarks reporting sota results)
- artefacts/{tlc}_prop_sota_active.html

## 5. **benchmark_analysis.ipynb**

Input:
- Blazegraph endpoint (Defined in config.yml)
- /data/datasets.json (Downloaded from https://paperswithcode.com/media/about/datasets.json.gz)

Output:
- artefacts{tlc}_popular.csv
- artefacts{tlc}_unpopular.csv
- artefacts{tlc}_popular_task_types.csv
- artefacts{tlc}_unpopular_task_types.csv
- artefacts{tlc}_popular_2018.csv
- artefacts{tlc}_unpopular_2018.csv
- artefacts{tlc}_popular_task_types_2018.csv
- artefacts{tlc}_unpopular_task_types_2018.csv

# Other plots

## **plotting_expected_trajectory_patterns.ipynb**

Input:
- data/example/proteins_all_results.csv
- data/example/fashionmnist_all_results.csv
- data/example/imagenet_all_results.csv
- data/example/ucf101_all_results.csv
- data/example/df_proteins_sota.csv
- data/example/df_fashionmnist_sota.csv
- data/example/df_imagenet_sota.csv
- data/example/df_ucf101_sota.csv

Output:
- artefacts/expected_patterns.png
- artefacts/expected_patterns.svg

## **plotting_consecutive_and_parallel_benchmarks.ipynb**

Input:
- data/example/df_cifar10_sota.csv
- data/example/df_cifar100_sota.csv
- data/example/df_vqa1_sota.csv
- data/example/df_vqa2_sota.csv

Output:
- artefacts/consecutive_and_parallel_benchmarks.png
- artefacts/consecutive_and_parallel_benchmarks.svg