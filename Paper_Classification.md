# BẢNG PHÂN LOẠI 6 HƯỚNG NGHIÊN CỨU FL + SOC (2025–2026)
## Danh sách 6 bài báo phân tích

1. **Cross-Silo Federated Learning in Security Operations Centers for effective malware detection** *(Int. J. of Information Security, Q2, Jul 2025)*  
2. **Mitigating semantic label divergence in federated learning: Obfuscated encoding and alert filtering for security monitoring** *(PLOS ONE, Q1, Dec 2025)*  
3. **PoFQ: A Blockchain Consensus Protocol for Decentralized Federated Learning-Based Threat Hunting** *(Cluster Computing, Q1, Aug 2025)*  
4. **Dataset-centric evaluation of federated intrusion detection models in IoT networks** *(Scientific Reports – Nature, Q1, Jan 2026)*  
5. **Federated Learning–Enhanced SIEM for Multi-SOC Collaboration (FedSIEM)** *(IEEE ISNCC 2026, Jun 2026)*  
6. **CloudTenantShield: Adaptive Federated Learning for Multi-Tenant Cloud Intrusion Detection** *(J. of Supercomputing, Q1, Jul 2026)*

---

## 1. TỔNG QUAN 6 BÀI BÁO

| Tên bài báo | Tạp chí/Hội nghị | Xếp hạng | Thời gian | Trọng tâm chính |
|-------------|------------------|----------|-----------|-----------------|
| Cross-Silo FL for Malware Detection | *Int. J. of Information Security* | Q2 | Jul 2025 | Malware detection, HFL + VFL |
| Mitigating Semantic Label Divergence | *PLOS ONE* | **Q1** | Dec 2025 | Label divergence, KFH, Alert filtering |
| PoFQ – Blockchain for Threat Hunting | *Cluster Computing* | **Q1** | Aug 2025 | Blockchain, Decentralized FL, Threat Hunting |
| Dataset-Centric FL IDS in IoT | *Scientific Reports* (Nature) | **Q1** | Jan 2026 | Benchmarking, IDS, IoT |
| FedSIEM – FL-Enhanced SIEM | IEEE ISNCC 2026 | IEEE | Jun 2026 | SIEM, Multi-SOC Collaboration |
| CloudTenantShield – Adaptive FL for Cloud IDS | *J. of Supercomputing* | **Q1** | Jul 2026 | Cloud IDS, Non-IID, LLM Explainability |

---

## 2. PHÂN LOẠI THEO HƯỚNG NGHIÊN CỨU

### 🔹 Hướng 1: Kiến trúc FL trong SOC

| Tiêu chí | Cross-Silo FL for Malware | PoFQ – Blockchain for Threat Hunting | FedSIEM – FL-Enhanced SIEM |
|----------|---------------------------|---------------------------------------|----------------------------|
| Hướng xử lý | Cross-Silo FL | Decentralized FL | FL + SIEM Integration |
| Vấn đề giải quyết | Không chia sẻ dữ liệu/IP giữa các SOC | Single point of failure, poisoned updates | SIEM tập trung gây privacy/scalability |
| Phương pháp chính | HFL + VFL, cơ chế khuyến khích | Blockchain consensus, DP, cosine similarity | FL-enabled SIEM + blockchain trust |
| Đặc điểm nổi bật | Áp dụng cả HFL và VFL | Loại bỏ aggregation server | Tích hợp với công cụ lõi SOC |
| Điểm yếu | Vẫn cần server trung tâm | Độ trễ blockchain | Phụ thuộc hạ tầng SIEM hiện có |

### 🔹 Hướng 2: Xử lý dữ liệu không đồng nhất

| Tiêu chí | Mitigating Semantic Label Divergence | Dataset-Centric FL IDS in IoT | CloudTenantShield – Adaptive FL for Cloud IDS |
|----------|--------------------------------------|-------------------------------|------------------------------------------------|
| Hướng xử lý | Label Divergence | Non-IID Data | Non-IID + Explainability |
| Vấn đề giải quyết | Semantic inconsistencies do khác nhãn | Dữ liệu không đồng nhất giữa clients | Non-IID skew + kết quả khó giải thích |
| Phương pháp chính | KFH + Filtering Mechanism | FedAvg/Prox/Nova + LSTM/Transformer | FedProx + biLSTM + TinyLLaMA |
| Đặc điểm nổi bật | Dữ liệu thực 14 tổ chức | Đánh giá cross-dataset | LLM tạo natural-language explanations |
| Điểm yếu | Chỉ áp dụng cho IDS alerts | Không đề xuất method mới | Chi phí tính toán LLM cao |

