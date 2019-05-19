# 4. Docker Image OS có cần phải phù hợp với Host OS?

____
____

# <a name="content">Nội dung</a>

> ![docker-tips-and-tricks.jpg](/images/docker-tips-and-tricks.jpg)

- Docker Image OS là hệ điều hành bạn quy định trong Dockerfile và  Host OS chính là hệ điều hành sử dụng để cài đặt Docker. Giữa chúng có thể khác nhau.

- Đã có rất nhiều người đặt câu hỏi: "Nếu Docker host của tôi đang chạy Ubuntu thì có nghĩa là Docker image của tôi cũng cần phải dựa trên Ubuntu?"

- Câu trả lời cho câu hỏi trên là không đúng. Bạn có thể sử dụng bất cứ hệ điều hành nào đóng vai trò base image cho Docker Image của bạn.

- Trong thực tế, hầu hết các Docker Image "official" đều được dựa trên một bản phân phối của Linux có tên là "Alpine". "Alpine" gần như là hoàn hảo khi sử dụng cùng với Ubuntu, Debian, CentOS, RHEL hoặc bất cứ bản distro nào mà bạn muốn sử dụng trên Docker host.

____

# <a name="content-others">Các nội dung khác</a>
