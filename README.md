# win-explorer-java

Tên SV : Nguyễn Đình Trọng

Mã SV : 17IT112

Đề 07

Câu 1 : Thiết kế giao diện File Explorer

Câu 2 : Chức năng Copy nhiều files cùng lúc

+Chức năng phụ : Mở File,Xóa File

Link video hướng dẫn sử dụng : https://youtu.be/V47HhQ0Mhzk

# Cách chạy Code

Bắt sự kiện mouseReleased cho table : sẽ chạy hàm loadDataTable(MouseEvent);

+ Load dữ liệu trong hàm loadData:

      int row = table.getSelectedRow(); lấy vị trí đang chọn
      String name = table.getModel().getValueAt(row, 0).toString(); //lấy giá trị đang được chọn

+ Sử dụng giá trị "name " vừa lấy cùng với path hiện tại đề load table mới 

      loadFile(name,TableModel) // reload dữ liệu của table khi click vào folder name

+ Bật chức năng hỗ trợ chọn nhiều file cho Table bằng hàm : 
      
      table.setSelectionMode(ListSelectionModel.MULTIPLE_INTERVAL_SELECTION);

+ Sau đó lấy path của các file được chọn rồi lưu vào mảng String[] multiPath bằng các hàm

      multiRow[] = table.getSelectedRows(); //lấy count các file được chọn
      multiPath[i] = table.getModel().getValueAt(multirow[i], 0);
      
+ Sử dụng multiPath[i] để dùng cho hàm copyFile() và pasteFile() //Copy nhiều files

Bắt sự kiện mouseClicked cho Jtree : 

+ Load dữ liệu của tree mẹ và tree con bằng tổ hợp các hàm : 
      
      DefaultMutableTreeNode treeNode // Cấu trúc các tree folder
      treemodel = new DefaultTreeModel(treeNode); // Dữ liệu của Tree
      tree.setModel(treemodel);// Nạp dữ liệu vào tree
      createChildren(File fileRoot,DefaultMutableTreeNode root);//Tạo tree con dựa vào dữ liệu
      
JtextField tf_path đóng kết nối giữa Jtree và JTable, lấy các path của dữ liệu để các hàm có thể sử dụng

*Các hàm sử dụng :

DefaultTableModel loadFile() : dùng để load dữ liệu cho TableModel của JTable.

loadDataTable() : reload dữ liệu của Table khi có sự kiện click folder hoặc file.

createChildren() : Tạo tree con cho JTree.

treeAction() : Xổ các nhánh tree con khi có sự kiện click vào tree mẹ.

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

+ Sử dụng hàm desktop.open(new File(tf_path.getText())); của thư viện DeskTop để mở file
