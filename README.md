## Tác giả

- Vũ Kim Gia Minh - 22000109
- Dương Đức Vương - 22000133
- Nguyễn Thị Hoàng Yến - 22000134
- Đỗ Quốc An - 22000067

**Học phần**: Thiết kế và đánh giá thuật toán  
**Giảng viên**: PGS.TS. Nguyễn Thị Hồng Minh, ThS. Trần Bá Tuấn, CN. Đặng Trung Du

# Bài toán xếp lịch làm việc cho nhân viên

## Mô tả dự án

Dự án này thực hiện việc tối ưu hóa xếp lịch làm việc cho nhân viên sử dụng 4 phương pháp thuật toán khác nhau:
- **Brute Force (Vét cạn)**
- **Branch and Bound (Nhánh cận)**
- **Greedy (Tham lam)**
- **Dynamic Programming (Quy hoạch động)**

### Bài toán

Xếp lịch nhân viên cho các ca làm việc trong tuần với các ràng buộc:
- **3 ca sáng (Ca 1)**
- **4 ca chiều (Ca 2)**
- **2 ca tối (Ca 3)**

### Mục tiêu tối ưu
1. Tối đa hóa tổng điểm đánh giá năng lực
2. Ưu tiên ít ca hơn nếu điểm bằng nhau
3. Tránh ca rời (sáng + tối mà không có chiều)
4. Tôn trọng lịch đăng ký của nhân viên

## Cấu trúc dự án

```
Employee_scheduling.ipynb    # File chính chứa tất cả thuật toán
nhanvien_schedule.xlsx          # Dữ liệu mẫu nhân viên
```

## Yêu cầu hệ thống

### Thư viện Python cần thiết
```python
pandas
numpy
matplotlib
openpyxl
itertools
time
collections
typing
heapq
```

### Cài đặt
```bash
pip install pandas numpy matplotlib openpyxl
```

## Hướng dẫn sử dụng

### 1. Chuẩn bị dữ liệu

#### Định dạng file Excel đầu vào:
- **Cột Day 1 - Day 7**: Lịch đăng ký ca của nhân viên
  - `'0'`: Không đăng ký ca nào
  - `'1'`: Đăng ký ca sáng
  - `'2'`: Đăng ký ca chiều
  - `'3'`: Đăng ký ca tối
  - `'12'`: Đăng ký ca sáng + chiều
  - `'123'`: Đăng ký cả 3 ca
- **Rate_Ca1/Rate_Morning**: Đánh giá năng lực ca sáng (1-3)
- **Rate_Ca2/Rate_Afternoon**: Đánh giá năng lực ca chiều (1-3)
- **Rate_Ca3/Rate_Evening**: Đánh giá năng lực ca tối (1-3)

### 2. Sinh dữ liệu

```python
# Sinh dữ liệu cho n nhân viên
generate_schedule(n=15, filename='schedule.xlsx', seed=42)
```

### 3. Chạy thuật toán

#### Brute Force
```python
# Đọc file và chạy thuật toán vét cạn
df = pd.read_excel('nhanvien_schedule.xlsx')
print_schedule_for_day(df)
```

#### Branch and Bound
```python
# Tối ưu hóa với thuật toán nhánh cận
optimize_schedule15()
```

#### Greedy
```python
# Thuật toán tham lam
greedy_schedule_from_existing_data('nhanvien_schedule.xlsx', NEED=(3,4,2))
```

#### Dynamic Programming
```python
# Quy hoạch động (xem code trong notebook)
# Đọc dữ liệu và chạy DP cho từng ngày
```

### 4. Đo hiệu suất

#### Đo thời gian chạy:
```python
# Ví dụ cho Branch and Bound
total_time = run_schedule(df, NEED=(3,4,2), return_score=False)
```

#### Đo điểm tối ưu:
```python
# Ví dụ cho Greedy
total_score = run_schedule_greedy(df, NEED=(3,4,2), return_score=True)
```

### 5. Kết quả thực nghiệm
- Tất cả kết quả thực nghiệm nằm trong thư mục "thực nghiệm"

## Lưu ý quan trọng

1. **File paths**: Đảm bảo đường dẫn file đúng
2. **Format dữ liệu**: Kiểm tra định dạng Excel đầu vào
3. **Memory**: DP và B&B có thể tốn nhiều RAM với dữ liệu lớn
4. **Seed**: Sử dụng seed để tái tạo kết quả

