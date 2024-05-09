# Filename: poisoning_record
## Description:
    - Ghi chú quá trình huấn luyện trong quá trình pha hoá

# Filename: saved_models
## Description:
    - Lưu trữ các mô hình trong quá trình pha hoá

# Filename: poisoning_NIDS_MLP/DNN.py
## Description:
    - Pha hoá mô hình MLP/DNN và lưu kết quả tương ứng

# Filename: poisoning_NIDS_MLP/DNN_mse.py
## Description:
    - Pha hoá mô hình MLP/DNN và ghi chú thông tin giá trị MSE trong quá trình huấn luyện
    - Tính toán giá trị MSE trong quá trình huấn luyện
    - mse = mean_squared_error(target, predicted)

# Filename: unpoisoning_NIDS_MLP/DNN.py
## Description:
    - Huấn luyện bình thường (không pha hoá) mô hình MLP/DNN và lưu kết quả tương ứng

# Filename: unpoisoning_NIDS_MLP/DNN_mse.py
## Description:
    - Huấn luyện bình thường (không pha hoá) mô hình MLP/DNN và ghi chú thông tin giá trị MSE trong quá trình huấn luyện
    - Tính toán giá trị MSE trong quá trình huấn luyện
    - mse = mean_squared_error(target, predicted)
