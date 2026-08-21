# BÁO CÁO PHÂN TÍCH HỌC THUẬT: FLIC (PERSONALIZED FEDERATED LEARNING ON HETEROGENEOUS FEATURE SPACES)

## 1. ABSTRACT (Tóm tắt)
*   **Bài toán nghiên cứu:** Hầu hết các phương pháp học liên bang cá nhân hóa (Personalised FL) hiện nay đều giả định dữ liệu thô của tất cả các thiết bị biên (clients) cùng chung một không gian đặc trưng (tức là cùng cấu trúc hay schema) [1]. Tuy nhiên, trong thực tế, các client thu thập và lưu trữ dữ liệu trên các hệ thống riêng biệt, dẫn đến sự không đồng nhất về mặt biểu diễn dữ liệu (khác biệt về số chiều hoặc ý nghĩa ngữ nghĩa của các tọa độ đặc trưng) [1, 2].
*   **Tầm quan trọng:** Giả định cùng không gian đặc trưng là quá khắt khe đối với thực tế khi dữ liệu của client bị thiếu trường thông tin, số chiều khác nhau, hoặc đã bị biến đổi qua các phép chuẩn hóa, tỉ lệ, hoặc tổ hợp tuyến tính khác nhau [2, 3]. Sự không đồng nhất này khiến các thuật toán FL truyền thống hoặc thậm chí các phương pháp cá nhân hóa chuẩn không thể áp dụng trực tiếp do tham số mô hình của các client không tương thích để so sánh hay tổng hợp trực tiếp trên server trung tâm [1].
*   **Phương pháp/Ý tưởng chính:** Nghiên cứu đề xuất khung làm việc mang tên **FLIC** (Personalised Federated Learning on Heterogeneous Feature Spaces) [2]. Ý tưởng cốt lõi là ánh xạ dữ liệu thô của từng client vào một không gian ẩn chung (common latent space) có số chiều cố định thông qua các **hàm nhúng cục bộ học được** (local embedding functions) [2]. Để đảm bảo dữ liệu mang cùng ý nghĩa ngữ nghĩa rơi vào cùng một vùng không gian ẩn, FLIC thực hiện **căn chỉnh phân phối** (distribution alignment) bằng cách ép phân phối dữ liệu nhúng cục bộ tiến sát tới một **phân phối neo ẩn chung** (latent anchor distribution) được học liên bang thông qua cơ chế **trọng tâm Wasserstein** (Wasserstein barycenter) trên server [2]. Sau khi căn chỉnh phân phối, học liên bang cá nhân hóa (như FedRep) sẽ được áp dụng trên không gian ẩn tương thích này [2].
*   **Kết quả nổi bật:** FLIC vượt trội hơn hẳn so với các phương pháp đối sánh (Local learning và FedHeNN) trên cả dữ liệu mô phỏng lẫn dữ liệu thực tế [2]. Trong các thiết lập thử nghiệm khó khăn nhất (nhiều client, ít lớp dữ liệu trên từng client), FLIC giúp cải thiện độ chính xác phân loại từ **3% đến hơn 5%** [3]. Ngoài ra, nghiên cứu chứng minh được tốc độ hội tụ tuyến tính phi tiệm cận của biểu diễn toàn cục được học về không gian con thực tế trong một thiết lập lý thuyết đơn giản hóa [3].
*   **Giải thích đơn giản cho sinh viên:** Hãy tưởng tượng một lớp học trực tuyến nơi sinh viên đến từ nhiều quốc gia khác nhau. Người thì ghi chép bằng tiếng Anh, người dùng tiếng Pháp, người lại dùng tiếng Việt, và độ dài ghi chép của mỗi người cũng khác nhau (đây là "không gian đặc trưng dị dạng") [3]. Để học nhóm mà không phải chia sẻ ghi chép gốc cho nhau (bảo mật), họ cần một "ngôn ngữ trung gian" chung (không gian ẩn) [3]. Mỗi sinh viên sẽ tự học một "bộ dịch" riêng của mình để dịch ghi chép của mình sang ngôn ngữ chung này [3]. Để đảm bảo từ "quả táo" trong tiếng Anh hay tiếng Pháp sau khi dịch đều khớp với khái niệm "quả táo" chung, họ dùng các "hình ảnh mẫu" chung được thống nhất cả nhóm làm mốc (phân phối neo) [3, 4]. Sau khi mọi người dịch về cùng một ngôn ngữ và định chuẩn đúng nghĩa, họ có thể dễ dàng trao đổi kiến thức với nhau qua một người trưởng nhóm (server) để cải thiện mô hình học tập cá nhân của từng người [4].

---

## 2. CONTRIBUTIONS (Đóng góp khoa học)
Nghiên cứu mang lại 4 đóng góp chính cốt lõi:

