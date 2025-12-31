# Hydraulic Product Demand Forecasting 📈

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)
![University](https://img.shields.io/badge/UIT-Information%20Systems-green)

## 📖 Giới thiệu (Overview)

Dự án này tập trung vào việc ứng dụng các mô hình Học máy (Machine Learning) và Chuỗi thời gian (Time Series) để phân tích và dự báo nhu cầu tiêu thụ sản phẩm (cụ thể là máy bơm và van công nghiệp) cho một công ty thủy lực đa quốc gia.

Dữ liệu được sử dụng là dữ liệu mô phỏng hàng tháng từ đầu năm 2020 đến hết năm 2024. Mục tiêu là xây dựng mô hình dự báo chính xác doanh số bán hàng trong tương lai, hỗ trợ doanh nghiệp tối ưu hóa quy trình nhập hàng và quản lý kho.

**Lĩnh vực nghiên cứu:** Data Mining, Time Series Analysis, Demand Forecasting.

## 👥 Thành viên nhóm (Team Members)

Dự án được thực hiện bởi **Nhóm 18** - Khoa Hệ Thống Thông Tin, Trường Đại học Công Nghệ Thông Tin (UIT):

| STT | Họ và tên | MSSV | 
|:---:|:---|:---|
| 1 | Võ Ngọc Hoàng Lân | 23520843 |
| 2 | Nguyễn Minh Hiển | 23520462 | 
| 3 | Nguyễn Phúc Lộc | 23520859 |  
| 4 | Võ Hồ Trung Quân | 23521273 | 

## 🗂 Cấu trúc dữ liệu (Dataset)

Dữ liệu đầu vào bao gồm lịch sử bán hàng của các thiết bị thủy lực với các đặc trưng chính:
* **Thời gian:** Dữ liệu theo tháng (2020 - 2024).
* **Sản phẩm:** Máy bơm thủy lực, Van công nghiệp.
* **Biến phụ thuộc:** Doanh số bán hàng (Sales Volume).
* **Các yếu tố ảnh hưởng:** Xu hướng thị trường, yếu tố mùa vụ.

## 🛠 Công nghệ & Thư viện (Tech Stack)

Dự án được thực hiện hoàn toàn trên ngôn ngữ **Python**, sử dụng các thư viện phân tích dữ liệu và học máy phổ biến:

* **Xử lý dữ liệu:** `Pandas`, `NumPy`
* **Trực quan hóa:** `Matplotlib`, `Seaborn`
* **Thống kê & Chuỗi thời gian:** `Statsmodels`, `Pmdarima` (Auto ARIMA)
* **Mô hình học máy:** `Scikit-learn`, `XGBoost` (theo tài liệu tham khảo)
* **Môi trường:** Jupyter Notebook / Google Colab

## ⚙️ Quy trình thực hiện (Pipeline)

1.  **Tiền xử lý dữ liệu (Data Preprocessing):**
    * Làm sạch dữ liệu, xử lý missing values.
    * Chuyển đổi định dạng thời gian.
2.  **Phân tích khám phá (EDA):**
    * Vẽ biểu đồ chuỗi thời gian để quan sát xu hướng (Trend) và tính mùa vụ (Seasonality).
    * Phân tích tương quan.
3.  **Xây dựng mô hình (Modeling):**
    * Áp dụng các mô hình thống kê truyền thống (ARIMA/SARIMA).
    * Áp dụng các mô hình Machine Learning hiện đại.
4.  **Đánh giá (Evaluation):**
    * Sử dụng các chỉ số đo lường sai số: MAE, RMSE, MAPE.
   

## 📊 Kết quả (Results)

* Dự án đã xác định được tính mùa vụ rõ rệt trong doanh số bán hàng.
* Các mô hình đưa ra dự báo với độ chính xác chấp nhận được cho kế hoạch kinh doanh ngắn hạn.
