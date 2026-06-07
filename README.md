# Data Analytics Contest 2026: Credit Card Default Risk & Strategic Recommendations

## 1. Thông tin chung
* **Đề tài bài thi:** Phân tích hành vi và đề xuất chiến lược quản trị rủi ro nợ xấu thẻ tín dụng (Default of Credit Card Clients).
* **Bối cảnh:** Giải pháp xử lý đề thi tự luận trực tiếp tại Vòng Loại Chính thức - Cuộc thi Nhà phân tích dữ liệu 2026.
* **Thời gian thực hiện:** Ngày 17/05/2026
* **Thời lượng thi giới hạn:** 1 tiếng 30 phút.
* **Nhóm thực hiện:** 02 thành viên.
* **Kết quả chung cuộc:** Đậu vòng Chung kết của cuộc thi.

## 2. Đối chiếu Yêu cầu Đề thi và Mức độ hoàn thiện của Nhóm
Trận chiến phòng thi yêu cầu nhóm phải ứng dụng tư duy phân tích dữ liệu để giải quyết bài toán quản trị và tối ưu danh mục tín dụng. Dưới đây là bảng đối chiếu chi tiết giữa các hạng mục cốt lõi của đề bài tự luận và giải pháp thực tế nhóm đã hoàn thiện trong 90 phút:

| Nội dung yêu cầu từ Đề thi | Giải pháp Thực tế Nhóm đã Hoàn thiện trong Code
|---|---|---|
| **Phân tích Khám phá & Tiền xử lý** <br>- Khảo sát cấu trúc phân phối dữ liệu và làm sạch biến. | - Thực hiện thống kê mô tả toán học (`describe`) để nắm bắt các tham số tập trung (Mean, Std, Min, Max, Tứ phân vị). <br>- Loại bỏ cột định danh `ID` để tối ưu hóa không gian biến. 
| **Xác định yếu tố phân tách rủi ro** <br>- Tìm ra thuộc tính hành vi có sức mạnh phân loại nợ xấu cao nhất. | - Khai phá và định vị thành công thuộc tính `PAY_0` (Lịch sử thanh toán tháng gần nhất) là chỉ báo mạnh nhất. <br>- Chứng minh logic: Giá trị âm (thanh toán đúng/trước hạn) thể hiện sức khỏe tài chính tốt; giá trị dương (chậm trả) khiến rủi ro nợ xấu tăng theo hàm mũ.
| **Phân khúc rủi ro danh mục** <br>- Chia nhóm khách hàng dựa trên dữ liệu hành vi. | - Kỹ thuật hóa tập dữ liệu thành 3 phân tầng tài chính rõ rệt bằng cấu trúc điều kiện lọc: <br>1. *High Risk:* Nhóm phát sinh tỷ lệ default thực tế lên tới 92.9%. <br>2. *Medium Risk:* Nhóm chuyển giao biến động hành vi. <br>3. *Low Risk:* Nhóm an toàn, chiếm gần 50% danh mục nhưng chỉ gây ra 1.2% tỷ lệ default. 
| **Đề xuất Chiến lược chiến thuật** <br>- Đưa ra khuyến nghị hành động cụ thể cho từng nhóm. | - Thiết lập ma trận kịch bản hành động trực tiếp: <br>- *High Risk:* Giảm ngay 50% hạn mức tín dụng hiện tại, kích hoạt hệ thống nhắc nợ tự động tần suất cao. <br>- *Medium Risk:* Áp dụng nhắc nợ tự động trong tuần để chặn chuyển nhóm nợ. <br>- *Low Risk:* Tập trung nguồn lực Cross-selling (bán chéo sản phẩm cao cấp). 
| **Định lượng Tác động Kinh doanh** <br>- Ước tính hiệu quả kinh tế biên (Business Impact) cho doanh nghiệp. | - Chuyển con số kỹ thuật thành bài toán tài chính với các chỉ số đo lường hiệu quả cụ thể: <br>- Tiết kiệm 35% - 40% chi phí xử lý nợ xấu từ nhóm High Risk. <br>- Giảm 15% - 20% tỷ lệ default tại nhóm Medium Risk. <br>- Thúc đẩy tăng trưởng doanh thu 10% - 15% từ việc khai thác nhóm Low Risk.

