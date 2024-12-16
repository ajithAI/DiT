# DiT

### Download Model : 
```
mkdir /home/user/TRT_LLM_0.16 && mkdir /home/user/TRT_LLM_0.16/DiT/
cd /home/user/TRT_LLM_0.16/DiT
wget https://dl.fbaipublicfiles.com/DiT/models/DiT-XL-2-512x512.pt
```

### Convert Model to TRT Checkpoint : 
```
cd /home/user/TRT_LLM_0.16/TensorRT-LLM/examples/dit
python3 convert_checkpoint.py --timm_ckpt /home/user/TRT_LLM_0.16/DiT/Models/DiT-XL-2-512x512.pt --tp_size 4
```
