---
title : "AWS First Cloud AI Journey - FCAJ Community Day"
date : 2026-05-23
weight : 3
chapter : false
pre : "<b> 4.2. </b>"
---

#### Mục đích của sự kiện

+ Giới thiệu tầm quan trọng của việc xây dựng **Context** khi làm việc với các mô hình AI nhằm nâng cao độ chính xác và chất lượng kết quả.

+ Tìm hiểu các giải pháp AI của AWS như **Amazon Quick** và khả năng hỗ trợ phân tích dữ liệu, xây dựng quy trình làm việc thông minh.

+ Chia sẻ các phương pháp tối ưu hiệu năng, tăng cường bảo mật và giảm chi phí vận hành thông qua **Amazon CloudFront**.

+ Lắng nghe kinh nghiệm thực tế từ cuộc thi **LotusHacks**, giúp người tham gia hiểu rõ quy trình xây dựng một sản phẩm AI từ ý tưởng đến triển khai trong thời gian giới hạn.

+ Tìm hiểu nguyên nhân dẫn đến tính phi định tính của các mô hình ngôn ngữ lớn (LLM) cũng như các giải pháp giúp giảm sự sai khác trong kết quả sinh ra.

+ Giới thiệu mô hình **Enterprise Multi-Agent** thông qua bài toán chấm điểm tín dụng dành cho Startup.

#### Danh sách diễn giả
+ **Trịnh Trường** – Platform Engineer, GoTymeX.
+ **Phạm Nguyễn Hải Anh** – Cloud Consultant, G-AsiaPacific Vietnam.
+ **Nguyễn Tuấn Thịnh** – DevOps Engineer, FCAJ.
+ **Thảo Nguyễn** – GenAI Engineer, VIB.
+ **Mai Nguyễn** – GenAI Engineer, VIB.
+ **Uyên Lê** – GenAI Engineer, VIB.
+ **Đức Đào** – Solutions Architect, Cloud Kinetics.
+ **Vy Lam** – Senior Business Systems Analyst, VPBank.

#### Nội dung nổi bật

+ **Context Is Everything: Making AI Actually Work for You** – *Trịnh Trường*

Diễn giả chia sẻ về vai trò quan trọng của **Context Engineering** trong việc sử dụng AI hiệu quả. Một mô hình AI dù mạnh đến đâu cũng khó có thể đưa ra kết quả chính xác nếu thiếu ngữ cảnh phù hợp.

Các nội dung chính bao gồm:

- Khái niệm Context và tác động của Context đến chất lượng phản hồi của AI.
- Quá trình phát triển từ Prompt đơn giản đến các hệ thống AI có khả năng ghi nhớ ngữ cảnh.
- Các phương pháp xây dựng Context hiệu quả để AI hiểu đúng yêu cầu của người dùng.
- Định hướng học tập và phát triển dành cho sinh viên, lập trình viên muốn theo đuổi lĩnh vực AI.

+ **Friendly AI Assistant with Amazon Quick** – *Phạm Nguyễn Hải Anh*

Buổi chia sẻ giới thiệu **Amazon Quick** như một nền tảng AI hỗ trợ doanh nghiệp trong việc khai thác dữ liệu và tự động hóa quy trình làm việc.

Các tính năng nổi bật gồm:

- Quick Chat Agent hỗ trợ truy vấn và phân tích dữ liệu.
- Quick Flows cho phép xây dựng workflow bằng ngôn ngữ tự nhiên.
- Quick Spaces tạo môi trường cộng tác và chia sẻ tri thức.
- Quick Sight hỗ trợ xây dựng Dashboard và báo cáo trực quan từ dữ liệu.

Qua phần trình bày, em hiểu thêm về khả năng ứng dụng AI vào hoạt động phân tích dữ liệu và quản trị doanh nghiệp.

+ **From Edge To Origin: CloudFront as Your Foundation** – *Nguyễn Tuấn Thịnh*

Diễn giả giới thiệu vai trò của **Amazon CloudFront** trong việc tăng tốc phân phối nội dung và tối ưu hạ tầng trên AWS.

Các nội dung chính bao gồm:

- Triển khai CloudFront cho nhiều loại hệ thống khác nhau.
- Các giải pháp tối ưu chi phí vận hành.
- Tăng cường bảo mật bằng các tính năng tích hợp.
- Cải thiện tốc độ truy cập và độ ổn định của ứng dụng.

Qua bài chia sẻ, em hiểu rõ hơn cách sử dụng CloudFront để nâng cao hiệu năng và giảm chi phí cho hệ thống.

+ **36 Hours with LotusHacks – Building UTMorpho from Idea to Reality** – *Thảo Nguyễn, Mai Nguyễn và Uyên Lê*

Các diễn giả chia sẻ hành trình tham gia cuộc thi **LotusHacks**, từ lúc hình thành ý tưởng đến khi hoàn thiện sản phẩm.

