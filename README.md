Image Colorization using ResNet + U-Net

Dự án này triển khai một mô hình tô màu ảnh tự động, kết hợp ResNet để trích xuất đặc trưng và U-Net để tái tạo ảnh màu từng pixel, giúp chuyển ảnh grayscale sang ảnh màu.

kết quả mẫu:

<img width="1117" height="751" alt="image" src="https://github.com/user-attachments/assets/9bd51d78-f511-45d2-b4d7-c8f57f2889a3" />

Nhận xét:

* Mô hình màu sắc bị pha loãng, một số vùng quá bão hòa, một số vùng nhạt màu.
* Quá trình huấn luyện sử dụng hàm loss MSE, mặc dù loss hội tụ nhưng vẫn dẫn đến ảnh có màu không tự nhiên.

hướng giải quyết:

* Sử dụng hàm loss cho bài toán tô màu theo gợi ý trong bài báo [Zhang et al., 2016](https://arxiv.org/pdf/1603.08511) Dùng loss phân loại trong không gian màu ab thay vì MSE để mô hình học được phân bố màu hợp lý hơn.
* Thử data augmentation và histogram equalization để tăng độ phong phú của màu trong dữ liệu huấn luyện.
* Thử nghiệm với perceptual loss hoặc adversarial loss để tạo màu sắc và kết cấu tự nhiên hơn.
