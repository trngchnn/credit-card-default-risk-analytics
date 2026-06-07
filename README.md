# Credit Card Default Risk Analytics: Phân tích hành vi và đề xuất chiến lược quản trị rủi ro nợ xấu thẻ tín dụng

## 1. Thông tin chung
- **Bối cảnh:** Bài làm giải quyết đề thi tự luận trực tiếp tại Vòng Loại Chính thức - Cuộc thi Nhà phân tích dữ liệu 2026 cấp Khoa.
- **Thời gian thực hiện:** 17/05/2026.
- **Thời lượng giới hạn:** 1 tiếng 30 phút dưới áp lực phòng thi.
- **Nhóm thực hiện:** 02 thành viên.
- **Kết quả chung cuộc:** Đạt điểm số tối ưu và chính thức bước tiếp vào Vòng Chung kết.

## 2. Cấu trúc Đề thi và Giải pháp triển khai
Dự án tập trung giải quyết trọn vẹn 2 câu hỏi cốt lõi của đề thi dựa trên tập dữ liệu rủi ro tín dụng khách hàng:

### Câu 1a: Thống kê mô tả và Tiền xử lý dữ liệu
- **Yêu cầu:** Khảo sát cấu trúc phân phối, kiểm tra tham số tập trung và làm sạch biến đầu vào.
- **Giải pháp:** Triển khai hàm thống kê mô tả `describe()` nhằm xác định nhanh các chỉ số nền tảng (Mean, Std, Min, Max, các điểm phân vị). Thực hiện loại bỏ thuộc tính định danh `ID` nhằm tối ưu không gian biến và tăng tốc độ xử lý tính toán.

### Câu 1b: Khai phá hành vi và Xác định yếu tố bóc tách rủi ro
- **Yêu cầu:** Xác định thuộc tính hành vi đóng vai trò quyết định, có khả năng phân loại rủi ro nợ xấu cao nhất.
- **Giải pháp:** Cô lập và phân tích sâu thuộc tính `PAY_0` (Lịch sử trạng thái thanh toán của tháng gần nhất). Nghiên cứu chỉ ra logic phân tách rõ ràng: Khi `PAY_0 <= 0` (Thanh toán đúng hoặc trước hạn), danh mục tài chính nằm trong vùng an toàn; ngược lại, khi `PAY_0 > 0` (Chậm trả tăng dần), rủi ro phát sinh nợ xấu (`default`) có xu hướng tăng trưởng theo hàm mũ.

### Câu 2a: Mô hình hóa Phân khúc rủi ro danh mục
- **Yêu cầu:** Chia nhóm cấu trúc khách hàng dựa trên dữ liệu hành vi đã khai phá.
- **Giải pháp:** Áp dụng kỹ thuật lọc và gán nhãn điều kiện để phân tầng tập dữ liệu thành 3 nhóm rủi ro tài chính biệt lập:
  1. *High Risk (Rủi ro cao):* Nhóm khách hàng chậm trả kéo dài, sở hữu tỷ lệ nợ xấu thực tế đạt **92.9%**.
  2. *Medium Risk (Rủi ro trung bình):* Nhóm biến động hành vi, nằm trong vùng chuyển giao nợ quá hạn.
  3. *Low Risk (Rủi ro thấp):* Nhóm an toàn, chiếm quy mô lớn nhất danh mục (gần 50%) nhưng chỉ chịu **1.2%** tỷ lệ nợ xấu hệ thống.

### Câu 2b: Đề xuất Chiến lược hành động và Định lượng tác động kinh doanh
- **Yêu cầu:** Đóng vai trò Chuyên viên chiến lược dữ liệu (Data Strategist) để đề xuất giải pháp ứng phó cụ thể cho từng nhóm và ước tính hiệu quả kinh tế biên (Business Impact).
- **Giải pháp:** Thiết lập ma trận kịch bản hành động: Giảm 50% hạn mức đối với nhóm *High Risk*, tự động hóa quy trình nhắc nợ trong tuần với nhóm *Medium Risk*, và tập trung nguồn lực bán chéo sản phẩm tài chính cao cấp (Cross-selling) cho nhóm *Low Risk*. 
- **Tác động định lượng dự kiến:** Tiết kiệm từ 35% - 40% chi phí xử lý nợ xấu từ nhóm High Risk; giảm 15% - 20% tỷ lệ chuyển nhóm nợ tại nhóm Medium Risk; thúc đẩy tăng trưởng doanh thu từ 10% - 15% từ việc khai thác nhóm khách hàng an toàn.

## 3. Dữ liệu sử dụng (Dataset)
Bộ dữ liệu được cung cấp trực tiếp tại phòng thi (*Default of Credit Card Clients Dataset*).
- **Biến độc lập (Features):** Hạn mức tín dụng (LIMIT_BAL), Đặc điểm nhân khẩu học (Giới tính, Học vấn, Tình trạng hôn nhân, Độ tuổi), Lịch sử trạng thái thanh toán qua các tháng (`PAY_0` đến `PAY_6`).
- **Biến mục tiêu (Target Variable):** Trạng thái vi phạm hợp đồng tín dụng vào tháng kế tiếp (`default.payment.next.month`).

## 4. Công cụ sử dụng
- **Ngôn ngữ:** Python.
- **Thư viện:** Pandas, NumPy, Matplotlib, Seaborn.
- **Môi trường:** Google Colab.

## 5. Tính nguyên bản của mã nguồn
Toàn bộ mã nguồn trong kho lưu trữ này được giữ nguyên trạng 100% so với kết quả xử lý thực tế tại phòng thi vào ngày 17/05/2026. Nhóm quyết định không tái cấu trúc hay tối ưu lại code sau khi kết thúc giờ thi nhằm phản ánh trung thực năng lực phân tích tốc độ cao (Fast-paced Analytics) và tư duy áp dụng dữ liệu để giải quyết bài toán quản trị rủi ro doanh nghiệp trong thời gian giới hạn.
