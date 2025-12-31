# hydraulic-demand-forecasting-ml

Ứng dụng các mô hình chuỗi thời gian & học máy để **phân tích và dự báo nhu cầu** (units_sold) cho các sản phẩm thuỷ lực (máy bơm/van công nghiệp) dựa trên dữ liệu bán hàng lịch sử theo tháng và các yếu tố bên ngoài. 

---

## I. Tổng quan đề tài

- **Bài toán:** Dự báo doanh số/nhu cầu theo thời gian giúp tối ưu tồn kho, giảm rủi ro thiếu hàng hoặc tồn kho quá mức. fileciteturn0file0  
- **Dữ liệu:** Chuỗi thời gian **theo tháng**, có phân nhóm theo **region/country**, kèm các biến ngoại sinh (economic indicator, competitor activity, …). fileciteturn0file0  
- **Kết quả chính:** Trong các mô hình thử nghiệm, **Prophet** cho hiệu năng tốt nhất (MAPE ~ 4.99% trong báo cáo). fileciteturn0file0  

---

## II. Mô hình & phương pháp

Notebook triển khai theo các nhóm mô hình sau:

### 1) Baseline (mốc so sánh)
- **Moving Average (MA)**: cửa sổ 5 tháng và 10 tháng.

### 2) Chuỗi thời gian truyền thống
- **SARIMA**: chọn tham số bằng `auto_arima` theo tiêu chí AIC (chu kỳ mùa vụ s=12 cho dữ liệu tháng). fileciteturn0file0  
- **Holt–Winters**: làm mịn mũ (level + trend + seasonality). fileciteturn0file0  

### 3) Học máy
- **XGBoost Regressor**:  
  - Mã hoá region/country  
  - Tạo **time features** (month/year/quarter)  
  - Tạo **lag features** (lag_1, lag_3, lag_12)  
  - Kết hợp thêm các **biến ngoại sinh**  
- **Prophet** (Meta): mô hình cộng g(t)+s(t)+h(t)+ε(t); có thể thêm regressors để tận dụng yếu tố ngoại sinh. fileciteturn0file0  

---

## III. Tiêu chí đánh giá

So sánh mô hình bằng các chỉ số phổ biến:
- **R²**
- **RMSE**
- **MAE**
- **MAPE** fileciteturn0file0  

---

## IV. Kết quả tham khảo (theo báo cáo)

| Mô hình | R² | RMSE | MAE | MAPE |
|---|---:|---:|---:|---:|
| MA(5) | -0.4683 | 10127.10 | 8984.82 | 19.44% |
| MA(10) | -0.2579 | 9375.88 | 6962.13 | 16.18% |
| SARIMA | 0.3847 | 6433.90 | 5527.10 | 11.62% |
| Holt–Winters | 0.5225 | 5497.13 | 4777.06 | 10.01% |
| XGBoost | 0.8072 | 3657.51 | 3203.34 | 7.12% |
| **Prophet** | **0.8830** | **2814.56** | **2238.36** | **4.99%** |

> Ghi chú: Kết quả phụ thuộc vào cách chia train/test và phiên bản dữ liệu làm sạch. fileciteturn0file0  

---

## V. Cấu trúc repo (gợi ý)

```
hydraulic-demand-forecasting-ml/
├─ data/
│  └─ Hydraulic_Sales_Cleaned.csv        # dữ liệu đã làm sạch (không commit nếu lớn)
├─ notebooks/
│  └─ Hydraulic_Sales.ipynb              # notebook chính
├─ report/
│  └─ NHOM18-BaoCao.pdf                  # báo cáo IEEE
├─ requirements.txt
└─ README.md
```

---

## VI. Cài đặt & chạy

### Cách A — Chạy trên Google Colab (khuyến nghị)
1. Mở notebook `notebooks/Hydraulic_Sales.ipynb`.
2. Upload file dữ liệu `Hydraulic_Sales_Cleaned.csv` khi notebook yêu cầu.
3. Chạy lần lượt các cell từ trên xuống.

### Cách B — Chạy local (Jupyter)
**Yêu cầu:** Python 3.9+ (khuyến nghị 3.10+)

Cài thư viện:
```bash
pip install -U pip
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels pmdarima xgboost prophet
```

Mở notebook:
```bash
jupyter notebook notebooks/Hydraulic_Sales.ipynb
```

---

## VII. Tái lập thí nghiệm (reproducibility)

- Giữ cố định `random_state` cho các mô hình ML (XGBoost).
- Chia train/test theo **thời gian** (không shuffle) để tránh rò rỉ dữ liệu.
- Nếu thay đổi “dữ liệu sạch”/các cột ngoại sinh, cần cập nhật danh sách `exog_cols` trong notebook.

---

## VIII. Nhóm thực hiện

- Nguyễn Phúc Lộc  
- Nguyễn Minh Hiển  
- Võ Ngọc Hoàng Lân  
- Võ Hồ Trung Quân fileciteturn0file0  

---

## IX. Tài liệu

Xem chi tiết phương pháp, thiết lập thí nghiệm và phân tích kết quả trong `report/NHOM18-BaoCao.pdf`. fileciteturn0file0
