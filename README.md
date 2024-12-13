# LLM-Compress

![](https://github.com/GoMLsys/GoInference/blob/main/imgs/go.png?raw=true)

## OverView

一个大模型压缩框架，支持:

量化：

- [x] Awq-w8a8
- [x] Awq-w8a16
- [x] Awq-w4a16
- [x] Awq-fp8
- [x] GPTQ-w8a8
- [x] GPTQ-w8a16
- [ ] ……

剪枝：

- [x] Wanda
- [x] short-llm
- [ ] ……

后端：

- [x] vllm
- [x] TensorRT-LLM
- [ ] Rocm（working）
- [ ] llama.cpp（working）

## Install

```bash
git clone https://github.com/GoMLsys/GoInference.git
```



## Usage

在配置文件中修改模型路径、剪枝量化参数等

### 量化

```yaml
quant:
    method: Awq
    quant_type: int-quant
    weight:
        bit: 8
        symmetric: True
        granularity: per_channel
        group_size: -1
    act:
        bit: 8
        symmetric: True
        granularity: per_token
    special:
        trans: True
        trans_version: v2
        weight_clip: True
    quant_out: True
```

### 剪枝

```yaml
sparse:
    method: shortllm
    weight:
        n_prune_layers: 6
```

```yaml
sparse:
    method: Wanda
    weight:
        sparsity: 0.3
    sparsity_out: True
```