1.  **Hình thức hóa bài toán học liên bang ngang cá nhân hóa trên không gian đặc trưng dị dạng (Personalised Horizontal FL on Heterogeneous Feature Spaces):**
    *   *Đề xuất:* Lần đầu tiên chính thức hóa toán học bài toán học liên bang ngang cá nhân hóa khi các client sở hữu dữ liệu thô nằm ở các không gian có số chiều khác nhau hoặc ý nghĩa tọa độ khác nhau, đồng thời có sự lệch phân phối nhãn cục bộ [4].
    *   *Khác biệt:* Các phương pháp học liên bang cá nhân hóa trước đây (như FedRep, FedAvg-FT, L2GD) hoàn toàn giả định các client chia sẻ chung một cấu trúc không gian đặc trưng thô giống hệt nhau [4].
    *   *Giải quyết:* Khắc phục sự thiếu tương thích trực tiếp về mặt dữ liệu đầu vào giữa các client, khiến các tham số mô hình không thể so sánh hay tổng hợp trực tiếp [4].
    *   *Tầm quan trọng:* Cho phép một client tận dụng tri thức từ dữ liệu của các client khác ngay cả khi các bên lưu trữ dữ liệu dưới các định dạng, cấu trúc khác nhau, mở rộng đáng kể phạm vi ứng dụng thực tế của FL [5].

2.  **Khung làm việc và thuật toán FLIC:**
    *   *Đề xuất:* Framework FLIC tích hợp cơ chế học các hàm nhúng cục bộ cùng với việc học phân phối neo ẩn toàn cục theo phương thức liên bang [5].
    *   *Khác biệt:* So với các phương pháp căn chỉnh phân phối tập trung, FLIC thực hiện phân tán không chia sẻ dữ liệu [5]. So với FedHeNN (dùng tập dữ liệu RAD dùng chung chia sẻ từ server), FLIC không cần server phải phân phối tập dữ liệu thô tham chiếu, tránh được vấn đề bùng nổ số chiều và nguy cơ bảo mật rò rỉ dữ liệu [5].
    *   *Giải quyết:* Đảm bảo dữ liệu nhúng của các client có thể so sánh được và đồng nhất về mặt ngữ nghĩa trong không gian ẩn chung [5].
    *   *Tầm quan trọng:* Giáp tích hợp cơ chế căn chỉnh phân phối một cách mượt mà vào bất kỳ thuật toán PFL hiện đại nào (ví dụ: FedRep, L2GD, FedAvg-FT) [5, 6].

3.  **Bảo đảm lý thuyết hội tụ phi tiệm cận (Non-asymptotic Convergence Guarantees):**
    *   *Đề xuất:* Đưa ra phân tích lý thuyết chứng minh rằng trong một kịch bản hồi quy tuyến tính đơn giản hóa với các đặc trưng Gauss, FLIC có khả năng khôi phục chính xác không gian con tiềm ẩn thực tế (chỉ sai lệch tối đa một phép biến đổi dấu) [6].
    *   *Khác biệt:* Cung cấp bảo đảm toán học vững chắc thay vì chỉ dựa vào các kết quả thử nghiệm thực nghiệm (heuristic) [6].
    *   *Giải quyết:* Chứng minh mặt toán học cho việc tối ưu hóa đồng thời hàm nhúng cục bộ và biểu diễn toàn cục trong FL [6].
    *   *Tầm quan trọng:* Đảm bảo độ tin cậy và tính đúng đắn về mặt lý thuyết của thuật toán tối ưu hóa trong FLIC [6].

4.  **Thực nghiệm toàn diện trên dữ liệu mô phỏng và dữ liệu thực tế:**
    *   *Đề xuất:* Đánh giá hiệu năng của FLIC trên các tập dữ liệu đa dạng (Toy noisy features, Toy linear mapping, MNIST-USPS, TextCaps) [6].
    *   *Khác biệt:* Thiết lập các bài thử nghiệm có độ dị dạng đặc trưng cực kỳ cao (khác biệt kích thước ảnh, khác biệt phương thức ảnh/văn bản) kết hợp sự lệch nhãn cục bộ [6, 7].
    *   *Giải quyết:* Minh chứng tính hiệu quả vượt trội của FLIC so với các baseline học cục bộ và biến thể thích ứng FedHeNN [7].
    *   *Tầm quan trọng:* Xác nhận khả năng hoạt động thực tế và độ bền bỉ của framework trước các yếu tố như tỷ lệ tham gia của client [7].

