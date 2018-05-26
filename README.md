# win-explorer-java

Tên SV : Nguyễn Đình Trọng

Lớp : 17IT2

Mã SV : 17IT112

Email : ndtrong.17it2@sict.udn.vn

Đề 07

Câu 1 : Thiết kế giao diện File Explorer

Câu 2 : Chức năng Copy nhiều files cùng lúc

+Chức năng phụ : Mở File,Xóa File

Link video hướng dẫn sử dụng : https://youtu.be/V47HhQ0Mhzk

# Cách chạy Code

*Cách 1 : Đối với Eclipse

1.Download project về máy và giải nén.

2.Vào Eclipse, Chọn File > Open Project form File System.

3.Chọn Directory> Chọn project vừa giải nén.

4.Run file : Click chuột phải vào project vừa mở > Run As > Java Application.

*Cách 2 : Chạy bằng dòng lệnh:

1. Tải và giải nén project từ github

2. Mở command (cmd).

3. Dùng lệnh cd chuyển đến thư mục chứa source code

        Ví dụ:
        cd C:\Users\Administrator\Desktop\Explorer\src

4. Biên dịch bằng lệnh javac 

        javac Test\Explorer.java

5. Chạy bằng lệnh java

        java Test.Explorer

*Hàm chính/Chức năng chính

copyFile() : Copy toàn bộ path của files được chọn, sau đó đưa tất cả vào mảng String[] path.
              
        Ví dụ : chọn các file : hihi.txt , 1.rar tại E:\ 
                                       
                  Tương đương : path[0]  , path[1]
              
pasteFile() : Paste toàn bộ file có path lấy từ mảng String[] path ở trên vào folder có path đang được chọn
        
        Ví dụ : Copy từ sourcePath : " path[0] = E:\hihi.txt
              
                                       path[1] = E:\1.rar " 
              
                Paste tại destPath : "New folder" có path : E:\New folder\
                      
                Sử dụng hàm Files.copy(sourcePath[i],destPath) được chạy trong vòng lặp for(i) để Copy toàn bộ file
             
*Hàm phụ/Chức năng phụ

delete() : xóa file đang được chọn

+ file đang được chọn có path tại textField tf_path 
          
+ Dùng hàm Files.delete(path) của thư viện java.nio để xóa file
          
        Ví dụ : file đang chọn : hihi.txt có path tại textField tf_path là E:\hihi.txt
          
        Xóa : Files.delete((new File(tf_path.getText().toPath)));
          
Open File : 

+ Bắt sự kiện khi click vào button Open 

        Lấy path của file đang được chọn trên textField tf_path

+ Sử dụng hàm 

        desktop.open(new File(tf_path.getText())); 
  
  của thư viện DeskTop để mở file
