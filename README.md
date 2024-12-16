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
 Error Code: 9: Skipping tactic 0x0000000000000000 due to exception [autotuner.cpp:get_best_tactics:2400] Autotuner: no tactics to implement operation:
 1216: corrltn: DiT/x_embedder/proj/conv2d_L3511/CONVOLUTION_0_output_0'_before_bias.1-(f16[__mye2080_proxy.1,1152,32,32][]so[], mem_prop=0) | DiT/forward_with_cfg_L323/concat_L2514/CONCATENATION_0_output_0'.1-(f16[__mye2080_proxy.1,4,64,64][]so[], mem_prop=0), DiT/x_embedder/proj/conv2d_L3511/CONVOLUTION_0 filterWeightsHalf-{2.58088e-05, 0.0063
[12/16/2024-05:36:07] [TRT] [E] IBuilder::buildSerializedNetwork: Error Code 10: Internal Error (Could not find any implementation for node {ForeignNode[DiT/forward_with_cfg_L320/slice_L1276/SLICE_0...DiT/blocks/0/attn/dense/multiply_collect_L272/multiply_and_lora_L246/matmul_L1064/cast_L871/CAST_0]}.)
```

![{EA282778-2F89-4E0C-8515-15EA975221BF}](https://github.com/user-attachments/assets/f38a0894-86ac-44b2-bcb2-ce5567314825)

