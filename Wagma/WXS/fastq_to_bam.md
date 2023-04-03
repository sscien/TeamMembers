# step1 
```
export LSF_DOCKER_VOLUMES="/storage1/fs1/dinglab/Active:/storage1/fs1/dinglab/Active /scratch1/fs1/dinglab:/scratch1/fs1/dinglab"
export PATH="/miniconda/envs/pecgs/bin:$PATH"
bsub -q dinglab-interactive -G compute-dinglab -Is -a 'docker(estorrs/pecgs-pipeline:0.0.1)' '/bin/bash'
```

# step2

```
mkdir /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/

python /storage1/fs1/dinglab/Active/Projects/ysong/Projects/pecgs-cwl/pecgs-pipeline/src/compute1/generate_run_commands.py make-run --sequencing-info /storage1/fs1/dinglab/Active/Projects/ysong/Projects/Team_Members/Wagma/sequencing_info.txt --queue general pecgs_TN_wxs_fq /storage1/fs1/dinglab/Active/Projects/ysong/Projects/Team_Members/Wagma/wagma_WXS_FASTQ_run_list.txt /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/
```


# step3 (NEW Terminal)

```
cd /scratch1/fs1/dinglab/Active/Projects/ysong/Wagma/fq_bam/
bash 1.run_jobs.sh
```

```
#!/bin/bash
python /storage1/fs1/dinglab/Active/Projects/estorrs/pecgs-pipeline/src/compute1/generate_run_commands.py tidy-run pecgs_TN_wxs_fq run_list.txt /scratch1/fs1/dinglab/estorrs/cromwell-data/pecgs/testing/pecgs_TN_wxs_fq
```

3.summarize_run.sh
```
#!/bin/bash
python /storage1/fs1/dinglab/Active/Projects/estorrs/pecgs-pipeline/src/compute1/generate_run_commands.py summarize-run pecgs_TN_wxs_fq run_list.txt /scratch1/fs1/dinglab/estorrs/cromwell-data/pecgs/testing/pecgs_TN_wxs_fq
```
4.move_run.sh
```
#!/bin/bash
python /storage1/fs1/dinglab/Active/Projects/estorrs/pecgs-pipeline/src/compute1/generate_run_commands.py move-run pecgs_TN_wxs_fq run_list.txt /scratch1/fs1/dinglab/estorrs/cromwell-data/pecgs/testing/pecgs_TN_wxs_fq --target-dir /storage1/fs1/dinglab/Active/Projects/estorrs/wombat/tests/data/pecgs_TN_wxs_fq/run
```
