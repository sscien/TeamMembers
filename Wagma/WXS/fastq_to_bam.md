# If your input start from WXS fastqs

## step1 (Terminal 1)
```
export LSF_DOCKER_VOLUMES="/storage1/fs1/dinglab/Active:/storage1/fs1/dinglab/Active /scratch1/fs1/dinglab:/scratch1/fs1/dinglab"
export PATH="/miniconda/envs/pecgs/bin:$PATH"
bsub -q dinglab-interactive -G compute-dinglab -Is -a 'docker(estorrs/pecgs-pipeline:0.0.1)' '/bin/bash'
```

## step2 (Terminal 1)

```
rm -r /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/*

mkdir -p /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/

python /storage1/fs1/dinglab/Active/Projects/ysong/Projects/pecgs-cwl/pecgs_wxs_fq_Tindaisy_v2023_03/src/compute1/generate_run_commands.py make-run --sequencing-info /storage1/fs1/dinglab/Active/Projects/ysong/Projects/Team_Members/Wagma/sequencing_info.txt --queue general pecgs_TN_wxs_fq /storage1/fs1/dinglab/Active/Projects/ysong/Projects/Team_Members/Wagma/wagma_WXS_FASTQ_run_list.txt /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/
```


## step3 submit run (NEW Terminal2)

```
cd /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/
bash 1.run_jobs.sh
```

## step4 tidy_run (Terminal 1)
```
#!/bin/bash
python /storage1/fs1/dinglab/Active/Projects/estorrs/pecgs-pipeline/src/compute1/generate_run_commands.py tidy-run pecgs_TN_wxs_fq /storage1/fs1/dinglab/Active/Projects/ysong/Projects/Team_Members/Wagma/wagma_WXS_FASTQ_run_list.txt /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/
```
## step5 summarize_run (Terminal 1)
3.summarize_run.sh
```
#!/bin/bash
python /storage1/fs1/dinglab/Active/Projects/estorrs/pecgs-pipeline/src/compute1/generate_run_commands.py summarize-run pecgs_TN_wxs_fq /storage1/fs1/dinglab/Active/Projects/ysong/Projects/Team_Members/Wagma/wagma_WXS_FASTQ_run_list.txt /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/
```

## step6 move_run (Terminal 1)

```
#!/bin/bash
python /storage1/fs1/dinglab/Active/Projects/estorrs/pecgs-pipeline/src/compute1/generate_run_commands.py move-run pecgs_TN_wxs_fq /storage1/fs1/dinglab/Active/Projects/ysong/Projects/Team_Members/Wagma/wagma_WXS_FASTQ_run_list.txt /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/ --target-dir /storage1/fs1/dinglab/Active/Projects/ysong/Projects/Team_Members/Wagma/
```

# If your input start from WXS bams

## Wagma WXS bam Tindaisy run

## step 1

```
export LSF_DOCKER_VOLUMES="/storage1/fs1/dinglab/Active:/storage1/fs1/dinglab/Active /scratch1/fs1/dinglab:/scratch1/fs1/dinglab"
export PATH="/miniconda/envs/pecgs/bin:$PATH"

bsub -q dinglab-interactive -G compute-dinglab -Is -a 'docker(estorrs/pecgs-pipeline:0.0.1)' '/bin/bash'

```

## step 2

```
mkdir - p /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/wxs_bam/

```
## step 3
```
python /storage1/fs1/dinglab/Active/Projects/ysong/Projects/pecgs-cwl/pecgs-pipeline/src/compute1/generate_run_commands.py make-run  --queue general pecgs_TN_wxs_bam /storage1/fs1/dinglab/Active/Projects/ysong/Projects/Team_Members/Wagma/wxs_bam_run_list.txt /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/wxs_bam/
```

## step 4
```
bash /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/wxs_bam/1.run_jobs.sh
```
