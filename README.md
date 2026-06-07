# Data Analytics Contest 2026: Credit Card Default Risk & Strategic Recommendations

## 1. Thông tin chung
* **Đề tài:** Phân tích hành vi và xây dựng chiến lược quản trị rủi ro nợ xấu thẻ tín dụng (Default of Credit Card Clients).
* **Bối cảnh:** Giải pháp xử lý đề thi tự luận trực tiếp tại Vòng Loại Chính thức - Cuộc thi Nhà phân tích dữ liệu 2026.
* **Thời gian thực hiện:** Ngày 17/05/2026
* **Thời lượng thi giới hạn:** 1 tiếng 30 phút.
* **Nhóm thực hiện:** 02 thành viên.
* **Kết quả chung cuộc:** Đạt vào Vòng Chung kết.

## 2. Đối chiếu Yêu cầu Đề thi và Mức độ hoàn thiện của Nhóm
Trận chiến phòng thi yêu cầu nhóm phải giải quyết bài toán cốt lõi về Quản trị rủi ro dựa trên dữ liệu. Dưới đây là bảng đối chiếu chi tiết giữa đề bài đặt ra và giải pháp thực tế nhóm đã hoàn thiện trong 90 phút:

| Yêu cầu từ Đề thi | Giải pháp Thực tế Nhóm đã Hoàn thiện | Mức độ hoàn thiện |
|---|---|---|
| **Câu 4a: Phân tích Phân khúc Rủi ro** <br>- Xác định các thuộc tính có sức mạnh phân tách rủi ro nợ xấu cao nhất. | - Định vị thành công thuộc tính `PAY_0` (Lịch sử thanh toán tháng gần nhất) là toán tử phân tách mạnh nhất. <br>- Chứng minh logic: Giá trị âm $\rightarrow$ Khỏe mạnh; Giá trị dương $\rightarrow$ Rủi ro tăng theo hàm mũ. | Hoàn thành 100% |
| **Câu 4a: Gom nhóm & Định lượng Phân khúc** <br>- Chia danh mục khách hàng thành các nhóm rủi ro cụ thể dựa trên hành vi. | - Cấu trúc hóa toàn bộ tập dữ liệu thành 3 phân tầng tài chính rõ rệt: <br>1. *High Risk* (92.9% tỷ lệ default thực tế). <br>2. *Medium Risk* (Nhóm chuyển giao biến động). <br>3. *Low Risk* (An toàn, chiếm gần 50% danh mục nhưng chỉ gây 1.2% default). | Hoàn thành 100% |
| **Câu 4b: Đề xuất Chiến lược Hành động** <br>- Đề xuất giải pháp hành động cụ thể cho từng nhóm khách hàng được phân loại. | - Thiết lập ma trận hành động có tính thực thi cao: <br>- *High Risk:* Cắt giảm 50% hạn mức tín dụng lập tức, kích hoạt kịch bản thu hồi nợ tự động cường độ cao. <br>- *Medium Risk:* Nhắc nợ tự động trong tuần. <br>- *Low Risk:* Tập trung nguồn lực Cross-selling. | Hoàn thành 100% |
| **Câu 4b: Ước tính Tác động Kinh doanh** <br>- Định lượng hiệu quả kinh tế (Business Impact) biên dựa trên các kịch bản đề xuất. | - Tính toán thành công các chỉ số đo lường hiệu quả tài chính: <br>- Tiết kiệm 35% - 40% chi phí xử lý nợ xấu. <br>- Giảm 15% - 20% tỷ lệ chuyển nhóm nợ tại nhóm Medium. <br>- Thúc đẩy tăng trưởng doanh thu 10% - 15% từ bán chéo nhóm Low. | Hoàn thành 100% |

## 3. Dữ liệu sử dụng (Dataset)
Bộ dữ liệu sử dụng là *Default of Credit Card Clients Dataset*.

### Các thuộc tính phân tích chính:
* **Thông tin định danh & Nhân khẩu học:** Hạn mức tín dụng được cấp (LIMIT_BAL), Giới tính, Học vấn, Tình trạng hôn nhân, Độ tuổi.
* **Lịch sử thanh toán qua các tháng:** Trạng thái chậm trả khoản vay từ tháng 4 đến tháng 9 (Biến chỉ báo mạnh `PAY_0` đến `PAY_6`).
* **Biến mục tiêu hệ thống:** Trạng thái khách hàng vi phạm hợp đồng tín dụng vào tháng kế tiếp (`default.payment.next.month`).

## 4. Kỹ năng và Công cụ sử dụng
* **Ngôn ngữ lập trình:** Python
* **Thư viện xử lý & Khai phá cấu trúc:** pandas, numpy
* **Thư viện trực quan hóa số liệu:** matplotlib, seaborn (Xây dựng các biểu đồ mật độ phân phối và ma trận tương quan)
* **Môi trường triển khai:** Google Colab / Jupyter Notebook (Thực hiện quy trình xử lý tốc độ cao)

## 5. Quy trình xử lý dữ liệu và Tư duy Phân tích (Workflow)
Do đặc thù giới hạn thời gian cực kỳ nghiêm ngặt tại vòng loại, nhóm đã triển khai quy trình phân tích tinh gọn nhằm tối ưu hóa tốc độ ra quyết định:

1. **Thống kê mô tả toán học:** Kiểm tra nhanh các thông số tập trung (`describe`), phát hiện cấu trúc phân phối và thực hiện loại bỏ cột định danh `ID` nhằm tối ưu hóa không gian biến.
2. **Khai phá điểm gãy hành vi:** Tập trung nguồn lực phân tích thuộc tính dòng thời gian gần nhất nhằm xác định ranh giới chuyển dịch của dòng tiền khách hàng.
3. **Mô hình hóa Phân khúc Rủi ro:** Triển khai kỹ thuật lọc và gán nhãn điều kiện toán học để phân tầng danh mục khách hàng thành 3 nhóm: High, Medium, Low Risk.
4. **Thiết lập Khung giải pháp & Định lượng Impact:** Cấu trúc hóa tư duy từ các con số khô khan thành một bài toán kinh tế hoàn chỉnh, ước tính trực tiếp giá trị tài chính mang lại cho ngân hàng nhằm đáp ứng trọn vẹn yêu cầu cốt lõi của vai trò "Data Strategist".

## 6. Kết luận và Ý nghĩa thực tiễn
* **Tính nguyên bản:** Toàn bộ mã nguồn trong repository này được giữ nguyên trạng 100% kết quả xử lý tại phòng thi vào ngày 17/05/2026. Nhóm quyết định không tái cấu trúc hay sửa đổi code sau cuộc thi nhằm phản ánh trung thực năng lực phân tích nhanh (Fast-paced Analytics) và kỹ năng giải quyết bài toán kinh doanh thực tế dưới áp lực cực hạn.
* **Giá trị bài thi:** Sự kết hợp hài hòa giữa kỹ thuật tiền xử lý dữ liệu chuẩn xác và tư duy chiến lược thương mại (Business Sense) ở phần cuối bài thi chính là yếu tố then chốt giúp nhóm chinh phục Hội đồng Giám khảo, vượt qua hàng loạt đối thủ nặng ký ở Vòng Loại để đi tiếp vào Vòng Chung kết toàn quốc.
