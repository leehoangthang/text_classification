## Dự án: Phân loại cảm xúc văn bản với DistilBERT

### 1. Giới thiệu

Dự án này xây dựng một mô hình phân loại cảm xúc (negative, neutral, positive) cho các câu tiếng Anh sử dụng DistilBERT. Các bước chính bao gồm:

- Đọc và làm sạch dữ liệu (loại bỏ ký tự đặc biệt, URL, emoji, v.v.).
- Xóa bản ghi trùng lặp và thống kê phân phối nhãn.
- Tiền xử lý dữ liệu: mã hóa nhãn, cân bằng dữ liệu (RandomOverSampler).
- Tokenization và đóng gói dữ liệu thành `Dataset` của Hugging Face.
- Huấn luyện hai lần mô hình DistilBERT với các tham số khác nhau.
- Đánh giá mô hình bằng Accuracy, Precision, Recall, F1-score và ma trận nhầm lẫn.

### 2. Yêu cầu

- Python >= 3.7
- pandas
- numpy
- matplotlib
- torch
- transformers
- datasets
- scikit-learn
- seaborn
- imbalanced-learn

Bạn có thể cài đặt nhanh bằng:
```bash
pip install pandas numpy matplotlib torch transformers datasets scikit-learn seaborn imbalanced-learn
```

### 3. Cấu trúc thư mục

```
project_root/
├── data.csv                 # Dữ liệu gốc
├── readme.md                # Tập tin hướng dẫn (README này)
├── train.py                 # Script chính để huấn luyện và đánh giá
├── results/                 # Thư mục lưu kết quả huấn luyện
├── logs/                    # Thư mục lưu logs
└── Model 2/                 # Thư mục lưu mô hình thứ 2
```

### 4. Hướng dẫn sử dụng

1. **Chuẩn bị dữ liệu**
   - Đảm bảo bạn đã đặt `data.csv` vào thư mục gốc hoặc sửa lại đường dẫn tương ứng trong script.

2. **Chạy huấn luyện**
   - Mở terminal, chuyển đến thư mục `project_root`
   - Chạy:
     ```bash
     python train.py --data_path ./data.csv --output_dir ./results
     ```
   - Tham số tuỳ chọn có thể được thêm vào script để điều chỉnh batch size, số epoch, v.v.

3. **Xem kết quả**
   - Kết quả huấn luyện và ma trận nhầm lẫn sẽ được in ra console và lưu trong `results/`.
   - Mô hình và tokenizer sẽ được lưu tại đường dẫn đã chỉ định.

### 5. Kết quả mẫu

- Accuracy: ~0.899
- Precision: ~0.89
- Recall: ~0.89
- F1-score: ~0.88

_Ma trận nhầm lẫn_ sẽ được hiển thị dưới dạng heatmap.

### 6. Mở rộng

- Thử nghiệm với các kiến trúc khác (BERT, RoBERTa).
- Điều chỉnh tham số huấn luyện (learning rate, batch size).
- Áp dụng các kỹ thuật tiền xử lý nâng cao như stemming, lemmatization.
- Triển khai mô hình lên API hoặc web app.