### Định nghĩa các thuật ngữ chính:
*   **Vấn đề heterogeneous/incomparable feature spaces:** Hiện tượng không gian dữ liệu thô $\mathcal{X}_i$ của các client khác nhau không cùng một hệ đo lường hay số chiều (ví dụ: client 1 dùng ảnh 28x28, client 2 dùng ảnh 16x16, hoặc đặc trưng văn bản 768 chiều vs đặc trưng ảnh 512 chiều) [7, 8].
*   **FLIC framework:** Khung làm việc cho phép học liên bang cá nhân hóa trên không gian đặc trưng dị dạng bằng cách kết hợp hàm nhúng cục bộ, căn chỉnh phân phối qua phân phối neo ẩn, và tổng hợp trọng tâm Wasserstein trên server [8].
*   **Local embedding functions (Hàm nhúng cục bộ $\phi_i$):** Hàm ánh xạ dữ liệu thô từ không gian riêng của từng client về một không gian ẩn chung có số chiều cố định [8].
*   **Common latent feature space (Không gian ẩn chung $\Phi$):** Không gian vector đích cố định có số chiều thấp hơn dữ liệu gốc, nơi đặc trưng từ mọi client trở nên tương thích và có thể so sánh [8].
*   **Anchor distributions (Phân phối neo ẩn $\mu_c$):** Các phân phối xác suất tham chiếu (mỗi lớp $c$ có một phân phối neo $\mu_c$) được học liên bang, đóng vai trò "bộ hiệu chuẩn vạn năng" để căn chỉnh đặc trưng nhúng của các client [8].
*   **Distribution alignment (Căn chỉnh phân phối):** Quá trình ép phân phối dữ liệu nhúng có điều kiện lớp của các client tiến gần đến phân phối neo chung để giữ nguyên cấu trúc ngữ nghĩa [8].
*   **Wasserstein distance (Khoảng cách Wasserstein $W_2$):** Thước đo đo lường khoảng cách giữa hai phân phối xác suất dựa trên chi phí vận chuyển tối thiểu [8]. Thước đo này luôn hữu hạn kể cả khi hai phân phối không giao nhau về mặt giá đỡ (support), giúp tối ưu hóa cực kỳ ổn định trong giai đoạn khởi tạo mạng [8].
*   **Wasserstein barycenter (Trọng tâm Wasserstein):** "Điểm trung tâm" của một tập hợp các phân phối xác suất theo hệ đo lường Wasserstein, được server sử dụng để tổng hợp các phân phối neo cập nhật từ các client [8].
*   **Personalization (Cá nhân hóa):** Kỹ thuật giải quyết sự không đồng nhất về thống kê (statistical heterogeneity) còn sót lại trong không gian ẩn bằng cách học các tham số mô hình riêng cho từng client (ví dụ: lớp phân loại cuối giữ riêng) phối hợp với các tham số biểu diễn chia sẻ toàn cục [8].

---

## 3. METHOD (Phương pháp nghiên cứu)

### Pipeline xử lý dữ liệu từ đầu đến cuối:
```
Client data ──> Local embedding ──> Common latent space ──> Distribution alignment
                                                                     │
                                                                     ▼
Personalized model <── Server aggregation <── Client update <── Local model training
```

1.  **Client data (Dữ liệu cục bộ):** Mỗi client $i$ giữ một tập dữ liệu thô riêng $D_i$ với các vector đặc trưng sống trong các không gian dị dạng $\mathcal{X}_i \subseteq \mathbb{R}^{k_i}$ (số chiều $k_i$ khác nhau) [8]. Dữ liệu này không bao giờ rời khỏi client [8].
2.  **Local embedding (Nhúng cục bộ):** Client chuyển đổi dữ liệu thô bằng cách đưa qua hàm nhúng cục bộ $\phi_i(x_i)$ [8]. Đây là một mạng nơ-ron đóng vai trò "máy dịch" cục bộ để biến dữ liệu định dạng riêng thành định dạng chung [3, 8].
3.  **Common latent space (Không gian ẩn chung):** Đầu ra của hàm nhúng là một vector nằm trong không gian ẩn chung $\Phi \subseteq \mathbb{R}^k$ với số chiều $k$ cố định cho tất cả các client [8].
4.  **Distribution alignment (Căn chỉnh phân phối):** Để đảm bảo "máy dịch" của các client dịch chuẩn xác và thống nhất ngữ nghĩa, client thực hiện ép phân phối của dữ liệu sau nhúng ứng với lớp $c$ (ký hiệu là $\nu_{\phi_i}^{(c)}$) tiến sát tới phân phối neo $\mu_c$ bằng cách giảm thiểu khoảng cách Wasserstein bậc 2 ($W_2^2$) [8, 9]. Ép các điểm dữ liệu cùng nhãn lớp của các client khác nhau tập trung vào cùng một vùng không gian được đánh dấu bởi phân phối neo [3, 9].
5.  **Local model training (Huấn luyện mô hình cục bộ):** Sau khi dữ liệu đã nằm an toàn trong không gian ẩn tương thích, client đưa đặc trưng này qua mô hình phân loại cá nhân hóa cục bộ $g_{\theta_i}^{(i)}$ để dự đoán nhãn lớp và tính toán loss phân loại [9].
6.  **Client update (Cập nhật cục bộ):** Client cập nhật các tham số cục bộ bao gồm hàm nhúng $\phi_i$ và phần cá nhân hóa $\beta_i$ trong $M$ bước [9]. Sau đó, client tính toán cập nhật một bước cho các tham số toàn cục (biểu diễn chia sẻ $\alpha_i$ và phân phối neo cục bộ $\mu_{i, c}$) để tránh hiện tượng trôi client (client drift) [9].
7.  **Server aggregation (Tổng hợp trên server):** Server nhận các bản cập nhật toàn cục từ các client đang hoạt động [9]. Server thực hiện trung bình cộng có trọng số để cập nhật biểu diễn chia sẻ toàn cục $\alpha^{(t+1)}$, đồng thời giải bài toán Wasserstein barycenter để cập nhật phân phối neo toàn cục mới $\mu_c^{(t+1)}$ [9].
8.  **Personalized model (Mô hình cá nhân hóa hoàn chỉnh):** Vòng lặp tiếp tục cho đến khi hội tụ. Mỗi client sở hữu một mô hình cá nhân hóa hoàn chỉnh gồm "bộ dịch cục bộ" $\phi_i$ đã được căn chỉnh và "đầu phân loại cá nhân hóa" $\beta_i$ để phục vụ suy luận [9].