### 🔹 Hướng 3: Bảo mật và Quyền riêng tư

| Tiêu chí | Mitigating Semantic Label Divergence | PoFQ – Blockchain for Threat Hunting | FedSIEM – FL-Enhanced SIEM |
|----------|--------------------------------------|---------------------------------------|----------------------------|
| Hướng xử lý | Model Inversion Protection | Poisoned Updates Detection | Secure Aggregation |
| Vấn đề giải quyết | Rủi ro khôi phục dữ liệu từ mô hình | Client gửi model updates độc hại | Đảm bảo trust giữa các SOC |
| Phương pháp chính | KFH obfuscated encoding | Cosine similarity + Trust Management | Blockchain-based trust mechanisms |
| Đặc điểm nổi bật | Giảm nguy cơ model inversion | Phát hiện gần như hoàn hảo | Tích hợp privacy + trust |
| Điểm yếu | Chỉ bảo vệ ở tầng encoding | Phụ thuộc vào consensus | Chưa rõ cơ chế cụ thể |

### 🔹 Hướng 4: Giải thích và Tin cậy

| Tiêu chí | PoFQ – Blockchain for Threat Hunting | CloudTenantShield – Adaptive FL for Cloud IDS |
|----------|---------------------------------------|------------------------------------------------|
| Hướng xử lý | Trust Management | LLM Explainability |
| Vấn đề giải quyết | Đánh giá độ tin cậy của participants | Numerical alerts khó hiểu cho SOC analysts |
| Phương pháp chính | Trust scoring dựa trên contributions | TinyLLaMA tạo natural-language narratives |
| Đặc điểm nổi bật | Đánh giá historical performance | Giảm cognitive load cho analyst |
| Điểm yếu | Chưa rõ trust metric cụ thể | LLM có thể tạo giải thích sai |

### 🔹 Hướng 5: Đánh giá và Benchmark

| Tiêu chí | Dataset-Centric FL IDS in IoT |
|----------|-------------------------------|
| Hướng xử lý | Dataset-Centric Evaluation |
| Vấn đề giải quyết | Các nghiên cứu chỉ đánh giá trên 1 dataset → không tổng quát |
| Phương pháp chính | 3 dataset IoT, 3 regimes, 3 FL algorithms, 2 backbones |
| Đặc điểm nổi bật | Benchmark toàn diện nhất hiện nay |
| Điểm yếu | Không đề xuất method mới |

### 🔹 Hướng 6: Tích hợp với Hệ thống SOC hiện có

| Tiêu chí | Cross-Silo FL for Malware | FedSIEM – FL-Enhanced SIEM |
|----------|---------------------------|----------------------------|
| Hướng xử lý | FL + Malware Detection | FL + SIEM |
| Vấn đề giải quyết | Tích hợp FL vào SOC cho malware detection | Tích hợp FL vào SIEM – công cụ lõi SOC |
| Phương pháp chính | Cross-Silo FL (HFL + VFL) | FL-enabled SIEM |
| Đặc điểm nổi bật | Gắn với nền tảng Sisyfos thực tế | Cải thiện autonomy, real-time performance |
| Điểm yếu | Chỉ tập trung vào malware | Chưa thử nghiệm trên dữ liệu thực SOC |

---

## 3. TÓM TẮT TỪNG BÀI (2–3 câu)

| Tên bài báo | Main Content (1 câu) | Hướng xử lý | Method chính | Đánh giá |
|-------------|----------------------|-------------|--------------|----------|
| **Cross-Silo FL for Malware Detection** | Cho phép SOC hợp tác phát hiện mã độc mà không chia sẻ dữ liệu/IP | Cross-Silo FL | HFL + VFL, cơ chế khuyến khích | Accuracy 94.99% |
| **Mitigating Semantic Label Divergence** | Xử lý sự khác biệt nhãn cảnh báo giữa các SOC bằng KFH + Filtering | Label Divergence | KFH, Filtering, 14 tổ chức thật | F1 +13.36%, 99% coverage |
| **PoFQ – Blockchain for Threat Hunting** | Dùng Blockchain thay thế server FL để chống poisoned updates | Decentralized FL + Blockchain | PoFQ consensus, DP, cosine similarity | F1 cao, scalable |
| **Dataset-Centric FL IDS in IoT** | Đánh giá FL IDS trên 3 dataset khác nhau để kiểm tra generalization | Benchmarking | FedAvg/Prox/Nova + LSTM/Transformer | Macro-F1 98% in-domain |
| **FedSIEM – FL-Enhanced SIEM** | Tích hợp FL vào SIEM để multi-SOC collaboration | FL + SIEM Integration | FL-enabled SIEM + blockchain trust | Accuracy +6-9%, FP -30% |
| **CloudTenantShield – Adaptive FL for Cloud IDS** | FL IDS cho cloud multi-tenant với LLM explainability | Non-IID + Explainability | FedProx + biLSTM + TinyLLaMA | F1 0.978, Acc 97.87% |