## 3. Dữ liệu sử dụng (Dataset)
Bộ dữ liệu sử dụng là *Default of Credit Card Clients Dataset* được cung cấp trực tiếp trong phòng thi.

### Các thuộc tính phân tích cốt lõi:
* **Thông tin nhân khẩu học & Nền tảng:** Hạn mức tín dụng được cấp (LIMIT_BAL), Giới tính, Học vấn, Tình trạng hôn nhân, Độ tuổi.
* **Lịch sử trạng thái thanh toán qua các tháng:** Tiến độ trả khoản vay từ tháng 4 đến tháng 9 (Biến chỉ báo từ `PAY_0` đến `PAY_6`).
* **Biến mục tiêu (Target):** Trạng thái khách hàng vi phạm hợp đồng tín dụng/nợ xấu vào tháng kế tiếp (`default.payment.next.month`).

## 4. Kỹ năng và Công cụ sử dụng
* **Ngôn ngữ lập trình:** Python
* **Thư viện xử lý dữ liệu:** pandas, numpy
* **Thư viện trực quan hóa:** matplotlib, seaborn
* **Môi trường triển khai:** Google Colab

## 5. Quy trình xử lý và Tư duy Phân tích (Workflow phòng thi)
Do đặc thù giới hạn thời gian cực kỳ nghiêm ngặt của vòng loại trực tiếp, nhóm đã triển khai một workflow tinh gọn nhằm tối ưu hóa tốc độ ra quyết định chiến lược:

1. **Khảo sát toán học sơ bộ:** Đọc hiểu cấu trúc bảng dữ liệu thô, sử dụng thống kê mô tả để kiểm tra tính toàn vẹn của các biến hành vi tài chính.
2. **Cô lập điểm gãy hành vi:** Tập trung nguồn lực phân tích thuộc tính dòng thời gian gần nhất (`PAY_0`) để xác định ranh giới biến động của dòng tiền khách hàng.
3. **Mô hình hóa Phân khúc:** Sử dụng kỹ thuật lọc và gán nhãn điều kiện để phân tầng danh mục khách hàng thành các khối rủi ro biệt lập (High, Medium, Low Risk).
4. **Cấu trúc khung giải pháp kinh doanh:** Đóng vai trò là "Data Strategist", nhóm không dừng lại ở các dòng lệnh code sạch mà đã dịch chuyển các kết quả phân tích thành một kịch bản quản trị rủi ro và tăng trưởng doanh thu hoàn chỉnh, đáp ứng trọn vẹn yêu cầu cốt lõi của đề thi.

## 6. Kết luận và Ý nghĩa thực tiễn
* **Tính nguyên bản:** Toàn bộ mã nguồn trong repository này được giữ nguyên trạng 100% kết quả xử lý tại phòng thi vào ngày 17/05/2026. Nhóm quyết định không tái cấu trúc hay sửa đổi code sau cuộc thi nhằm phản ánh trung thực năng lực phân tích nhanh (Fast-paced Analytics) và kỹ năng giải quyết bài toán kinh doanh thực tế dưới áp lực cực hạn.
* **Giá trị bài thi:** Sự kết hợp hài hòa giữa kỹ thuật tiền xử lý dữ liệu chuẩn xác và tư duy chiến lược thương mại (Business Sense) ở phần kết luận chính là yếu tố then chốt giúp nhóm chinh phục Hội đồng Giám khảo, vượt qua hàng loạt đối thủ nặng ký ở Vòng Loại để chính thức ghi tên mình vào Vòng Chung kết toàn quốc.
