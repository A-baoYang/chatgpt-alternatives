# ChatGPT Alternatives
Collection of ChatGPT alternatives &amp; LLM tuning methods

---

### [ [THUDM/ChatGLM-6B](https://github.com/THUDM/ChatGLM-6B) ]  
#model

基於 General Language Model (GLM) 架構，具有 62 億參數、支持中英雙語的對話語言模型。輔以 RLHF、監督微調、反饋自助等技術，經過約 1T token 的中英雙語訓練。

實測：
- Inference: 可成功在 1 GPU (T4, 16G) 上運行。
- Chat Mode: 支援 streaming 像 CahtGPT 那樣逐字輸出，不用等到所有文字生成完畢才看到輸出
- Finetune: (實作中)

<br>

### [ [HuggingFace/PEFT](https://github.com/huggingface/peft) ]  
#promptuning #parametereffective

HuggingFace 開源的高效參數微調框架！PEFT 方法僅微調少量 (額外) 模型參數，同時凍結預訓練 LLM 的大部分參數，降低了計算和儲存成本、克服災難性遺忘的問題。

實測：
- finetune: 可在 1 GPU 上成功 fine-tine BLOOM-1b1 （用 torchrun 不做任何優化，若要維持同樣 batch_size 需要分散到 4 GPU）

了解更多：
- [PEFT: 在低資源硬件上對十億規模模型進行參數高效微調](https://blog.csdn.net/HuggingFace/article/details/129292898)

<br>

### [ [FMInference/FlexGen](https://github.com/FMInference/FlexGen) ]  
#offload

目的是使低階顯卡也具備 serve 大模型的能力！對 CPU + GPU 記憶體 + 硬體儲存空間的使用進行全域調度優化。

實測：
- Inference: 可成功運行 OPT-6.7B 於 4 GPU (T4, 16G) 上。

了解更多：
- [知乎博主對 FlexGen 的實測](https://zhuanlan.zhihu.com/p/610853654)

<br>

### [ [hpcaitech/ColossalAI](https://github.com/hpcaitech/ColossalAI) ]  
#parallel #distributed #RLHF

基於 Deepspeed ZeRO + Gemini + 自動 Chunk 記憶體管理機制 & 低秩矩陣微調（LoRA） 等記憶體管理等方法，提出在單機單 GPU、單機多 GPU 上的大規模平行推理及訓練的解決方案。 

實測：
- Inference: (實作中)
- Finetune: (實作中)

了解更多：
- [Colossal-AI 用單張消費級顯示卡，就可以低成本重現ChatGPT完整演算流程](https://www.techbang.com/posts/104007-chatgpt-colossalai-graphics-card)

<br>

### [ [lucidrains/PaLM-rlhf-pytorch](https://github.com/lucidrains/PaLM-rlhf-pytorch) ]  
#RLHF

在 PaLM 架構上實現 RLHF（人類反饋的強化學習）

<br>

### [ [ChatLLaMA](https://github.com/juncongmoo/chatllama) ]  
#RLHF

在 LLaMA 基礎下使用 RLHF 訓練，建構出類似 ChatGPT 的服務；LLaMA 架構比 ChatGPT(GPT3.5) 更小，但訓練過程和單 GPU 推理速度更快，成本更低。

<br>

### [ [oobabooga/text-generation-webui](https://github.com/oobabooga/text-generation-webui) ]  
#UI

文本生成領域的 AUTOMATIC1111/stable-diffusion-webui ，可運行 GPT-J 6B、OPT、GALACTICA、LLaMA 和 Pygmalion 等大語言模型的 gradio web UI；並且提供了 FlexGen offload, Deepspeed ZeRO-3 offload, LoRA 等讓模型在有限資源下運行的方式、及 colab 環境的操作引導。

<br>

### [ [togethercomputer/OpenChatKit](https://github.com/togethercomputer/OpenChatKit) ]  
#model #RLHF

主要的亮點是 OpenAI 前員工創立、在 OIG-43M 訓練數據集上訓練的 200 億參數模型。

<br>

### [ [tatsu-lab/stanford_alpaca](https://github.com/tatsu-lab/stanford_alpaca) ]  
#model #RLHF

Stanford 用 OpenAI text-davinci-003模型所生成的 52K 指令遵循資料集，用來 finetune LLaMA-7B 訓練出行為與 text-davinci-003 模型相近的 Alpaca 7B 模型。雖然 LLaMA 僅限有相關學術研究的人員申請，Alpaca 本身也未完全開源，但 HuggingFace 上已有人根據 Alpaca 作法 finetune 出一樣的模型： chavinlo/alpaca-native

實測：
- Inference: chavinlo/alpaca-native 可在 1 GPU (T4, 16G) 下成功運行，但只支援英文輸出（可以讀懂中文但不論怎麼調 prompt 只能輸出英文）


