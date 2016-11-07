# CellNet

## Introduction
CellNet is a network biology-based computational platform that assesses the fidelity of cellular engineering and generates hypotheses for improving cell derivations. CellNet is based on the reconstruction of cell-type specific gene regulatory networks (GRNs), which we performed using publicly available **RNA-Seq** data of 16 mouse and 16 human cell and tissue types. There are two ways to run CellNet for RNA-Seq data. You can run it locally (not recommended). Or you can run it on Amazon's cloud service (AWS).

## Running CellNet locally
To run CellNet for RNA-Seq data locally, you will need to install [TrimGalore](http://www.bioinformatics.babraham.ac.uk/projects/trim_galore/) and [Salmon](https://combine-lab.github.io/salmon/).

## Running CellNet on the cloud
Alternatively, we highly recommend that you use Amazon's Cloud (AWS) to run CellNet for RNA-Seq data instead of running it locally. If you are unfamiliar with AWS and cloud computing, you can think of an AMI as a computer + software frozen in the cloud just waiting for someone to turn it on and use it. Once the AMI has been 'turned on', then we refer to it as an instance, and can interact with it via ssh, and we can place and fetch files on it using scp. The public CellNet AMI, available through the US East (N. Virginia region), is named *CellNet* (ami-62065e75) and has all of the prerequisite software and libraries, including TrimGalore and Salmon pre-installed. If you haven't used AWS before, you can [learn more here](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html) and you can [get started here](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html). Running CellNet on AWS means that you have to upload your raw data (.fastq files) either to your running instance on AWS, or to S3 and then transfer the files to your instance. To learn about transfering your fastq files directly to your instance, see ["Transferring Files to Linux Instances from Linux Using SCP"](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html). To learn about transferring files to/from S3, see the [S3 guide](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonS3.html). Note that Amazon charges by the hour for a running instance (~$1.68/hour). On average, it takes up to 2 hours to run a complete CellNet analysis for 144 gb of raw data (9 samples of 16 gb).

## Trained CellNet objects (*cnProc*)
To analyze expression data with CellNet, you need a trained CellNet object, which we refer to as a CellNet processor or *cnProc* for short. You can select and use the approrpiate cnProc that we have generated from the list below. You can also make your own using the code we provide here. This is useful if you want to add more cell types, or if you want to train up a cnProc for a different species.

| species | date | Cell and tissue types (number of profiles) | cnProc | metadata | expression data |
|---------|------|------|--------|------|----------|-----------------|
| human | Oct_24_2016 | b_cell (83), dendritic_cell (75), endothelial_cell (53), esc (52), fibroblast (79), heart (30), hspc (27), intestine_colon (64), kidney (29), liver (33), lung (95), macrophage (254), monocyte (207), neuron (109), skeletal_muscle (189), t_cell (53) | [cnProc](https://s3.amazonaws.com/CellNet/rna_seq/human/cnProc_RS_human_Oct_24_2016.rda) | [metadata](https://s3.amazonaws.com/CellNet/rna_seq/human/sampTab_RS_human_Oct_24_2016.rda) | [expression data](https://s3.amazonaws.com/CellNet/rna_seq/human/expList_RS_human_Oct_24_2016.rda) |
| mouse | Oct_21_2016 | b_cell (193), dendritic_cell (134), esc (134), fibroblast (182), heart (189), hspc (75), intestine_colon (149), kidney (109), liver (265), lung (116), macrophage (176), neuron (188), nk_cell (53), skeletal_muscle (130), t_cell (87), wat (64) | [cnProc](https://s3.amazonaws.com/CellNet/rna_seq/mouse/cnProc_RS_mouse_Oct_21_2016.rda) | [metadata](https://s3.amazonaws.com/CellNet/rna_seq/mouse/sampTab_RS_mouse_Oct_21_2016.rda) | [expression data](https://s3.amazonaws.com/CellNet/rna_seq/mouse/expList_RS_mouse_Oct_21_2016.rda) |


## Example data
Here are data sets so that you can test drive applying CellNet to your RNA-Seq data

| species | date | SRA accession | description | metadata | expression data |
|---------|------|---------------|-------------|----------|-----------------|


## CellNet for microarray data
You can also use CellNet to analyze *microarray* data either locally using [this code](https://pcahan1.github.io/cellnetr/), or using the [the original web application](http://cellnet.hms.harvard.edu/).