### Giải thích các ký hiệu và khái niệm toán học:
*   **$\phi_i$:** Hàm nhúng cục bộ (thường là một mạng nơ-ron kết nối đầy đủ hoặc CNN) ánh xạ dữ liệu thô $x_i \in \mathbb{R}^{k_i}$ về không gian ẩn $\Phi \in \mathbb{R}^k$ [9].
*   **$\alpha_i$ và $\beta_i$:** Theo cơ chế FedRep, mô hình được tách làm hai phần [9]. $\alpha$ là biểu diễn chia sẻ toàn cục (các lớp đầu của mô hình phân loại nhận đầu vào từ không gian ẩn, được server tổng hợp) [9]. $\beta_i$ là lớp phân loại cuối cùng (classifier head) được giữ riêng tại mỗi client để cá nhân hóa [9].
*   **$\mu_c$:** Phân phối neo ẩn chung cho lớp $c$ [9]. Giả định là phân phối Gauss $\mathcal{N}(v_c, \Sigma_c)$ [9].
*   **Anchor distribution dùng để làm gì:** Đóng vai trò làm "bộ hiệu chuẩn vạn năng" trung gian để căn chỉnh dữ liệu nhúng của các client, ngăn hiện tượng dữ liệu cùng nhãn lớp từ các client khác nhau bị phân tán hỗn loạn trong không gian ẩn [9].
*   **Wasserstein distance dùng để làm gì:** Dùng làm số hạng phạt (regularization) trong hàm loss cục bộ để đo lường và giảm thiểu sai khác giữa phân phối dữ liệu nhúng của client và phân phối neo [9]. Do có giả định Gauss, khoảng cách này có công thức đóng cực kỳ tiện lợi:
    $$W_2^2(\mu_c, \nu_{\phi_i}^{(c)}) = \|v_c - m_i^{(c)}\|^2 + \mathfrak{B}^2(\Sigma_c, \Sigma_i^{(c)})$$ [9].
*   **Wasserstein barycenter dùng để làm gì:** Dùng trên server để tìm ra phân phối "trung tâm" tối ưu nhất từ các phân phối neo cục bộ do các client gửi lên, đóng vai trò là phép tổng hợp phân phối toàn cục [9].
*   **Server aggregate những gì:** Server nhận và tổng hợp:
    1.  Tham số biểu diễn chia sẻ $\alpha = \frac{b}{|A_{t+1}|} \sum_{i \in A_{t+1}} \omega_i \alpha_i^{(t+1)}$ [9].
    2.  Vector trung bình của phân phối neo $v_c = \frac{b}{|A_{t+1}|} \sum_{i \in A_{t+1}} \omega_i v_{i, c}^{(t+1)}$ [9].
    3.  Thừa số Cholesky $L_c = \frac{b}{|A_{t+1}|} \sum_{i \in A_{t+1}} \omega_i L_{i, c}^{(t+1)}$ để tái tạo ma trận hiệp phương sai $\Sigma_c = L_c L_c^\top$ [9, 10].
*   **Client cập nhật những gì:** Client huấn luyện cục bộ bằng thuật toán lan truyền ngược để cập nhật:
    1.  Tham số hàm nhúng $\phi_i$ [10].
    2.  Tham số đầu phân loại cục bộ $\beta_i$ [10].
    3.  Thực hiện một bước cập nhật cục bộ cho $\alpha_i$ và phân phối neo $\mu_{i, c}$ trước khi gửi về server [10].
*   **Tại sao cách này xử lý được heterogeneous feature spaces:** Bởi vì mọi sự khác biệt về số chiều hay ngữ nghĩa của dữ liệu thô cục bộ đều đã được tiêu biến sau khi đi qua hàm nhúng cục bộ $\phi_i$ để chuyển hóa về không gian ẩn chung $\Phi$ [10]. Việc căn chỉnh phân phối qua phân phối neo đảm bảo không gian ẩn chung này có cấu trúc ngữ nghĩa nhất quán, cho phép server tổng hợp mô hình một cách hợp lý [10].

