
# 1.Xây dựng báo cáo phân tích kết quả học tập từ nhiều tài liệu

###  1. Các Prompt sử dụng để đọc và xử lý 4 file

Em sử dụng AI để đọc từng file riêng biệt, trích xuất dữ liệu thành bảng và giữ nguyên thông tin gốc, không tự ý bổ sung điểm

**Prompt 1: Đọc file danh sách sinh viên**

Em hãy đọc file 1 và trích xuất danh sách sinh viên thành bảng gồm 2 cột: Mã sinh viên, Họ tên. Kiểm tra mã sinh viên bị trùng hoặc thông tin bị thiếu. Không tự sửa dữ liệu nếu chưa có căn cứ

**Prompt 2: Đọc file điểm chuyên cần và bài tập**

Em hãy đọc file 2 và trích xuất thành bảng gồm: Mã sinh viên, họ tên, điểm chuyên cần, điểm bài tập. Kiểm tra dữ liệu trùng lặp, thiếu điểm và điểm ngoài thang 0–10

**Prompt 3: Đọc file điểm giữa kỳ**

Em hãy đọc file 3 và trích xuất thành bảng gồm: Mã sinh viên, họ tên, điểm giữa kỳ. Kiểm tra mã sinh viên trùng, thiếu điểm hoặc điểm không hợp lệ

**Prompt 4: Đọc file điểm cuối kỳ**

Em hãy đọc file 4 và trích xuất thành bảng gồm: Mã sinh viên, họ tên, điểm cuối kỳ, nhận xét giảng viên. Giữ nguyên nội dung nhận xét và đánh dấu các trường hợp thiếu dữ liệu

### 2. Prompt đối chiếu dữ liệu

Em hãy đối chiếu dữ liệu của cả 4 file bằng mã sinh viên làm khóa định danh chính

Yêu cầu:

-   Không ghép dữ liệu chỉ dựa vào họ tên
    
-   Phát hiện sinh viên thiếu điểm ở từng đầu điểm
    
-   Phát hiện mã sinh viên bị trùng hoặc không có trong danh sách gốc
    
-   Kiểm tra điểm có nằm trong khoảng 0–10 không
    
-   Không tự điền hoặc suy đoán điểm còn thiếu
    
-   Những trường hợp bất thường phải được ghi rõ để kiểm tra lại
    

### 3. Prompt tính điểm và phân loại

Em hãy tính điểm tổng kết theo công thức:

-   Chuyên cần: 10%
    
-   Bài tập: 20%
    
-   Giữa kỳ: 30%
    
-   Cuối kỳ: 40%

Công thức:

Điểm tổng kết = Chuyên cần × 0,1 + Bài tập × 0,2 + Giữa kỳ × 0,3 + Cuối kỳ × 0,4.

Quy định:

-   Từ 5,0 điểm trở lên: đạt
    
-   Dưới 5,0 điểm: chưa đạt
    
-   Nếu thiếu bất kỳ đầu điểm nào: Ghi Thiếu dữ liệu, không tính điểm tổng kết
    
-   Làm tròn điểm tổng kết đến 2 chữ số thập phân

### 4. Danh sách các trường hợp bất thường

Em yêu cầu AI kiểm tra và lập danh sách gồm:

-  Sinh viên bị thiếu điểm chuyên cần
    
-  Sinh viên bị thiếu điểm bài tập
    
-  Sinh viên bị thiếu điểm giữa kỳ hoặc cuối kỳ
    
-  Mã sinh viên xuất hiện nhiều lần
    
-  Mã sinh viên không có trong danh sách gốc
    
-  Điểm nhỏ hơn 0 hoặc lớn hơn 10
    
-  Sinh viên có họ tên giống nhau nhưng mã sinh viên khác nhau
