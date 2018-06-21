---
layout: article
title: "Risk contribution và danh mục đầu tư"
date: 2016-10-14 12:00:00
categories: Misc
featured: true
featured_image: "/images/PM/pmp1.jpg"
tags: prg pm
author: Duong Vu
---
*Bài viết dựa trên lý thuyết Risk Parity.*
Giả sử 1 danh mục đầu tư có 2 tài sản, 1 là cổ phiếu và 2 là trái phiếu. Thường thấy chúng ta sẽ đầu tư theo tỉ lệ vàng, phân bổ 60% nguồn vồn vào cổ phiếu và 40% nguồn vốn vào trái phiếu.

Dữ liệu phân tích chỉ ra rằng, volatility của stock (cổ phiếu) tính bằng standard deviation (độ lệch chuẩn) là 15% và của bond (trái phiếu) là 5%. Correlation hay còn gọi là hệ số tương quan của cổ phiếu và trái phiếu là 0.2.

Theo công thức tính volatility của cả portfolio, chúng ta có:

$$\sigma_p = \displaystyle\sqrt{(\sigma_s^2 w_s^2 + \sigma_b^2 w_b^2 + 2 w_b w_s \sigma_s \sigma_b \rho_{sb}})$$

Áp dụng công thức trên vào số liệu chúng ta ước lượng, volatility của portfolio tương đương 9.6% dựa vào standard deviation. Cần nhớ chúng ta có công thức liên hệ giữa standard deviation và variance (độ lệch chuẩn và phương sai) như sau:

$$ var(p) = \sigma_p^2 $$

Thay vì dùng volatility dựa trên standard deviation thuần túy, chúng ta có thể xác định mức độ đóng góp rủi ro của mỗi tài sản vào danh mục chung bằng variance. Cụ thể ở đây, có thể xác định được variance của stock tương đương:

$$ \sigma_s^2 w_s^2 + \rho_{sb} w_s w_b \sigma_s \sigma_b $$

$$ 0.6^2\times0.15^2 + 0.2 \times0.6\times0.4\times0.15\times0.05 = 0.00846 $$

và variance của bond tương đương:

$$ \sigma_b^2 w_b^2 + \rho_{sb} w_s w_b \sigma_s \sigma_b $$

$$ 0.4^2\times0.05^2 + 0.2\times0.6\times0.4\times0.15\times0.05 = 0.00076 $$

Chúng ta có variance của portfolio tương đương 0.009216. Vậy mức độ rủi ro đóng góp vào danh mục chung của stock và bond lần lượt là :

$$ \frac{0.00846}{0.009216} = 0.92 = 92 \% $$

$$ \frac{0.00076}{0.009216} = 0.08 = 8 \% $$

Vậy với 1 danh mục đầu tư thuần túy với 60% cổ phiếu và 40% trái phiếu, rủi ro của danh mục chủ yếu đến từ rủi ro của cổ phiếu hơn là trái phiếu.

Việc sử dụng thuật ngữ "balanced-portfolio" với 60% cổ phiếu và 40% trái phiếu không thực sự phản ánh thực tế rằng, 60% phân bổ cổ phiếu đóng góp tới 92% rủi ro.

Điều nhiều nhà đầu tư vẫn tin đó là 1 danh mục 60% cổ phiếu và 40% trái  sẽ có 60% rủi ro đóng góp bởi cổ phiếu và 40% đóng góp bởi trái phiếu. Vậy hiệu quả và rủi ro của danh mục đầu tư cần được đánh giá kĩ càng hơn.
