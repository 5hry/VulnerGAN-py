# Filename: data
## Description: Lưu trữ dữ liệu
    - success.npy Các mẫu bất thường mà NIDS phát hiện chính xác
    - fail.npy Các mẫu bất thường mà NIDS phát hiện sai
    - epoch=1 Huấn luyện trực tuyến với toàn bộ dữ liệu huấn luyện, mỗi lô dữ liệu được huấn luyện đủ 1 lần
    - epoch=5 Huấn luyện trực tuyến với toàn bộ dữ liệu huấn luyện, mỗi lô dữ liệu được huấn luyện đủ 5 lần
    - .csv Kết quả phân loại của mô hình (ghi chú nhãn)

# Filename: saved_model
## Description: Lưu trữ các mô hình đã được huấn luyện

# Filename: .txt
## Description: Ghi chú quá trình huấn luyện

# Filename: NIDS_MLP.py / NIDS_DNN.py
## Description:
    - Huấn luyện mô hình MLP/DNN, ghi chú quá trình, lưu kết quả

# Filename: test_MLP/DNN_bypass.py
## Description:
    - Kiểm tra tỷ lệ né tránh của mẫu tấn công đối với MLP/DNN

# Filename: train_NIDS.py
## Description:
    - Quá trình huấn luyện các mô hình máy học khác
    -
    "gnb": GaussianNB,  # Gaussian Naive Bayes
    "knn": KNeighborsClassifier,  # K-nearest neighbors
    "gbc": GradientBoostingClassifier,  # Gradient Boosting Classifier
    "rfc": RandomForestClassifier,  # Random Forest Classifier
    "lr": LinearRegression,  # Linear Regression
    "svc": SVC,  # Support Vector Classifier
    "dtc": DecisionTreeClassifier  # Decision Tree Classifier

# Filename: test_bypass.py
## Description:
    - Kiểm tra tỷ lệ né tránh của mẫu tấn công đối với các mô hình khác
