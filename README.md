# 🇹🇷 Turkish E-commerce Product Information Extraction with Fine-Tuned LLaMA

🧠 Convert messy Turkish HTML into clean structured JSON — 100% offline with Ollama  
📄 License: MIT | ✅ [Open in Colab](https://colab.research.google.com/drive/1cYXaDjN18XauiCccqiR4gNK2AN1fNoIa?usp=sharing) | 💻 [GitHub Repo](https://github.com/AsliCY/turkish-ecommerce-ai)

---

## 🎯 What This Project Does

This project fine-tunes a **LLaMA 3.2 3B** model to extract **structured product information from Turkish e-commerce HTML pages**.

It transforms unstructured HTML into clean JSON format with **local, private inference** using **Ollama**.

### 🧾 Perfect for:
- 🕷️ **Web Scraping**: Automate product data collection  
- 💰 **Price Monitoring**: Track prices across sites  
- 📊 **Market Research**: Analyze competitors  
- 🔄 **Data Migration**: Transfer products between platforms

---

## 🌟 Key Features

| Feature | Description |
|---------|-------------|
| 🇹🇷 **Turkish Language Specialized** | Fine-tuned on realistic Turkish HTML structures |
| 🧠 **High Accuracy** | >90–95% JSON extraction success rate |
| ⚡ **Fast Inference** | 2–5 seconds per product |
| 🔒 **100% Local** | Fully offline with Ollama |
| 🛠️ **No Dependencies** | Only Ollama is needed |
| 🧱 **Easily Extendable** | Add categories, features, or HTML formats |

---

## 🎬 Quick Text-Based Demo

```bash
echo '<div class="product">
  <h1>iPhone 15 Pro - Apple</h1>
  <div class="price">54.999 TL</div>
  <div class="brand">Apple</div>
</div>' | ollama run turkish-ecommerce
```

**Output:**
```json
{
  "name": "iPhone 15 Pro",
  "brand": "Apple",
  "price": "54.999 TL",
  "category": "Telefon"
}
```

---

## 🚀 Quick Start

### 🛠️ Step 1: Install Ollama

```bash
# macOS/Linux
curl -fsSL https://ollama.ai/install.sh | sh
```

➡️ **For Windows**: Download from https://ollama.ai

### 🧠 Step 2: Train the Model (Optional)

**Option A:** Use our pre-trained model (recommended)
- 🔗 [Download from Hugging Face](https://huggingface.co/Asli-123/turkish-ecommerce-model)

**Option B:** Train yourself
- Open the [Fine-Tuning Notebook](https://colab.research.google.com/drive/1cYXaDjN18XauiCccqiR4gNK2AN1fNoIa?usp=sharing)
- Generates 500+ synthetic HTML/JSON pairs
- Fine-tunes LLaMA with LoRA
- Exports model in GGUF format
- Runs in ~30–45 minutes on free GPU

### 🖥️ Step 3: Deploy Locally with Ollama

```bash
# Create model (in model folder)
ollama create turkish-ecommerce -f turkish_ecommerce.modelfile

# Run it
echo '<html>...</html>' | ollama run turkish-ecommerce
```

---

## 💻 Usage Examples

### Basic Usage
```bash
# Extract from file
ollama run turkish-ecommerce < product.html

# Interactive mode
ollama run turkish-ecommerce
```

### Batch Processing
```bash
# Process multiple files
for file in *.html; do
  echo "Processing: $file"
  ollama run turkish-ecommerce < "$file" > "${file%.html}.json"
done
```

---

## 📊 Performance Metrics

| Metric | Value |
|--------|-------|
| **Success Rate** | >90–95% |
| **Model Size** | ~1.8 GB (GGUF) |
| **Inference Time** | 2–5 seconds |
| **Categories Supported** | 5 (Phone, Laptop, etc.) |
| **Training Time** | ~30 minutes (Colab) |
| **RAM Usage** | ~5–6 GB |

---

## 🏗️ Architecture

```
┌─────────────┐    ┌─────────────────┐    ┌──────────────┐
│ HTML Input  │ -> │ Ollama + LLaMA  │ -> │ JSON Output  │
└─────────────┘    └─────────────────┘    └──────────────┘
```

**Technical Stack:**
- **Base Model**: LLaMA 3.2 3B Instruct
- **Fine-tuning**: LoRA via Unsloth
- **Deployment**: Ollama (GGUF format)
- **Quantization**: Q4_K_M (optimized size/performance)

---

## 🧪 Testing & Validation

### Quick Test
```bash
# Create a sample test file
echo '<div><h1>iPhone 15 Pro</h1><span>54.999 TL</span></div>' > test.html
ollama run turkish-ecommerce < test.html | jq .
```

### Batch Testing
```bash
# Test multiple files
for file in test_*.html; do
  result=$(ollama run turkish-ecommerce < "$file")
  echo "$result" | jq . > "${file%.html}_result.json"
done
```

---

## 🧩 Customization

### ➕ Add New Categories
Edit the Colab notebook:

```python
products["Kozmetik"] = ["L'Oreal Foundation"]
features_by_category["Kozmetik"] = ["SPF 30", "Su Geçirmez"]
```

### 🌐 Multi-language Support
Add English or Arabic examples in dataset generation step.

### 🛠️ Site-Specific Training
Use custom HTML formats (e.g., Trendyol vs. Hepsiburada) in training samples.

---

## 🌍 Supported Turkish Sites

Tested on HTML formats from:
- **Trendyol**
- **Hepsiburada**
- **GittiGidiyor**
- **N11**
- **Amazon.com.tr**
- And any custom e-commerce site with consistent markup

---

## 🤝 Contributing

We welcome contributions!

### 🐛 Report Bugs
- HTML parsing failures
- Incorrect JSON fields

### ✨ Suggest Features
- New categories
- Image extraction
- Multi-language models

### 🔧 Improve Code or Training Data
- Better templates
- More diverse HTML
- Documentation improvements

---

## 📝 Changelog

### v1.0.0 (Current)
- ✅ Fine-tuned LLaMA 3.2 3B on Turkish HTML
- ✅ Ollama deployment (GGUF Q4_K_M)
- ✅ 5 categories supported
- ✅ >90% JSON extraction accuracy

### 🚧 Coming Soon
- 🌐 Multi-language support
- 🖼️ Image metadata extraction
- 📱 Mobile-friendly layout parsing
- 🧠 Custom site adapters

---

## 🔒 Privacy & Security

- ✅ **100% Local**: No external API calls
- 🔍 **Transparent**: Fully open-source
- ❌ **No Tracking**: No telemetry or data collection
- ✅ **GDPR Compliant**

---

## 📎 Links

- 🔗 [GitHub Repository](https://github.com/AsliCY/turkish-ecommerce-ai)
- 🧠 [Hugging Face Model](https://huggingface.co/Asli-123/turkish-ecommerce-model)
- 🚀 [Fine-Tuning Colab Notebook](https://colab.research.google.com/drive/1cYXaDjN18XauiCccqiR4gNK2AN1fNoIa?usp=sharing)

---

## 🙏 Acknowledgments

- **Meta AI** for LLaMA
- **Unsloth** for efficient fine-tuning
- **Ollama** for elegant local LLM deployment
- **Turkish NLP community** for inspiration

---

⭐️ **Star this repo if you find it useful!**  
📬 **Contributions and feedback welcome!**  
🇹🇷 **Built with ❤️ for Turkish E-commerce**