---

## 4. SO SÁNH PHƯƠNG PHÁP

| Phương pháp | Bài báo sử dụng | Mô tả | Ưu điểm | Nhược điểm |
|-------------|----------------|-------|---------|------------|
| **HFL** | Cross-Silo FL for Malware | Cùng đặc trưng, khác mẫu dữ liệu | Đơn giản, hiệu quả | Yêu cầu cùng đặc trưng |
| **VFL** | Cross-Silo FL for Malware | Cùng mẫu, khác đặc trưng | Xử lý được đặc trưng khác nhau | Phức tạp hơn HFL |
| **KFH** | Mitigating Semantic Label Divergence | Mã hóa che giấu vector hóa nhất quán | Giảm model inversion, nhất quán | Chỉ áp dụng cho IDS alerts |
| **Filtering** | Mitigating Semantic Label Divergence | Loại bỏ alerts có label discrepancy | Cải thiện F1 13.36% | Có thể loại bỏ dữ liệu hữu ích |
| **Blockchain** | PoFQ, FedSIEM | Thay thế server trung tâm | Loại bỏ SPoF, chống poisoned updates | Độ trễ cao hơn |
| **Differential Privacy** | PoFQ | Bảo vệ privacy trong FL | Bảo vệ dữ liệu nhạy cảm | Giảm độ chính xác |
| **Cosine Similarity** | PoFQ | Phát hiện updates bất thường | Phát hiện gần như hoàn hảo | Chỉ phát hiện được updates khác biệt lớn |
| **FedProx** | Dataset-Centric, CloudTenantShield | Thêm proximal term cho ổn định non-IID | Ổn định hội tụ | Thêm siêu tham số |
| **FedNova** | Dataset-Centric | Normalized averaging | Giảm communication 15-25% | Phức tạp hơn FedAvg |
| **Transformer** | Dataset-Centric | Backbone cho IDS | Vượt LSTM 1-2% | Nặng hơn LSTM |
| **TinyLLaMA** | CloudTenantShield | LLM tạo natural-language explanations | Giảm cognitive load | Chi phí tính toán cao |

---

## 5. ĐÁNH GIÁ VÀ XẾP HẠNG

| Tên bài báo | Tạp chí/Hội nghị | Xếp hạng | IF (ước) | Độ thực tế | Độ khó đọc | Phù hợp SOC |
|-------------|------------------|----------|----------|------------|------------|-------------|
| Cross-Silo FL for Malware | *IJIS* | Q2 | ~2.5 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Mitigating Semantic Label Divergence | *PLOS ONE* | **Q1** | ~3.7 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| PoFQ – Blockchain for Threat Hunting | *Cluster Computing* | **Q1** | ~3.5 | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| Dataset-Centric FL IDS in IoT | *Scientific Reports* | **Q1** | ~4.6 | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| FedSIEM – FL-Enhanced SIEM | IEEE ISNCC | IEEE | Hội nghị | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| CloudTenantShield – Adaptive FL for Cloud IDS | *J. of Supercomputing* | **Q1** | ~3.2 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |

### Điểm đánh giá chi tiết

| Tiêu chí | Cross-Silo FL for Malware | Mitigating Semantic Label Divergence | PoFQ – Blockchain for Threat Hunting | Dataset-Centric FL IDS in IoT | FedSIEM – FL-Enhanced SIEM | CloudTenantShield – Adaptive FL for Cloud IDS |
|----------|---------------------------|---------------------------------------|---------------------------------------|-------------------------------|----------------------------|------------------------------------------------|
| Tính mới | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Tính thực tiễn | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Chất lượng thực nghiệm | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Dữ liệu thực tế | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| Mã nguồn mở | ❓ | ✅ GitHub | ❓ | ❓ | ❓ | ❓ |

---

## 6. XU HƯỚNG NỔI BẬT 2025–2026

