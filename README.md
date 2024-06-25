# ESM-DBP
The data and a user-friendly standalone program of ESM-DBP

# Pre-requisite:
- Python3, numpy(1.20 or higher), pandas, pytorch(1.5 or higher)
- esm(https://github.com/facebookresearch/esm)
- Linux system (suggested CentOS 7)
  
# Installation:
- 1.Download the source code in this repository.
- 2.Download the models of ESM-DBP at https://huggingface.co/zengwenwu/ESM-DBP, and make sure they locate in the same folder.
- 3.Typical install time on a "normal" desktop computer is about about 30 minutes, depending on the Download speed from Huggingface.

 # Running
- Enter the following command lines on Linux System.
 ```
 $ python prediciton.py esm_model_dict_dir fasta_path result_dir device
```
- [esm_model_dict_dir]: The path of folder that contains all ESM-DBP models.
- [fasta_path]: The path of query protein sequences in fasta format.
- [result_dir]: The path of folder of prediction results.
- [device]: cuda or cpu

# Functionality description
- The protein sequence in fasta format will be first fed to ESM-DBP model to generate a embedding matrix as the feature representation; then, the embedding matrix will be fed into the networks of four downstream tasks to obatain the predcition results.

# Note
- The feature representation of ESM-DBP will be generated named protein_name.fea.
- The prediction results in .csv format will be generated in $result_dir.
- For a typical sequence of about 500 in length, it takes only a few seconds to complete the entire prediction.
- The pretraining data set UniDBP40 can be download at https://huggingface.co/datasets/zengwenwu/UniDBP40/tree/main.
- If you have any question, please email to wwz_cs@126.com freely.
- All the best to you!

# Domain-adaptive pretraining
- Before training the language model of ESM-DBP from scratch, you should download the UniDBP40 dataset at https://huggingface.co/datasets/zengwenwu/UniDBP40/tree/main. 
- Then, enter the following command
```
 $ python domain_adaptive_train.py fasta_path device batch_size device_list epoch
```
- [fasta_path]: The path of UniDBP40.
- [device]: 'cuda:0' is recommended.
- [batch_size]: This should depend on the available memory. Our memory size is 64GB, and a batch size of 100 is appropriate.
- [device_list]: List of available CUDAs. For example: 0,1,2,3
- [epoch]: 20 is recommended.

# Reference
[1] Wenwu Zeng, Yutao Dou, Liangrui Pan, Liwen Xu, Shaoliang Peng. Improving prediction performance of general protein language model by domain-adaptive pretraining on DNA-binding protein. Submitted.
 