Một số nội dung đáng chú ý gồm:

- Tìm kiếm và lựa chọn ý tưởng phù hợp.
- Xác định bài toán thực tế cần giải quyết.
- Quản lý thời gian và phân chia công việc trong 36 giờ.
- Những khó khăn gặp phải và cách vượt qua.
- Demo sản phẩm UTMorpho sau khi hoàn thành.

Qua câu chuyện thực tế này, em nhận thấy tinh thần làm việc nhóm và khả năng quản lý thời gian đóng vai trò rất quan trọng trong quá trình phát triển sản phẩm.

+ **Non-Determinism of "Deterministic" LLM Settings** – *Đức Đào*

Buổi chia sẻ giải thích nguyên nhân khiến các mô hình LLM vẫn có thể tạo ra kết quả khác nhau mặc dù sử dụng cùng Prompt và cùng cấu hình.

Các nội dung chính gồm:

- Cơ chế lựa chọn token tiếp theo của mô hình.
- Hiểu lầm về việc Temperature = 0 luôn tạo ra cùng một kết quả.
- Tác động của quá trình tối ưu phần cứng và suy luận.
- Các giải pháp giúp giảm sự khác biệt giữa các lần sinh kết quả.

Qua đó, em hiểu rõ hơn nguyên lý hoạt động của các mô hình AI hiện đại.

+ **Enterprise-Grade Multi-Agent System: The Case of Startup Credit Scoring** – *Vy Lam*

Diễn giả giới thiệu mô hình **Multi-Agent** thông qua bài toán chấm điểm tín dụng dành cho Startup.

Một số nội dung nổi bật gồm:

- Hạn chế của mô hình Single Agent.
- Sự phối hợp giữa nhiều AI Agent trong các hệ thống phức tạp.
- Thiết kế quy trình mô phỏng hội đồng phê duyệt tín dụng.
- Các cơ chế đảm bảo an toàn dữ liệu và tuân thủ quy định.
- Đánh giá hiệu quả đầu tư và lộ trình triển khai thực tế.

Bài chia sẻ giúp em có thêm góc nhìn về việc ứng dụng AI trong lĩnh vực tài chính và ngân hàng.

#### Những gì học được

Qua buổi workshop, em học được nhiều kiến thức mới về AI, AWS Cloud và các công nghệ hiện đại đang được doanh nghiệp áp dụng. Điều em ấn tượng nhất là phần chia sẻ về Amazon CloudFront vì giúp em hiểu rõ hơn cách tối ưu hiệu năng, tăng tính bảo mật và giảm chi phí khi triển khai hệ thống trên AWS.

Bên cạnh đó, câu chuyện tại LotusHacks giúp em nhận ra tầm quan trọng của việc quản lý thời gian, phân chia công việc hợp lý và phối hợp hiệu quả giữa các thành viên trong nhóm. Những kiến thức về Context Engineering, Multi-Agent và đặc điểm của các mô hình LLM cũng mở ra cho em nhiều hướng nghiên cứu mới trong lĩnh vực AI.

#### Ứng dụng vào công việc

Những kiến thức thu được từ workshop có thể áp dụng trực tiếp vào việc học cũng như các dự án cá nhân của em.

Em có thể vận dụng kinh nghiệm về quản lý thời gian và làm việc nhóm khi thực hiện các đồ án hoặc project với nhiều thành viên. Đồng thời, kiến thức về Amazon CloudFront sẽ giúp em triển khai các ứng dụng web có hiệu năng tốt hơn và tối ưu chi phí khi sử dụng AWS.

Đối với các chủ đề như Context Engineering, Multi-Agent và LLM, mặc dù còn khá mới nhưng em sẽ tiếp tục tìm hiểu và từng bước áp dụng vào các dự án AI trong tương lai.

#### Trải nghiệm trong sự kiện

Đây là lần thứ hai em tham gia **AWS First Cloud AI Journey Community Day**, tuy nhiên em vẫn cảm thấy khá hồi hộp khi bước vào sự kiện. Không khí của workshop rất sôi nổi, các diễn giả chia sẻ nhiều kinh nghiệm thực tế kết hợp với các ví dụ minh họa nên giúp em dễ dàng tiếp cận những kiến thức mới về AI và điện toán đám mây.

Mặc dù em vẫn chưa đủ tự tin để đặt câu hỏi trực tiếp với các diễn giả, nhưng em đã học hỏi được rất nhiều kiến thức bổ ích và có cơ hội giao lưu với các anh chị cũng như các bạn có cùng đam mê công nghệ. Buổi workshop mang lại cho em thêm động lực để tiếp tục học tập, rèn luyện kỹ năng và tham gia nhiều sự kiện công nghệ trong thời gian tới.

![Ảnh minh chứng](/images/4-Event/2-event2.jpg)