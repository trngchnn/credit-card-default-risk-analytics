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

## 2. Đối chiếu Yêu cầu Đề thi và Giải pháp của Nhóm
Trận chiến phòng thi yêu cầu nhóm phải ứng dụng tư duy phân tích dữ liệu để giải quyết bài toán quản trị và tối ưu danh mục tín dụng. Dưới đây là cấu trúc đối chiếu giữa các hạng mục câu hỏi trong đề thi tự luận và giải pháp thực tế nhóm đã hoàn thiện trong 90 phút áp lực cao:

### Câu 1a: Thống kê mô tả cơ bản và Tiền xử lý dữ liệu
* **Yêu cầu đề thi:** Khảo sát cấu trúc phân phối dữ liệu, xem xét các tham số tập trung và làm sạch biến đầu vào.
* **Giải pháp của nhóm:** - Triển khai hàm thống kê mô tả toán học (`describe`) để nắm bắt nhanh các chỉ số nền tảng bao gồm giá trị trung bình (Mean), độ lệch chuẩn (Std), khoảng biến thiên (Min, Max) và các điểm phân vị hệ thống.
  - Loại bỏ thuộc tính định danh `ID` ra khỏi không gian biến nhằm tối ưu hóa bộ nhớ và tăng tốc độ xử lý cho các tiến trình phân tích tiếp theo.

### Câu 1b: Khai phá hành vi và Xác định yếu tố phân tách rủi ro
* **Yêu cầu đề thi:** Xác định thuộc tính hành vi mang tính quyết định, có sức mạnh phân loại và bóc tách rủi ro nợ xấu cao nhất trong danh mục.
* **Giải pháp của nhóm:** - Thực hiện kỹ thuật cô lập và phân tích sâu thuộc tính dòng thời gian gần nhất `PAY_0` (Lịch sử trạng thái thanh toán của tháng gần nhất).
  - Chứng minh thành công logic toán tử phân tách: Khi `PAY_0` mang giá trị âm (khách hàng thanh toán đúng hạn hoặc trước hạn) thể hiện sức khỏe tài chính an toàn; ngược lại, khi `PAY_0` chuyển sang giá trị dương (chậm trả tăng dần) rủi ro phát sinh nợ xấu sẽ tăng trưởng theo hàm mũ.

### Câu 2a: Mô hình hóa Phân khúc rủi ro danh mục
* **Yêu cầu đề thi:** Chia nhóm cấu trúc danh mục khách hàng dựa trên các dữ liệu hành vi đã khai phá.
* **Giải pháp của nhóm:** - Ứng dụng kỹ thuật lọc và gán nhãn điều kiện toán học để cấu trúc hóa tập dữ liệu thành 3 phân tầng rủi ro tài chính biệt lập:
    1. *High Risk (Rủi ro cao):* Nhóm tập trung các hành vi chậm trả kéo dài, sở hữu tỷ lệ nợ xấu thực tế (`default`) lên tới **92.9%**.
    2. *Medium Risk (Rủi ro trung bình):* Nhóm khách hàng nằm trong vùng chuyển giao biến động hành vi.
    3. *Low Risk (Rủi ro thấp):* Nhóm khách hàng an toàn, chiếm quy mô lớn nhất (gần 50% danh mục) nhưng chỉ gây ra **1.2%** tỷ lệ nợ xấu hệ thống.

### Câu 2b: Đề xuất Chiến lược hành động và Định lượng Tác động kinh doanh
* **Yêu cầu đề thi:** Đóng vai trò là "Data Strategist" để đề xuất giải pháp hành động cụ thể cho từng nhóm và ước tính hiệu quả kinh tế biên (Business Impact) mang lại cho doanh nghiệp.
* **Giải pháp của nhóm:** - Thiết lập ma trận kịch bản hành động trực tiếp mang tính thực thi cao: Giảm 50% hạn mức đối với nhóm *High Risk*, áp dụng kịch bản nhắc nợ tự động trong tuần cho nhóm *Medium Risk*, và tập trung nguồn lực bán chéo sản phẩm cao cấp (Cross-selling) cho nhóm *Low Risk*.
  - Dịch chuyển kết quả kỹ thuật thành bài toán tài chính thông qua việc định lượng các chỉ số tác động: Ước tính tiết kiệm từ **35% - 40% chi phí xử lý nợ xấu** từ nhóm High Risk; giảm từ 15% - 20% tỷ lệ chuyển nhóm nợ tại nhóm Medium Risk; và thúc đẩy tăng trưởng doanh thu từ 10% - 15% từ việc khai thác nhóm khách hàng an toàn.

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
