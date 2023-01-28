# Benchmarking ingest pipeline with an inference process 
This script will kick off a _reindex of an existing index into a new index. This is to remove external latency possibilities and focus on inference time. 

Different allocation and threads per allocation combinations are used for each loop, restarting the supervised model each time. 

## Various metrics are collected including:
- average_inference_time_ms_last_minute
- throughput_last_minute

For each of those metrics several calulations are done:
- min
- median
- max

both metrics and functions can be changed

# output
results are written to separate .csv and .json file formats

## json partial example
```
{'16x1': {'allocations': 16,
          'nodesReport': {'instance-0000000025': 
                    {'average_inference_time_ms_last_minute': {'max': 301.1378683157512,
                                                               'median': 301.11121703209403,
                                                               'min': 299.6329194524037},
                                                  'throughput_last_minute': {'max': 3147,
                                                                             'median': 3141.0,
                                                                             'min': 2749}}},
          'running_time_in_nanos': 190735480466,
          'threads per allocation': 1},
 '1x1': {'allocations': 1,
         'nodesReport': {'instance-0000000025': 
                    {'average_inference_time_ms_last_minute': {'max': 166.53015873015872,
                                                               'median': 163.46049046321525,
                                                                'min': 159.54521276595744},
                                                 'throughput_last_minute': {'max': 376,
                                                                            'median': 367.0,
                                                                            'min': 315}}},
                                                                            ```
