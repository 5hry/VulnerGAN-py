# VulnerGAN-py
A backdoor attack by vulnerability amplification on online machine learning-based network intrusion detection system



# Filename: data
## Description:
    1. Lưu trữ dữ liệu
    2. Bộ dữ liệu gốc CIC-IDS-2017
    3. Bộ dữ liệu huấn luyện, kiểm tra và kiểm định chéo được tạo ra
    4. Bộ dữ liệu mẫu đối kháng

# Filename: data_process
## Description:
    1. Tiền xử lý dữ liệu:
    - extract_traffic_types.py input: data/cic_2017/resource/       output: data/cic_2017/traffic_types/
    - create_datasets.py       input: data/cic_2017/traffic_types/  output: data/cic_2017/data_sets/
    2. Trích xuất lưu lượng bất thường từ tập dữ liệu huấn luyện (dùng để tạo mẫu đối kháng sau này):
    - create_attack_datasets.py   
	- input: data/cic_2017/data_sets/train_set.csv
    	- output: data/cic_2017/data_sets/attack_set.csv
    3. Chia tập mẫu đối kháng theo tỷ lệ (có thể tùy chỉnh) thành tập huấn luyện và tập kiểm tra: tập huấn luyện để đầu độc, tập kiểm tra để đánh giá tỷ lệ né tránh mẫu đối kháng/ tạo tập kiểm định chuẩn để kiểm tra độ chính xác của mô hình:
    - split_adv_datasets.py 
	- input: data/cic_2017/adver_sets/adver_example.csv
    	- output: data/cic_2017/adver_sets/adver_train.csv & data/cic_2017/adver_sets/adver_test.csv

		
# Filename: nids_models
## Description:
    1. Huấn luyện mô hình
    2. Lấy mẫu bất thường mà mô hình trong lần huấn luyện cuối cùng có thể phân loại đúng/sai:
        - NIDS_MLP/DNN.py          
        - input: data/cic_2017/data_sets/      
        - output: nids_models/data/ & nids_models/saved_model/
    3. Kiểm tra tỷ lệ né tránh của mô hình đối với các bộ dữ liệu khác nhau:
        - test_MLP/DNN_bypass.py     
        - input: bộ dữ liệu được tạo                    
        - output: tỷ lệ né tránh


# Filename: GAN
## Description:
    1. Tạo mẫu đối kháng
    2. Quá trình huấn luyện GAN
    3. train_GAN.py
        - input: nids_models/data/...success....npy & nids_models/data/...fail....npy
        - output: GAN/discriminator/ & GAN/generator (logs_gan lưu nhật ký）
    4. Quá trình tạo mẫu đối kháng
    5. generate_adver.py
        - input: data/cic_2017/data_sets/attack_set.csv
        - output: put: data/cic_2017/adver_sets/..._adver_example.csv
    6. find_attack.py - Lọc tính tấn công, sử dụng trong quá trình huấn luyện GAN, tạo mới mẫu có giữ lại lỗ hổng tấn công, kiểm soát khoảng cách Euclid giữa mẫu mới và input gốc, tạo thêm nhiều mẫu có khả năng đối kháng
    7. find_weakness.py - Lọc tính lừa đảo, sử dụng trong quá trình huấn luyện GAN, tạo mới mẫu lỗ hổng, mở rộng thư viện mẫu lỗ hổng, tạo thêm nhiều mẫu có khả năng đối kháng


# Filename: poisoning
## Description:
    1. Tấn công đầu độc (cách thức tấn công có thể tự thiết kế)
    2. poisoning_NIDS_MLP/DNN.py
    - (Không đầu độc) input: data/cic_2017/data_sets/ bao gồm tập huấn luyện, tập kiểm tra, tập kiểm định chéo
    - (Đầu độc) input: data/cic_2017/data_sets/ & data/cic_2017/adver_sets/adver_train.csv
    - output: ghi lại mô hình tại poisoning/saved_models/
    3. Ghi lại quá trình đầu độc (thông tin xuất ra từ bảng điều khiển, tự sao chép và dán, lưu vào file txt) tại poisoning/poisoning_record/

   
# Filename: model _steal
## Description:
    1. Tạo mô hình bóng
    2. Sử dụng DNN để rút trích mô hình từ NIDS gốc
    3. Input là các đặc trưng của mẫu huấn luyện và kết quả dự đoán của mô hình gốc, output là các mô hình thay thế DNN cho từng mô hình
    4. get_result.py - Lấy kết quả huấn luyện của mô hình gốc/thay thế
    5. get_targets.py - Lấy input cần thiết cho việc huấn luyện GAN (success - các trường hợp NIDS có thể phán đoán chính xác) và target (fail - các lỗi mà NIDS phán đoán sai)

