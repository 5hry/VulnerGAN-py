# Filename: extract_traffic_types.py
## Description:
    - Đọc tệp dữ liệu gốc .csv
    - Loại bỏ các bản ghi chứa giá trị NAN hoặc INF
    - Nhóm các bản ghi theo loại nhãn
    - Phân loại theo loại luồng để tạo ra tệp .csv mới

# Filename: create_datasets.py
## Description:
    - Đọc tệp .csv được tạo theo loại luồng
    - Chỉ định số lượng bản ghi cần trích xuất
    - Chỉ định tỷ lệ tập huấn luyện, tập kiểm định chéo và tập kiểm tra
    - Tạo các tập dữ liệu tương ứng

# Filename: tools.py
## Description:
    - Tùy chỉnh cách đọc tệp .csv
    - Phân loại nhãn thành hai lớp
    - Chuẩn hóa dữ liệu

# Filename: my_dataset.py
## Description:
    - Được sử dụng để đọc tập dữ liệu tương ứng cho các thí nghiệm sau này

# Filename: create_attack_datasets.py
## Description:
    - Trích xuất tất cả các loại luồng tấn công (ngoại trừ nhãn benign)

# Filename: split_adv_datasets.py
## Description:
    - Chia tách tập huấn luyện và tập kiểm tra của mẫu tấn công theo tỷ lệ đã đặt
    - Tập huấn luyện được sử dụng để tạo độc hại
    - Tập kiểm tra được sử dụng để tạo ra tập kiểm định chuẩn hoặc kiểm tra hiệu ứng phóng đại lỗ hổng
