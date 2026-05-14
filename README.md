# DS108 Lab 4 – Notebooks

Thư mục này chứa 3 Jupyter Notebook tương ứng với 3 giai đoạn chính của pipeline dự đoán trễ hàng (shipment delay prediction).

## Cấu trúc

| Notebook | Nội dung | File Python tương ứng |
|----------|----------|----------------------|
| `Cleaning.ipynb` | Đọc dữ liệu, merge, align cột, cleaning, impute, encode, scale | `config.py`, `data_loader.py`, `preprocessing.py` |
| `EDA and Feature Engineering.ipynb` | Khám phá dữ liệu, phân tích phân bố nhãn, missing values, correlation | `config.py`, `eda.py`, `preprocessing.py` |
| `Modeling.ipynb` | 4 thí nghiệm α₁→α₄, train 3 model (LGBM/XGB/CatBoost), evaluation | `config.py`, `experiments.py`, `models.py`, `evaluation.py`, `main.py` |

## Cách sử dụng

1. Chạy theo thứ tự: **Cleaning → EDA and Feature Engineering → Modeling**
2. Mỗi notebook đã bao gồm toàn bộ code Python và giải thích Markdown chi tiết.
3. Nếu muốn chạy toàn bộ pipeline tự động, sử dụng `python main.py` ở thư mục gốc.

## Lưu ý quan trọng

- Dữ liệu gốc có **class imbalance nghiêm trọng** (~1:40). Không nên tin tưởng Accuracy mà cần dùng ROC-AUC, F1, Precision/Recall.
- Period 4-6 có 47 cột, period 7-9 có 37 cột. Khi làm cross-period experiments, **chỉ giữ 37 cột chung** để tránh mismatch.
- Tên cột `SPECIAL DIV` (có space) và `SPECIAL_DIV` (có underscore) trong data gốc có thể gây crash với LightGBM/XGBoost nếu không sanitize.
