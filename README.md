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

### Build TRT Engines : 

```
trtllm-build --checkpoint_dir ./tllm_checkpoint --max_batch_size 8 --remove_input_padding disable  --bert_attention_plugin disable
python vae_decoder_trt.py --max_batch_size 8
# Succeeded building vae_decoder/plan/visual_encoder_fp16.plan in 122 s
```

### Run Inference : 
```
mpirun -n 4 --allow-run-as-root python sample.py --batch-size 8
```

### Result : 
![{15DC3646-86A2-4E04-9D30-8FCB0D181AC1}](https://github.com/user-attachments/assets/0b7f243a-0cf5-48b9-9ed1-be161b79d379)

