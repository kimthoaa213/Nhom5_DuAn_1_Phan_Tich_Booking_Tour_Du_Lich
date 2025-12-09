# Nhom5_DAT111_DuAn1_BookingTour
# Dự án 1- Phân tích booking Tour Du Lịch của công ty 5 Stars 🏝️
## **1. Giới thiệu về dự án**
Dự án Vietnam Tour Booking Analytics được xây dựng nhằm phân tích hoạt động kinh doanh của doanh nghiệp du lịch Việt Nam trong giai đoạn sau đại dịch COVID-19. Dựa trên tập dữ liệu ~10.061 booking, tiến hành thiết kế mô hình dữ liệu, xây dựng KPI và trực quan hóa trong Power BI để hỗ trợ doanh nghiệp:  
1. Theo dõi mức độ phục hồi sau Covid-19  
2. Đánh giá hiệu quả từng tour  
3. Phân tích hành vi & trải nghiệm khách hàng  
4. Hỗ trợ quyết định tối ưu danh mục tour, marketing, vận hành và chất lượng dịch vụ  
**- Thông tin tập dữ liệu 📑:**
+ **Hiện trạng**: Sau đại dịch COVID-19 (2020–2021), ngành du lịch Việt Nam chịu ảnh hưởng nặng nề, hầu hết doanh nghiệp lữ hành phải tạm dừng hoạt động.
Đến năm 2022, khi mở cửa trở lại, công ty 5 Stars bắt đầu phục hồi bằng các tour nội địa ngắn ngày, giá hợp lý, tập trung vào khách hàng trong nước.
Từ 2022 đến 2024, lượng khách và doanh thu tăng mạnh trở lại, đặc biệt tại các điểm đến như Sapa, Nha Trang, Cần Thơ.
Tuy nhiên, lợi nhuận vẫn tăng chậm, chưa tương xứng với doanh thu do chi phí vận hành và hiệu quả từng vùng chưa đồng đều.
+ **Quy mô dữ liệu**: 10,061 booking, 19 cột (khách, tour, kênh đặt, giá, chi phí, lợi nhuận, ngày đi/về, vùng, mùa…).
+ **Trường giá chính**: unit_price_vnd (đơn giá/khách), tổng hợp doanh thu/chi phí/lợi nhuận: revenue_vnd, total_cost_vnd, profit_vnd.
+ **Thời gian**: travel_start từ 2022-01-01 đến 2024-12-31.
+ **Địa điểm**: location (thành phố/điểm đến), region (miền).
+ **Loại tour**: tour_type (Beach, Cultural, Mountain, River, Adventure, City, Cruise, Food).
+ **Khách**: customer_origin (Domestic/Foreign).  
## **2. Mục tiêu dự án 🎯**
+ Xây dựng dashboard trực quan phục vụ phân tích kinh doanh 3 lớp:  
1. Tổng quan hoạt động (Business Overview)  
2. Hiệu quả tour (Tour Performance)  
3. Hành vi – trải nghiệm khách hàng (Customer Behavior)  
+ Phát hiện insight quan trọng để cải thiện doanh thu, lợi nhuận và chất lượng dịch vụ.  
+ Xây dựng quy trình xử lý dữ liệu và mô hình hóa chuẩn cho Power BI & SQL Server.  
## **3. Quy trình xử lý dữ liệu 🔧**
### **Bước 1:** Trích xuất dữ liệu (Extract) 📥
Import file CSV gốc.
Kiểm tra lỗi định dạng, encoding, missing values
### **Bước 2:** Làm sạch dữ liệu (Clean) – Excel 🧹
Xóa hoặc xử lý giá trị null
Chuẩn hóa dữ liệu
Loại bỏ trùng lặp
Format ngày tháng
### **Bước 3:** Lưu trữ dữ liệu (Load) – SQL 🗄️
+ Tách dữ liệu thành các bảng: **Fact_Booking, D_Tour, D_Location, D_Customer, D_Channel, D_Date**  
+ Thiết kế mối quan hệ dạng star schema.
<img width="975" height="637" alt="image" src="https://github.com/user-attachments/assets/f50f4ea0-3701-43ab-9cd5-a7b84714d7a7" />