### Giải thích thuật toán FLIC theo từng bước truyền thông:
*   **Bước 1 (Khởi tạo):** Server khởi tạo các tham số toàn cục $\alpha^{(0)}$ và phân phối neo $\mu_{1:C}^{(0)}$ [10]. Các client khởi tạo hàm nhúng $\phi_i^{(0,0)}$ và classifier head $\beta_i^{(0,0)}$ [10].
*   **Bước 2 (Lựa chọn Client):** Ở mỗi vòng truyền thông $t$, server chọn ngẫu nhiên một tập hợp các client đang hoạt động $A_{t+1}$ [10].
*   **Bước 3 (Gửi tham số - Server -> Client):** Server gửi biểu diễn toàn cục $\alpha^{(t)}$ và phân phối neo hiện tại $\mu_{1:C}^{(t)}$ cho các client được chọn [10].
*   **Bước 4 (Huấn luyện cục bộ):** Mỗi client $i$ chạy $M$ bước gradient descent để tối ưu hóa tham số cục bộ $\phi_i$ và $\beta_i$ dựa trên dữ liệu cục bộ của mình [10].
*   **Bước 5 (Cập nhật tham số toàn cục cục bộ):** Client chạy đúng 1 bước gradient descent để tính toán phiên bản cập nhật cục bộ của biểu diễn chia sẻ $\alpha_i^{(t+1)}$ và phân phối neo cục bộ $\mu_{i, 1:C}^{(t+1)}$ [10].
*   **Bước 6 (Truyền ngược - Client -> Server):** Client gửi $\alpha_i^{(t+1)}$ và các tham số phân phối neo cục bộ (gồm vector trung bình $v_{i,c}$ và ma trận Cholesky $L_{i,c}$) về server [10].
*   **Bước 7 (Tổng hợp toàn cục - Server):** Server nhận dữ liệu từ các client, tiến hành trung bình trọng số để cập nhật biểu diễn chia sẻ toàn cục $\alpha^{(t+1)}$, và thực hiện thuật toán WassersteinBarycenter để tổng hợp phân phối neo toàn cục mới $\mu_{1:C}^{(t+1)}$ [10]. Vòng lặp quay lại bước 2 [10].

---

## 4. METRICS / MEASURES (Tiêu chí đo lường & Thiết lập thực nghiệm)

### Các tiêu chí đo lường (Metrics):
1.  **Average Accuracy (Độ chính xác trung bình):**
    *   *Định nghĩa:* Paper không cung cấp công thức toán học cụ thể cho metric này, nhưng định nghĩa nó là giá trị trung bình cộng độ chính xác phân loại trên tập kiểm tra (test set) của tất cả các client tham gia sau khi quá trình huấn luyện kết thúc [10].
    *   *Đo cái gì:* Hiệu năng phân loại thực tế của các mô hình cá nhân hóa trên dữ liệu cục bộ của các client [10].
    *   *Giá trị nào tốt:* Càng cao càng tốt.
    *   *Sử dụng ở experiment nào:* Tất cả các thực nghiệm chính bao gồm Toy Noisy Features, Toy Linear Mapping, MNIST-USPS, và TextCaps [10].
2.  **Wasserstein Distance of Order 2 (Khoảng cách Wasserstein bậc 2 - $W_2$):**
    *   *Công thức:* $$W_2(\mu, \nu) = \left( \inf_{\zeta \in \mathcal{T}(\mu,\nu)} \int_{\mathbb{R}^d \times \mathbb{R}^d} \|x - y\|^2 d\zeta(x,y) \right)^{1/2}$$ [10]. Dưới giả định Gauss, công thức đóng bình phương là: $W_2^2(\mu_c, \nu_{\phi_i}^{(c)}) = \|v_c - m_i^{(c)}\|^2 + \mathfrak{B}^2(\Sigma_c, \Sigma_i^{(c)})$ [10, 11].
    *   *Đo cái gì:* Đo chi phí dịch chuyển tối thiểu để biến đổi phân phối dữ liệu nhúng của client thành phân phối neo chung [11].
    *   *Giá trị nào tốt:* Càng thấp (tiến về 0) càng tốt [11].
    *   *Sử dụng ở experiment nào:* Được dùng làm số hạng phạt trực tiếp trong hàm mục tiêu huấn luyện cục bộ (Objective function) [11], và được dùng để trực quan hóa sự hội tụ qua các epoch [11].
3.  **Bures Distance (Khoảng cách Bures - $\mathfrak{B}$):**
    *   *Công thức:* Paper không cung cấp công thức chi tiết cho $\mathfrak{B}$ mà chỉ nêu nó là khoảng cách giữa hai ma trận hiệp phương sai xác định dương [11].
    *   *Đo cái gì:* Đo sự khác biệt về hình dạng (covariance structure) giữa ma trận hiệp phương sai của phân phối neo $\Sigma_c$ và ma trận hiệp phương sai thực nghiệm cục bộ $\Sigma_i^{(c)}$ [11].
    *   *Giá trị nào tốt:* Càng thấp càng tốt.
    *   *Sử dụng ở experiment nào:* Sử dụng trong việc tính toán gradient cục bộ để cập nhật thừa số Cholesky $L_{i,c}$ tại bước cập nhật phân phối neo của client [11].
4.  **Principal Angle Distance (Khoảng cách góc chính - $dist$):**
    *   *Công thức:* $$dist(M, N) = \|\hat{M}^\top_{\perp} \hat{N}\|_2 = \|\hat{N}^\top_{\perp} \hat{M}\|_2$$ với $\hat{M}, \hat{N}$ là các cơ sở trực giao của không gian con spanned bởi cột của $M, N$ [11].
    *   *Đo cái gì:* Đo khoảng cách hình học giữa hai không gian con tuyến tính [11].
    *   *Giá trị nào tốt:* Càng thấp (tiến về 0) càng tốt [11].
    *   *Sử dụng ở experiment nào:* Sử dụng trong thực nghiệm mô phỏng (Toy regression) để chứng minh tốc độ hội tụ của biểu diễn toàn cục $A^{(t)}$ về không gian con thực tế $A^\star$ [11].

