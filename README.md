# DialoGPT - Chatbot Model

## 📌 Giới thiệu
**DialoGPT** là một mô hình chatbot dựa trên Transformer, sử dụng mô hình **DialoGPT** từ Microsoft để tạo hội thoại tự động. Repo này chứa mã nguồn để huấn luyện và triển khai mô hình trên dữ liệu hội thoại.

---

## 🚀 Cài đặt môi trường
Trước khi chạy mã, hãy cài đặt các thư viện cần thiết:
```bash
pip install torch transformers datasets notebook
```

---

## 🔹 Hướng dẫn sử dụng
### 1️⃣ Mở Notebook và chạy thử
Mở **Jupyter Notebook** và chạy `src/model_dialogpt.ipynb`:
```bash
jupyter notebook
```
Sau đó mở file **`src/model_dialogpt.ipynb`** và chạy từng cell.

---

## 🤖 Sử dụng mô hình
Sau khi tải mô hình **DialoGPT**, bạn có thể nhập câu hỏi và nhận phản hồi từ chatbot:

```python
from transformers import AutoModelForCausalLM, AutoTokenizer

# Load model và tokenizer
model_name = "microsoft/DialoGPT-small"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(model_name)

# Nhập câu hỏi
input_text = "Hello, how are you?"
input_ids = tokenizer.encode(input_text, return_tensors="pt")

# Sinh phản hồi
output = model.generate(input_ids, max_length=100, pad_token_id=tokenizer.eos_token_id)
response = tokenizer.decode(output[:, input_ids.shape[-1]:][0], skip_special_tokens=True)

print("Chatbot:", response)
```

---

## 🛠 Tùy chỉnh và Huấn luyện thêm
Bạn có thể fine-tune mô hình trên tập dữ liệu hội thoại của riêng mình để tạo chatbot phù hợp hơn.

### 📌 Fine-tuning DialoGPT:
1. Tải tập dữ liệu hội thoại
2. Huấn luyện mô hình trên dữ liệu mới
3. Đánh giá mô hình sau khi fine-tune

---

## 📜 Thông tin thêm
- **Mô hình:** [DialoGPT trên Hugging Face](https://huggingface.co/microsoft/DialoGPT-small)
- **Tài liệu tham khảo:** [Transformers Library](https://huggingface.co/transformers/)

---


