## ATAC WXS bam validation run
```
mkdir - p /scratch1/fs1/dinglab/Active/Projects/ysong/atac_wxs_bam_v2/
python /storage1/fs1/dinglab/Active/Projects/ysong/Projects/pecgs-cwl/pecgs-pipeline/src/compute1/generate_run_commands.py make-run  --queue general pecgs_TN_wxs_bam /storage1/fs1/dinglab/Active/Projects/ysong/Projects/PECGS/Analysis/ATAC_Tindaisy_Somaticwrapper_comparision/ATAC_WXS_bam_run_list.txt /scratch1/fs1/dinglab/Active/Projects/ysong/atac_wxs_bam_v2/
```

```
python /storage1/fs1/dinglab/Active/Projects/ysong/Projects/pecgs-cwl/pecgs-pipeline/src/compute1/generate_run_commands.py summarize-run  --queue general pecgs_TN_wxs_bam /storage1/fs1/dinglab/Active/Projects/ysong/Projects/PECGS/Analysis/ATAC_Tindaisy_Somaticwrapper_comparision/ATAC_WXS_bam_run_list.txt /scratch1/fs1/dinglab/Active/Projects/ysong/atac_wxs_bam_v2/
```

```
bash /scratch1/fs1/dinglab/Active/Projects/ysong/atac_wxs_bam_v2/1.run_jobs.sh
```