### Thiết lập thực nghiệm tổng quát (Experimental Setting):
*   **Số lượng client (b):** 100 hoặc 200 tùy thuộc vào thiết lập thử nghiệm [11].
*   **Tỷ lệ tham gia của client (r):** 0.1 ở mỗi vòng truyền thông [11].
*   **Số vòng truyền thông toàn cục (T):** 50 vòng [11].
*   **Số epoch huấn luyện cục bộ (M):** M = 10 đối với các tập dữ liệu thực tế (Digits, TextCaps), và M = 100 đối với dữ liệu mô phỏng (Toy datasets) [11].
*   **Thuật toán tối ưu (Optimizer):** Adam với tốc độ học (learning rate) là 0.001 cho tất cả các phương pháp [11].
*   **Kích thước batch (Batch size):** 100 [11]. Đối với việc huấn luyện hàm nhúng cục bộ, kích thước batch là 10 (cho Toy và TextCaps) và 100 (cho MNIST-USPS) [11].
*   **Tham số điều hòa (Regularization parameters):** $\lambda_1 = 0.001$ và $\lambda_2 = 0.001$ (mặc định) [11, 12].
*   **Không gian ẩn (Latent Space dimension - k):** Cố định bằng 64 [12].
*   **Mô hình kiến trúc mạng cục bộ:**
    *   *Đối với Toy và TextCaps:* Mạng FCNN 1 lớp ẩn với 64 đơn vị, kích hoạt ReLU [12].
    *   *Đối với Digits:* CNN gồm 2 lớp tích chập, tiếp nối bởi max-pooling, kích hoạt Sigmoid, sau đó làm phẳng và qua 1 lớp kết nối đầy đủ kích hoạt ReLU [12].
*   **Mô hình đối sánh (Baseline models):**
    *   *Local:* Mỗi client tự huấn luyện mô hình cục bộ trên dữ liệu của riêng mình, không liên kết hay chia sẻ tham số với server hay client khác [12].
    *   *FedHeNN:* Biến thể cải tiến từ nghiên cứu của Makhija et al. (2022) [12]. Vì các client có số chiều đặc trưng khác nhau nên không thể dùng chung tập dữ liệu tham chiếu RAD của FedHeNN gốc; nhóm tác giả đã xây dựng RAD có số chiều lớn nhất rồi thực hiện cắt tỉa (pruning) kích thước tương ứng cho từng client để làm baseline đối sánh [12].

---

## 5. EVALUATION / RESULTS (Đánh giá & Kết quả thực nghiệm)

### Bảng so sánh kết quả thực nghiệm:

| Thử nghiệm (Experiment) | Tập dữ liệu (Dataset) | Đối sánh (Baselines) | Số đo (Metric) | Kết quả FLIC-Class | Kết quả FLIC-HL | Baseline tốt nhất | FLIC tốt hơn bao nhiêu | Kết luận chính |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Toy NF** | Noisy Features (ki: 5-15) [12] | Local, FedHeNN [12] | Average Accuracy [12] | ~78.00% [12] | ~78.00% [12] | ~75.00% (FedHeNN) [12] | **~3.00%** [12] | FLIC căn chỉnh hiệu quả đặc trưng nhiễu, vượt trội hơn FedHeNN và Local [12]. |
| **Toy LM** | Linear Mapping (ki: 5-30) [12] | Local, FedHeNN [12] | Average Accuracy [12] | ~73.00% [12] | 73.50% [13] | ~69.50% (Local/FedHeNN) [13] | **~4.00%** [13] | FLIC chịu được các phép biến đổi tuyến tính ngẫu nhiên tốt hơn hẳn baselines [13]. |
| **Digits (b=100, 3 Cls)** | MNIST & USPS [13] | Local, FedHeNN [13] | Average Accuracy [13] | 97.83% [13] | 97.70% [13] | 97.49% (Local) [13] | **0.34%** [13] | FLIC đạt kết quả cao nhất dù phân phối nhãn rất lệch (3 lớp/client) [13]. |
| **Digits (b=100, 5 Cls)** | MNIST & USPS [13] | Local, FedHeNN [13] | Average Accuracy [13] | 96.46% [13] | 96.31% [13] | 96.15% (FedHeNN) [13] | **0.31%** [13] | FLIC duy trì phong độ vượt trội khi số lượng lớp tăng lên 5 lớp/client [13]. |
| **Digits (b=200, 3 Cls)** | MNIST & USPS [13] | Local, FedHeNN [13] | Average Accuracy [13] | 94.50% [13] | 94.51% [13] | 93.40% (FedHeNN) [13] | **1.11%** [13] | Khi quy mô client tăng gấp đôi, lợi thế của FLIC so với các baseline tăng rõ rệt [13]. |
| **Digits (b=200, 5 Cls)** | MNIST & USPS [13] | Local, FedHeNN [13] | Average Accuracy [13] | 90.66% [13] | 90.63% [13] | 87.22% (FedHeNN) [13] | **3.44%** [13] | Ở thiết lập khó (200 client, 5 lớp), FLIC cải thiện vượt bậc đến 3.44% so với baseline tốt nhất [13]. |
| **TextCaps (b=100, 2 Cls)** | BERT (768) & ResNet (512) [13] | Local, FedHeNN [13] | Average Accuracy [13] | 89.14% [13] | 99.68% [13] | 84.19% (Local) [13] | **5.49%** [13] | Trên dữ liệu đa phương thức cực kỳ dị dạng, FLIC-HL cải thiện hiệu năng vượt bậc (~5.5%) [13]. |
| **TextCaps (b=100, 3 Cls)** | BERT (768) & ResNet (512) [13] | Local, FedHeNN [13] | Average Accuracy [13] | 81.27% [13] | 81.50% [13] | 76.04% (Local) [13] | **5.46%** [13] | Hiệu năng cải thiện ổn định khoảng 5.5% khẳng định sức mạnh của lớp ẩn toàn cục alpha [13]. |
| **TextCaps\* (b=200, 2 Cls)** | BERT (768) & ResNet (512) [13] | Local, FedHeNN [13] | Average Accuracy [13] | 87.73% [13] | 87.74% [13] | 83.89% (FedHeNN) [13] | **3.85%** [13] | Khi số lượng client tăng lên 200, FLIC vẫn giữ khoảng cách biệt lớn (~3.85%) [13]. |
| **TextCaps\* (b=200, 3 Cls)** | BERT (768) & ResNet (512) [13] | Local, FedHeNN [13] | Average Accuracy [13] | 79.08% [13] | 78.49% [13] | 74.95% (Local) [13] | **4.13%** [13] | FLIC-Class vượt trội hơn Local 4.13% và FedHeNN 4.31% [13]. |

