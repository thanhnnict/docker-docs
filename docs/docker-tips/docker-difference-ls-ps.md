# 24. Sự khác biệt giữa `docker ps` và `docker container ls`

____
____

# <a name="content">Nội dung</a>

![docker-tips-and-tricks.jpg](/images/docker-tips-and-tricks.jpg)

- Khi bạn chạy câu lệnh:

        docker help

    kết quả nhận được sẽ tương tự như sau:

        Management Commands:
          ...
          container   Manage containers
          image       Manage images
          ...

        Commands:
          ...
          ps          List containers
          run         Run a command in a new container
          ...

- Với số lượng câu lệnh khá là nhiều, và nhìn qua thì các lệnh này được liên kết với containers, images, networks, volumes, ...

- Khá khó là phân biệt, vì vậy họ thêm vào "Management Commands" để phân loại tất cả các lệnh và cũng làm cho các lệnh trở nên nhất quán hơn.

- Ví dụ: `docker container ls` là câu lệnh mới có cùng chức năng với `docker ps`. Chắc chắn nó gõ nhiều hơn, nhưng nó rõ ràng hơn nhiều về những gì nó làm.

____

# <a name="content-others">Các nội dung khác</a>
