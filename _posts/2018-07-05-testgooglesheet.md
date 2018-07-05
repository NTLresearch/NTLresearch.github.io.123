---
layout: article
title: "Mô hình định giá và sự khó hiểu của nó"
date: 2018-07-06 12:00:00
categories: Value Investing
featured: true
featured_image: "/images/VI/Valuation/feature_image.png"
tags: Value Investing
author: Kim Vu Duc
---

*Hôm nay ngồi làm case study cho 1 công ty, tôi và ông bạn học cùng đại học lại ngồi thảo luận về mô hình định giá. Có quá nhiều thứ để nói về các mô hình định giá cổ phiếu từ cả góc nhìn thực tế và toán học. 2 năm đầu sau khi tốt nghiệp đại học tôi vật lộn thực hành, kiểm tra các mô hình định giá, cố gắng áp dụng mô hình định giá vào trong các trường hợp cụ thể, công ty cụ thể, và mọi thứ đều không work out như tôi mong đợi bởi một lý do. Đó là bản chất mô hình định giá sử dụng các input một cách chủ quan và ko có tính hệ thống.*

## *Công thức cơ bản của định giá*
Giá trị của một doanh nghiệp là gì? Với các mô hình định giá, giá trị của 1 doanh nghiệp đơn giản chỉ là, tìm xem trong tương lai, công ty sẽ kiếm được thêm bao nhiêu tiền, tăng trưởng bao nhiêu, nếu dùng từ ngữ chuyên môn gọi là forecast, sau đó tìm một tỉ lệ chiết khấu hợp lý để chuyển đổi những giá trị forecast thành các giá trị hiện tại (tính present value).

Hiểu đơn giản, có 2 yếu tố mang tính chủ quan trong mô hình. Thứ nhất, nhà đầu tư cần đưa ra dự báo về tương lai, tính toán các yếu tố kì vọng. Thứ hai, nhà đầu tư cần ước lượng tỉ lệ chiết khấu sao cho phù hợp để chiết khấu đống dự báo kia về giá hiện tại. Như Warren Câu trả lời đặt ra là, dự đoán như thế nào là đúng, và chiết khấu bao nhiêu là đủ.

![VAL_1](/images/VI/Valuation/VAL_5.jpg)

Đầu tiên là về dự báo, nếu không có thông tin nội bộ và là tay trong của công ty, sẽ rất khó để biết được chính xác đâu là con số cho năm tới, 2 năm tới, 5 năm tới hay 10 năm tới. Một nhà phân tích độc lập hay thuộc tổ chức đơn giản sẽ liên hệ với công ty, và công ty sẽ cho ra con số. Cách làm này tỉ lệ chiến thắng vẫn là 50-50 bởi có ai dám chắc con số công ty bạn cover đưa cho bạn là chính xác? Và liệu công ty có tính toán được trong 5 năm tới, liệu vị thế trên thị trường của họ có thể thay đổi hay giữ nguyên?

Thứ hai là về lãi suất chiết khấu. Thông thường phương pháp phổ biến là sử dụng CAPM. Như đã biết thì CAPM không đúng, và cái phần risk premium trong CAPM thì cũng rất là chủ quan. Với thị trường Việt Nam, lúc thì người ta bảo là 9%, mấy hôm sau lại bảo 10%. Việc lựa chọn con số cho từng thời điểm nhất định lại càng khó hơn bởi đơn giản risk premium và cả CAPM đều có tính dynamic và phụ thuộc vào thời gian.

## *Gordon Growth Model*
Mô hình cơ bản dễ hiểu nhất khi định giá cổ phiếu là Gordon Growth Model (GGM). Công thức đơn giản như thế này:

$$ V_0 = \frac{d_1}{1+r} + \frac{d_1}{(1+r)^2} + ... + \frac{1}{(1+r)^{T-1}} \frac{d_T}{r-g} $$

GGM buộc chúng ta phải đưa ra dự báo cho tăng trưởng của cổ tức trong 1,2... 5 năm và cả tỉ lệ tăng trưởng trong vô hạn. Việc dự báo trong vô hạn gần như là bất khả thi. Quan trọng hơn, g trong vô hạn bao nhiêu là đủ và bao nhiêu là hợp lý? 3%? 4%? 5%? Tất cả con số trên đều có thể được lựa chọn bởi những lý do vô cùng hợp lý và thuyết phục. Với junior analyst, họ sẽ nói, ok sếp em bảo 3% là hợp lý ở thị trường này! Với senior analyst thì bảo 3% là ngưỡng mà thế giới áp dụng, xem báo cáo của JPM hay GS kìa! Một ông economist cũng có thể nói rằng, vì tỉ lệ GDP growth rate toàn cầu trong nhiều thâp kỉ qua trung bình là 2-4% nên tôi nghĩ 3% là hợp lý!... Các lý do trên đều có 1 sự hợp lý nhất định, và khi nghe xong tôi cũng thấy, uh hợp lý đấy, nhưng mỗi tội thị giá ngoài thị trường nó vận động không như thế.

## *Free Cash Flow Model*
Với dân kế toán, mô hình Discounted Cash Flow có thể hợp lý hơn (DCF) một chút:

$$ V_0 = \frac{FCF_1}{1+r} + \frac{FCF_2}{(1+r)^2} + ... + \frac{1}{(1+r)^{T-1}} \frac{FCF_T}{r-g} - Net Debt $$