| Xu hướng | Mô tả | Bài báo đại diện | Mức độ hot |
|----------|-------|------------------|------------|
| **Blockchain-FL Integration** | Kết hợp blockchain để giải quyết trust trong môi trường phi tập trung | PoFQ, FedSIEM | 🔥🔥🔥🔥🔥 |
| **LLM for Explainability** | Dùng LLM để giải thích kết quả cho SOC analysts | CloudTenantShield | 🔥🔥🔥🔥🔥 |
| **Cross-Dataset Evaluation** | Đánh giá trên nhiều dataset để kiểm tra generalization | Dataset-Centric FL IDS in IoT | 🔥🔥🔥🔥 |
| **Label Divergence Handling** | Xử lý sự khác biệt nhãn giữa các tổ chức | Mitigating Semantic Label Divergence | 🔥🔥🔥🔥 |
| **Vertical FL ứng dụng** | Áp dụng VFL khi các SOC có đặc trưng khác nhau | Cross-Silo FL for Malware | 🔥🔥🔥 |
| **FL + SIEM Integration** | Tích hợp FL với SIEM – công cụ lõi của SOC | FedSIEM | 🔥🔥🔥🔥 |

---

## 7. GỢI Ý ƯU TIÊN ĐỌC

### Theo mục tiêu nghiên cứu

| Mục tiêu | Ưu tiên #1 | Ưu tiên #2 | Lý do |
|----------|------------|------------|-------|
| Hiểu tổng quan FL + SOC | Dataset-Centric FL IDS in IoT | Cross-Silo FL for Malware | Bài Nature benchmark toàn diện, bài IJIS case study cụ thể |
| Xử lý dữ liệu thực tế | Mitigating Semantic Label Divergence | CloudTenantShield | Dữ liệu 14 tổ chức thật, cloud multi-tenant |
| Giải pháp bảo mật/trust | PoFQ – Blockchain for Threat Hunting | FedSIEM | Blockchain + FL, FL + SIEM |
| Học thuật toán mới | CloudTenantShield | Mitigating Semantic Label Divergence | LLM explainability, KFH |
| Triển khai thực tế | Cross-Silo FL for Malware | FedSIEM | Gắn với Sisyfos, tích hợp SIEM |

### Top 3 ưu tiên tuyệt đối

| Thứ tự | Tên bài báo | Lý do |
|--------|-------------|-------|
| 🥇 | **Mitigating Semantic Label Divergence** | Dữ liệu thực 14 tổ chức, giải quyết vấn đề thực tế nhất của SOC, Q1, có mã nguồn |
| 🥈 | **CloudTenantShield – Adaptive FL for Cloud IDS** | Kết hợp FL + Non-IID + LLM explainability, hiệu suất cao nhất, Q1 |
| 🥉 | **PoFQ – Blockchain for Threat Hunting** | Blockchain + FL giải quyết trust và poisoned updates, tác giả VN, Q1 |

---

## THỐNG KÊ NHANH

| Tiêu chí | Số lượng |
|----------|----------|
| Tổng số bài | 6 |
| Bài Q1 | 4 (Mitigating Semantic Label Divergence, PoFQ, Dataset-Centric, CloudTenantShield) |
| Bài Q2 | 1 (Cross-Silo FL for Malware) |
| Bài IEEE | 1 (FedSIEM) |
| Bài có dữ liệu thực tế | 2 (Mitigating Semantic Label Divergence, CloudTenantShield) |
| Bài có mã nguồn mở | 1 (Mitigating Semantic Label Divergence) |
| Bài có tác giả Việt Nam | 1 (PoFQ) |
| Số hướng nghiên cứu chính | 6 hướng |

---

## KẾT LUẬN

6 bài báo trên đại diện cho **6 hướng nghiên cứu FL + SOC khác nhau**:

| Hướng nghiên cứu | Bài báo đại diện |
|------------------|------------------|
| **Kiến trúc FL** | Cross-Silo FL for Malware, PoFQ, FedSIEM |
| **Xử lý data heterogeneity** | Mitigating Semantic Label Divergence, Dataset-Centric, CloudTenantShield |
| **Bảo mật & Privacy** | Mitigating Semantic Label Divergence, PoFQ, FedSIEM |
| **Explainability & Trust** | PoFQ, CloudTenantShield |
| **Benchmarking** | Dataset-Centric FL IDS in IoT |
| **Tích hợp SOC** | Cross-Silo FL for Malware, FedSIEM |

---

## LINK TRUY CẬP NHANH

| Tên bài báo | Link |
|-------------|------|
| Cross-Silo FL for Malware | https://link.springer.com/article/10.1007/s10207-025-01101-4 |
| Mitigating Semantic Label Divergence | https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0338488 |
| PoFQ – Blockchain for Threat Hunting | https://dl.acm.org/doi/10.1007/s10586-025-05247-7 |
| Dataset-Centric FL IDS in IoT | https://www.nature.com/articles/s41598-025-33596-1 |
| FedSIEM – FL-Enhanced SIEM | https://ieeexplore.ieee.org/document/11647961 |
| CloudTenantShield – Adaptive FL for Cloud IDS | https://link.springer.com/article/10.1007/s10791-026-10366-9 |