### Phân tích chi tiết từng thực nghiệm:
1.  **Thực nghiệm Noisy Features (Toy NF):**
    *   *Mục tiêu:* Kiểm tra khả năng chống nhiễu của FLIC khi các client bị chèn ngẫu nhiên các đặc trưng gây nhiễu làm bùng nổ số chiều từ 5 lên đến 15 [13].
    *   *Kết quả:* FLIC cải thiện độ chính xác khoảng **3%** một cách ổn định so với FedHeNN và vượt xa Local learning [13].
    *   *Ý nghĩa:* Hàm nhúng cục bộ của FLIC có khả năng lọc bỏ các nhiễu ngẫu nhiên đầu vào để cô đọng thông tin hữu ích vào không gian ẩn [13].
2.  **Thực nghiệm Linear Mapping (Toy LM):**
    *   *Mục tiêu:* Thử nghiệm tính bền bỉ của thuật toán trước các phép biến đổi tuyến tính ngẫu nhiên của không gian đặc trưng (số chiều dao động từ 5 đến 30) [13].
    *   *Kết quả:* Cải thiện tối đa khoảng **4%** độ chính xác so với các baseline khác [13]. Khoảng cách này thu hẹp dần khi số lượng client tăng lên [13]. FLIC-HL hoạt động tốt hơn FLIC-Class một chút [13].
    *   *Ý nghĩa:* Việc tối ưu hóa liên bang lớp ẩn toàn cục $\alpha$ giúp tăng khả năng học biểu diễn chung tốt hơn [13, 14].
3.  **Thực nghiệm Digits (MNIST vs USPS):**
    *   *Mục tiêu:* Phân loại chữ số viết tay trên môi trường thực tế dị dạng về kích thước ảnh (28x28 của MNIST vs 16x16 của USPS) [14].
    *   *Kết quả:* Ở cấu hình dễ (100 client), FLIC cải thiện khoảng 0.3% [14]. Ở cấu hình phức tạp nhất (200 client, 5 lớp/client), FLIC cải thiện vượt bậc tới **3.44%** so với baseline tốt nhất (FedHeNN đạt 87.22%, Local đạt 86.50% trong khi FLIC-Class đạt 90.66%) [14].
    *   *Ý nghĩa:* Sự vượt trội của FLIC càng rõ nét khi độ phức tạp hệ thống tăng lên (nhiều client hơn, độ lệch nhãn cục bộ cao hơn) [14].
4.  **Thực nghiệm TextCaps:**
    *   *Mục tiêu:* Bài toán cực kỳ thử thách khi một số client chỉ sở hữu dữ liệu văn bản (nhúng BERT 768 chiều), số khác chỉ sở hữu dữ liệu ảnh (nhúng ResNet18 512 chiều), kết hợp cắt tỉa ngẫu nhiên 10% đặc trưng [14].
    *   *Kết quả:* FLIC mang lại bước nhảy vọt hiệu năng rất lớn, cải thiện tới **5.49%** độ chính xác so với baseline tốt nhất (với 100 client, 2 lớp, FLIC-HL đạt 89.68% so với Local đạt 84.19% và FedHeNN đạt 83.99%) [14].
    *   *Ý nghĩa:* Chứng minh khả năng "dịch" các phương thức dữ liệu hoàn toàn khác biệt (Ảnh vs Chữ) về một không gian biểu diễn ẩn chung thống nhất ngữ nghĩa [14].

