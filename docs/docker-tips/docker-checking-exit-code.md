# 22. Kiểm tra Exit Code của `stopped containers`

____
____

# <a name="content">Nội dung</a>

![docker-tips-and-tricks.jpg](/images/docker-tips-and-tricks.jpg)

- Nếu như bạn muốn biết chính xác `exit code` của một container đang dừng hoạt động. Đây sẽ là cách thực hiện điều đó.

- **Tạo một container để giả lập lỗi chung**

        docker run alpine sh -c "exit 1"

- **Xác nhận rằng container đã được tạo ra và đã dừng hoạt động**. Ví dụ:

        docker ps -a

    kết quả sẽ hiển thị như sau:

        CONTAINER ID   IMAGE    COMMAND            CREATED              STATUS                       
        61c688005b3a   alpine   "sh -c 'exit 1'"   About a minute ago   Exited (1) 3 seconds ago

    ta hãy chú ý đến cột STATUS và nhận thấy rằng `exit code` ở đây là `1`. Đây là `exit code` chung của một lỗi. Thông thường các `exit code` khác `0` đều được coi là lỗi. `0` là `exit code` cho biếbieetontainer dừng lại chính xác mà không có sự xuất hiện của lỗi.

- Thậm chí, ta có thể biết chính xác `exit code` của một container bằng cách sử dụng câu lệnh `docker inspect`. Ví dụ:

        docker inspect 61c688005b3a --format='{{.State.ExitCode}}'
        
____

# <a name="content-others">Các nội dung khác</a>
