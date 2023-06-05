# Artifact

We will make our code publicly available after it is accepted. Currently, we only release the binary code for reproducing the results. We provide various scripts for reproducing the dynamic workload results. By default, these scripts run all state-of-the-art (SOTA) methods under the same workload.

## Hardware platform
Ubuntu Linux server with an Intel(R) Xeon(R) 810 Gold 6152 CPU and 755 GB RAM

## Datasets
For the datasets, please refer to the SOSD benchmark.
https://github.com/learnedsystems/SOSD

## Scripts
Write only after bulk loading

```
for DATA in fb genome osm planet
do
	./LEAST-ID378  \
	--keys_file=../dataset/${DATA}  \
	--cpu_id=40     \
	--number_keys=200000000      \
	--num_operations=100000000      \
	--num_preload=100000000 \
	--seed=2379 \
	--read_ratio=0 \
	--insert_ratio=1 \
	--output_path=../results/bulk_loading/write_${DATA}.txt

done
```

Read only after bulk loading
```
for DATA in fb genome osm planet
do
	./LEAST-ID378  \
	--keys_file=../dataset/${DATA}  \
	--cpu_id=40     \
	--number_keys=200000000      \
	--num_operations=400000000      \
	--num_preload=200000000 \
	--seed=2379 \
	--output_path=../results/bulk_loading/Read_${DATA}.txt

done
```

Read write after bulk loading
```
for DATA in fb genome osm planet
do
	./LEAST-ID378  \
	--keys_file=../dataset/${DATA}  \
	--cpu_id=40     \
	--number_keys=200000000      \
	--num_operations=200000000      \
	--num_preload=100000000 \
	--seed=2379 \
	--read_ratio=0.5 \
	--insert_ratio=0.5 \
	--output_path=../results/bulk_loading/mix_${DATA}.txt

done
```