+ Import dữ liệu đã làm sạch vào SQL  
### Bước 4: Xây dựng mô hình & measure trong Power BI 📝  
+ Tạo hệ thống KPI: Revenue, Profit, Profit Margin, YoY, Participants,…  
+ Tạo các measure nâng cao:  
Cumulative Revenue (Pareto)  
Profit per Participant  
Avg Participants per Tour  
Returning Customer Rate  
Rating Analysis  
Cancellation Reason Analysis  
### **Bước 5:** Trực quan hóa (Visualization) – Power BI 🔽  
#### ✔ Trang 1 — Business Overview
Theo dõi tình hình hoạt động tổng quan:
+ Doanh thu – lợi nhuận toàn công ty
+ Xu hướng phục hồi theo tháng/quý
+ Phân bổ theo region, season, tour type
+ Chi phí – biên lợi nhuận
+ Tỷ lệ booking theo segment
#### ✔ Trang 2 — Tour Performance
Đánh giá hiệu quả vận hành từng tour:
+ Revenue/Profit theo tour type
+ Pareto 80/20
+ Profit/Revenue per participant
+ Top tour hiệu quả nhất
+ Revenue by region × season
+ Scatter Revenue – Margin – Participants (phân loại Cash Cow / Star / Dog)
#### ✔ Trang 3 — Customer Behavior
Phân tích hành vi và trải nghiệm khách hàng:
+ Segment & Demographic
+ Booking time behavior (early/normal/late)
+ Channel performance
+ Cancellation reasons
+ Post-tour rating distribution
+ Returning customers
#### ✔ Trang 4 — Cancellation rick
Phân tích ảnh hưởng của tình trạng hủy tour:
+ Revenue lost/Customer lost
+ Tour Cancelled by Conths
+ Tour Cancelled by Region by Months
+ Tour Cancelled by Weathers
## 4. Cấu trúc thư mục (Project Structure)    
📁 project/    
 ├── data/   
 │    ├── raw/                        
 │    └── cleaned/                    
 │    
 ├── scripts/  
 │    ├── database_VN_booking_tour.sql
 │    └──  DAX.txt              
 │   
 ├── powerbi/    
 │    └── Nhom5_DuAn1.pbix                  
 │    
 ├── document/    
 │    └── dat111_baocao_nhom5.doc       
 │  
 ├── README.md  

## **5. Hướng dẫn cài đặt & sử dụng 📒**
1. Clone project
<pre> git clone https://github.com/kimthoaa213/Nhom5_DAT111_DuAn1_BookingTour </pre>
2. Chuẩn bị dữ liệu
Mở file CSV → làm sạch trong Excel → lưu lại vào thư mục /data/cleaned
3. Import SQL
Chạy file schema.sql để tạo bảng
Import dữ liệu từ excel vào SQL
4. Mở Power BI
Mở file .pbix
Refresh data để cập nhật dashboard
## **6. Dashboard mẫu (Preview) 🎞️**
<img width="1143" height="673" alt="image" src="https://github.com/user-attachments/assets/7f8ac7f3-f406-4842-99b7-ab7f326406f8" />    

### *Insight nổi bật
+ Khách nội địa chiếm tỷ trọng cao nhưng khách quốc tế có doanh thu/khách cao hơn.
+ Các tour mùa Summer và Autumn tạo ra doanh thu mạnh nhất.
+ Một số tour lượng khách cao nhưng biên lợi nhuận thấp → cần tối ưu chi phí hoặc tăng giá.
+ Lý do hủy tour chủ yếu liên quan đến thời tiết và thay đổi lịch trình.
+ Returning customers đóng góp tỉ lệ small nhưng giá trị booking cao → nhóm khách quan trọng.
## **7. Công nghệ sử dụng 💻**   
Excel – Data cleaning  
SQL Server / MySQL – Data storage  
Power BI – Visualization  
GitHub – Quản lý phiên bản  
