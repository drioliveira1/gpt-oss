<p align="center">
  🇧🇷 <a href="./README-PT.md"><strong>Português</strong></a> |
  🇺🇸 <a href="./README.md"><strong>English</strong></a>
</p>

# gpt-oss (Tradução para Português)

<p align="center">
  <a href="https://gpt-oss.com"><strong>Experimente gpt-oss</strong></a> ·
  <a href="https://cookbook.openai.com/topic/gpt-oss"><strong>Guias</strong></a> ·
  <a href="https://arxiv.org/abs/2508.10925"><strong>Ficha do modelo</strong></a> ·
  <a href="https://openai.com/index/introducing-gpt-oss/"><strong>Blog da OpenAI</strong></a>
</p>
<p align="center">
  <strong>Baixe <a href="https://huggingface.co/openai/gpt-oss-120b">gpt-oss-120b</a> e <a href="https://huggingface.co/openai/gpt-oss-20b">gpt-oss-20b</a> no Hugging Face</strong>
</p>

---

Bem-vindo à série **gpt-oss**, os [modelos de pesos abertos (open-weight)](https://openai.com/open-models/) da OpenAI, criados para **raciocínio avançado**, **tarefas agenticas** (com uso de ferramentas) e **casos de uso versáteis de desenvolvedores**.

Estamos lançando duas versões desses modelos:

- **`gpt-oss-120b`** — para uso em produção, propósito geral e tarefas de raciocínio pesado, capaz de rodar em uma GPU de 80 GB (como NVIDIA H100 ou AMD MI300X) — 117 bilhões de parâmetros com 5,1 bilhões ativos.  
- **`gpt-oss-20b`** — para menor latência e uso local ou especializado — 21 bilhões de parâmetros com 3,6 bilhões ativos.  

Ambos foram treinados usando o [formato de resposta Harmony](https://github.com/openai/harmony) e **devem ser usados exclusivamente com esse formato**, caso contrário não funcionarão corretamente.

---

## 🌟 Destaques

- **Licença permissiva Apache 2.0:** use livremente, sem restrições de copyleft nem riscos de patente — ideal para experimentação, personalização e implantação comercial.  
- **Esforço de raciocínio configurável:** ajuste o nível de raciocínio (baixo, médio, alto) conforme o caso de uso e a latência desejada.  
- **Cadeia completa de pensamento (chain-of-thought):** acesso total ao processo de raciocínio do modelo — útil para depuração e confiança nos resultados (não destinado ao usuário final).  
- **Ajustável (fine-tunable):** permite refinar o modelo para casos específicos.  
- **Capacidades agenticas:** suporta chamadas de função, navegação web, execução de código Python e saídas estruturadas.  
- **Quantização MXFP4:** pós-treinamento com pesos MoE quantizados, permitindo que o `120b` rode numa GPU de 80 GB e o `20b` em ~16 GB.  

---

## 💡 Uso Rápido com Transformers

```python
from transformers import pipeline
import torch

model_id = "openai/gpt-oss-20b"
pipe = pipeline("text-generation", model=model_id, torch_dtype="auto", device_map="auto")
messages = [{"role": "user", "content": "Explique mecânica quântica de forma clara e concisa."}]
outputs = pipe(messages, max_new_tokens=256)
print(outputs[0]["generated_text"][-1])
```

---

## ⚙️ Instalação

```bash
pip install gpt-oss
pip install gpt-oss[torch]
pip install gpt-oss[triton]
```

Para uso local:
```bash
git clone https://github.com/openai/gpt-oss.git
GPTOSS_BUILD_METAL=1 pip install -e ".[metal]"
```

---

## 📥 Download dos Modelos

```bash
hf download openai/gpt-oss-120b --include "original/*" --local-dir gpt-oss-120b/
hf download openai/gpt-oss-20b --include "original/*" --local-dir gpt-oss-20b/
```

---

## 📘 Sobre

Este repositório fornece implementações de referência em **PyTorch**, **Triton** e **Metal**, além de ferramentas integradas (`browser` e `python`) que foram usadas durante o treinamento do modelo.

---

## 🌐 Traduções

🇺🇸 **[Versão Original em Inglês (README.md)](./README.md)**  
Documento bilíngue sincronizado — acesse a versão oficial em inglês.

👤 **Tradução:** Adriano De Oliveira (drioliveira1)  
🔗 **Repositório:** [github.com/drioliveira1/gpt-oss](https://github.com/drioliveira1/gpt-oss)