### Phân tích Ablation Study:
Nghiên cứu tiến hành phân tích ablation study thông qua việc đánh giá đường cong tổn thất (loss curves) và thực nghiệm về tiền huấn luyện (pretraining) [14]:
*   **Loại bỏ việc học hàm nhúng và biểu diễn toàn cục (Chỉ huấn luyện classifier cục bộ):** Khi cố định hàm nhúng $\phi_i$ và mô hình toàn cục, chỉ huấn luyện classifier cục bộ. Tổn thất cục bộ giảm mượt mà qua các epoch nhưng không đạt được hiệu năng cao do thiếu sự căn chỉnh không gian đặc trưng [14].
*   **Loại bỏ việc học hàm nhúng cục bộ (Chỉ học classifier và biểu diễn toàn cục):** Đường cong tổn thất xuất hiện hiện tượng đứt gãy lớn ở đầu mỗi vòng huấn luyện cục bộ (do tham số toàn cục được server trung bình hóa và gửi lại) [14]. Điều này cho thấy sự bất ổn định trong quá trình tối ưu hóa khi không có sự dịch chuyển không gian đặc trưng đầu vào [14].
*   **Loại bỏ/Thay đổi số epoch tiền huấn luyện (Pretraining epochs):** Khi thay đổi số epoch tiền huấn luyện hàm nhúng cục bộ từ 1 đến 200: hiệu năng tăng dần khi tăng số epoch tiền huấn luyện nhưng đạt đỉnh rồi giảm sút (overfitting) [14]. Ví dụ trên tập Toy LM, việc tiền huấn luyện từ 10 đến 50 epoch là tối ưu nhất; vượt quá ngưỡng này khiến hàm nhúng bị quá khớp vào tập huấn luyện và không thể tổng quát hóa tốt trên tập test [14]. Thành phần quan trọng nhất của FLIC chính là việc cập nhật đồng thời hàm nhúng trong quá trình học liên bang thay vì chỉ cố định nó sau khi pretrain [14].

### Phân tích lý thuyết (Theoretical Analysis):
*   **Theorem chính (Theorem 1 / Theorem S3):** Trong một thiết lập hồi quy tuyến tính đơn giản hóa, với phân phối neo ẩn được giả định đã biết trước và dữ liệu có phân phối Gauss [14].
*   **Ý nghĩa:** Hàm nhúng cục bộ ước lượng $\hat{\phi}_i$ hội tụ về hàm nhúng lý tưởng $\phi_i^\star$ ngoại trừ một phép biến đổi đảo dấu $Q = \text{diag}(\pm 1)$ [14]. Đồng thời, biểu diễn chia sẻ toàn cục $A^{(t)}$ học bởi thuật toán FedRep hội tụ tuyến tính (với tốc độ hình học) về không gian con thực tế $QA^\star$ theo thước đo khoảng cách góc chính (principal angle distance) [14, 15].
*   **Điều kiện cần:**
    1.  Đặc trưng ẩn thực tế tuân theo phân phối Gauss chuẩn $\mathcal{N}(0_k, I_k)$ [15].
    2.  Các cột của ma trận biểu diễn thực tế $A^\star$ phải trực giao và $\|\beta_i^\star\|_2 = \sqrt{d}$ [15].
    3.  Ở mỗi vòng, số lượng client hoạt động $|A_{t+1}| = b'$ phải đủ lớn để các tham số classifier thực tế $\{\beta_i^\star\}_{i \in A_{t+1}}\\}$ bao phủ toàn bộ không gian $\mathbb{R}^d$ [15].
    4.  Tốc độ học cục bộ $\eta$ phải nhỏ hơn một ngưỡng giới hạn $1/(4\sigma^2_{\max, \star})$ [15].
    5.  Số lượng mẫu cục bộ $n$ phải đủ lớn thỏa mãn cận chặn dưới xác suất [15].

---

## FLIC trong 1 phút
FLIC giải quyết bài toán hóc búa khi các thiết bị tham gia học liên bang cá nhân hóa sở hữu dữ liệu thô không đồng nhất về số chiều hoặc ngữ nghĩa (dị dạng đặc trưng) [15]. Ý tưởng của nghiên cứu là trang bị cho mỗi thiết bị một "bộ dịch cục bộ" (local embedding function) để ánh xạ dữ liệu dị dạng về một không gian ẩn chung có số chiều cố định [15]. Để đảm bảo sự đồng nhất ngữ nghĩa giữa các bộ dịch này, hệ thống thực hiện căn chỉnh phân phối cục bộ hướng tới các phân phối neo toàn cục chung thông qua khoảng cách Wasserstein bậc 2 [15]. Server trung tâm sẽ tiến hành tổng hợp các phân phối neo này bằng cách giải bài toán trọng tâm Wasserstein (Wasserstein barycenter) [15]. Thực nghiệm trên các tập dữ liệu ảnh-chữ đa phương thức (TextCaps) và chữ số dị dạng kích thước (MNIST-USPS) chứng minh FLIC cải thiện vượt bậc từ 3% đến hơn 5% độ chính xác so với các baseline học cục bộ hay FedHeNN [15]. Nghiên cứu này mở ra khả năng cộng tác học máy an toàn, bảo mật giữa các doanh nghiệp hay thiết bị lưu trữ dữ liệu ở các định dạng hoàn toàn khác biệt nhau trong thực tế [15].