Tương tự như GGM, FCF model bao gồm 2 thành tố chủ quan là dự báo trong ngắn hạn và tỉ lệ tăng trưởng trong vô hạn. Terminal value được tính toán từ tỉ lệ tăng trưởng vô hạn kia đóng vai trò quan trọng trong tính toán giá trị hiện tại của cổ phiếu. Giả sử tôi ước lượng được giá trị FCF của cổ phiếu trong 5 năm tới là 500 VND 1 cổ phiếu, tăng trưởng 0% và doanh nghiệp không có nợ. Thêm vào đó, tôi ước lượng tăng trưởng vô hạn ở mức 3%, lãi suất chiết khấu ở mức 7%. Thông tin chi tiết như ở sheet bên dưới

<iframe src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRPlKcNkTVZdedyQ0Iys9-DRCckf20lcN6b8By_Jvwf7114QQu8dG1MJNUrFLoB53lnQcZxE7TnDZfx/pubhtml?gid=0&amp;single=true&amp;widget=true&amp;headers=false" width="700" height="400">
</iframe>

Khi tính toán ra giá cổ phiếu, tôi nhận thấy giá trị ước lượng của mình phụ thuộc tới hơn 70% vào giá trị terminal value của mô hình. Có nghĩa là, rất nhiều yếu tố của doanh nghiệp vô hình chung được gói gọn vào tham số g trong mô hình định giá. Điều này hẳn rất vô lý và phi logic.

Đặc tính chủ quan này của mô hình định giá được chỉ ra bởi Benjamin Graham, tác giả của cuốn sách huyền thoại Security Analysis. Và theo như John Maynard Keynes, cha đẻ của lý thuyết kinh tế Keynes nói rằng:

![VAL_1](/images/VI/Valuation/VAL_1.jpg)

> Thật là ngờ ngệch trong việc đưa ra những kì vọng, để rồi đặt lòng tin vào những thứ rất không chắc chắn (nguyên văn: It would be foolish, in forming our expectations, to attach great weight to matters which are very uncertain)

Có thể hiểu ở đây, chúng ta đưa ra những kì vọng về tỉ lệ tăng trưởng, về dòng tiền trong 5-10 năm hay 20 năm nữa, nhưng quên mất rằng chúng ta đang đặt lòng tin vào những thứ vô cùng không chắc chắn. Khó ai có thể dự đoán chuẩn xác tỉ lệ tăng trưởng dòng tiền (rất nhiều điều chỉnh cho accural items, 1 ước lượng đúng cho capex ...) Rất nhiều lần tôi và thằng bạn làm cùng cãi nhau về ước lượng tỉ lệ tăng trưởng của cash flow cũng như growth rate. Có những trường hợp nó đúng và có những trường hợp tôi đúng, nhưng cuối cùng odd ratio của tôi và nó cũng chỉ là 1-1, tức là tôi chỉ đúng 50% và nó cũng thế. Việc đưa ra 1 con số như 4% cho năm tới, 3% cho năm thứ hai hay đại loại những thứ như vậy gần như là vô nghĩa. Nếu dành đủ thời gian ra backtest toàn bộ báo cáo equity research của những công ty chứng khoán lớn, gần như tất cả các trường hợp đều có sai lệch giữa thị giá và giá khuyến nghị.

## *Vậy tại sao ai cũng sử dụng những mô hình rất chủ quan và tính chính xác rất thấp?*

Chúng ta cần vạch ra 1 ranh giới rất rõ, giữa việc đầu tư (investment) và việc tư vấn tài chính (advisory). Với tư vấn tài chính, chẳng hạn như M&A hay IPO, analyst được tiếp cận với thông tin tài chính, các thông tin liên quan đến kế hoạch, dự định của công ty một cách chính xác và trực tiếp. Vì thế rủi ro ước lượng các input như FCF hay terminal growth rate cũng giảm xuống ở mức thấp hơn. Tuy nhiên điều đó không có nghĩa là rủi ro không còn. Kết quả nghiên cứu trong lĩnh vực finance gần đây chỉ ra rằng, hơn 70% các phi vụ m&a thì những công ty bị mua thường bị overpriced. Ngay cả khi tiếp cận được thông tin rủi ro từ việc định giá vẫn còn rất lớn. Hơn nữa, hoạt động tư vấn tài chính thường không gắn liền với performance của cổ phiếu mà gắn với một mức phí cố định (hoặc bán cố định trong nhiều trường hợp). Sẽ rất khó để nhà phân tích đưa ra mức giá chuẩn khi lợi ích của anh ta chỉ gắn liền với một mức phí đã được thỏa thuận trước, dù đúng hay không đúng, không có gì ngăn cản anh ta nhận được phần thù lao sau khi thương vụ hoàn thành. Trong trường hợp có conflict of interest, nhiều trường hợp giá có thể đẩy lên cao hơn (IPO) hoặc đẩy xuống thấp hơn (Takeover), đơn giản bằng cách điều chỉnh tham số của mô hình.


![VAL_1](/images/VI/Valuation/VAL_6.jpg)

Ngược lại , trong trường hợp 1 quỹ đầu tư hay 1 người có vốn muốn đầu tư vào một công ty (không tính đến activist investor), lợi ích của anh ta gắn chặt với performance của cổ phiếu, vì vậy anh ta có động lực lớn hơn để tìm ra giá trị thực của cổ phiếu. Vậy đâu là cách để tìm ra giá trị thật của công ty thay vì sử dụng mô hình định giá phổ thông? Có vô số cách được sử dụng trong cuộc sống, tuy nhiên value investing - hay đầu tư giá trị có lẽ phần nào bù đắp được những khiếm khuyết của mô hình định giá cơ bản đề cập phía trên bởi cách tiếp cận logic hơn của nó.
