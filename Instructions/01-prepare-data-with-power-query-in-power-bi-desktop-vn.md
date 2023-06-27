---
lab:
    title: 'Get Data in Power BI Desktop'
    module: 'Get Data in Power BI'
---

# Get Data in Power BI Desktop

## **Lab story**

Phòng thí nghiệm này được thiết kế để giới thiệu cho bạn về ứng dụng Power BI Desktop và cách kết nối với dữ liệu cũng như cách sử dụng các kỹ thuật xem trước dữ liệu để hiểu các đặc điểm và chất lượng của dữ liệu nguồn. Mục tiêu học tập là

- Mở Power BI Desktop
- Kết nối với các nguồn dữ liệu khác nhau
- Xem trước dữ liệu nguồn với Power Query
- Sử dụng các tính năng lược tả dữ liệu trong Power Query

**Phòng thí nghiệm này sẽ mất khoảng 30 phút.**

## **Bắt đầu với Power BI Desktop**

Trong tác vụ này, bạn bắt đầu bằng cách mở tệp Power BI (.pbix) khởi động. Tệp khởi động không chứa bất kỳ dữ liệu nào, nhưng đã được cấu hình đặc biệt để giúp bạn hoàn thành bài thực hành. Các cài đặt cấp báo cáo sau đã bị vô hiệu hóa trong tệp khởi động:

- Tải dữ liệu > Nhập mối quan hệ từ nguồn dữ liệu trong lần tải đầu tiên
- Tải dữ liệu > Tự động phát hiện các mối quan hệ mới sau khi dữ liệu được tải

*Lưu ý: Mặc dù bật hai tùy chọn này có thể hữu ích khi phát triển mô hình dữ liệu, nhưng bạn đã tắt chúng trước đó để hỗ trợ trải nghiệm phòng thí nghiệm. Khi bạn tạo các mối quan hệ trong phòng thí nghiệm **Load Data in Power BI Desktop**, bạn sẽ tìm hiểu lý do tại sao bạn thêm từng mối quan hệ.*

1. Mở Power BI Desktop.

    ![Power BI Desktop icon](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image1.png)

    *Mẹo: Theo mặc định, hộp thoại Bắt đầu sẽ mở ra trước Power BI Desktop. Bạn có thể chọn đăng nhập rồi đóng cửa sổ bật lên.*

1. Để mở tệp khởi động Power BI Desktop, hãy chọn **File > Open Report > Browse Reports**.

1. Trong cửa sổ **Open**, điều hướng đến **D:\PL300\Labs\01-prepare-data-with-power-query-in-power-bi-desktop\Starter**.

1. Chọn tệp **Sales Analysis**.

1. Lưu một bản sao của tệp **Save As** lưu tại thư mục **D:\PL300\MySolution**.

## **Get data from SQL Server**

Nhiệm vụ này hướng dẫn bạn cách kết nối với cơ sở dữ liệu SQL Server và nhập các bảng để tạo truy vấn trong Power Query.

1. Trên thanh công cụ chọn **Home** trong mục **Data** chọn **SQL Server**.

     ![SQL Server Get Data icon](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image11.png)

1. Trong cửa sổ **SQL Server Database**, nhập giá trị **Server** và **Database** tương ứng

1. Nếu được nhắc về thông tin đăng nhập, trong cửa sổ **SQL Server Database** hãy đăng nhập **Use my current credentials**, sau đó **Connect**.

1. Sử dụng **AdventureWorksDW2020** database.

1. Chọn—nhưng không check bảng **DimEmployee** 

     ![AdventureWorksDW2020 database with DimEmployee indicated](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image18.png)

1. Trong ngăn bên phải, hãy chú ý đến bản xem trước của dữ liệu bảng. Dữ liệu xem trước cho phép bạn xem các cột và mẫu hàng.

1. Tích chọn 6 bảng sau:

    - DimEmployee
    - DimEmployeeSalesTerritory
    - DimProduct
    - DimReseller
    - DimSalesTerritory
    - FactResellerSales

1. Hoàn thành tác vụ này bằng cách nhấp vào **Transform Data**, để mở Power Query Editor.
    1. *Lab này chỉ nhằm mục đích kết nối và lập hồ sơ dữ liệu chứ không phải **transform data**.*

## **Preview Data in Power Query Editor**

Tác vụ này giới thiệu Power Query Editor và cho phép bạn xem lại và lập hồ sơ dữ liệu. Điều này giúp bạn xác định cách làm sạch và chuyển đổi dữ liệu sau này.

1. Trong cửa sổ **Power Query Editor**, ở bên trái, hãy để ý ngăn **Queries**. Ngăn **Queries** chứa một truy vấn cho mỗi bảng mà bạn đã chọn.

     ![List of loaded queries](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image20.png)

1. Chọn truy vấn đầu tiên—**DimEmployee**.

    *Bảng **DimEmployee** trong cơ sở dữ liệu SQL Server lưu trữ một hàng cho mỗi nhân viên. Một tập hợp con của các hàng từ bảng này đại diện cho nhân viên bán hàng, những hàng này sẽ liên quan đến mô hình mà bạn sẽ phát triển.*

1. Ở góc dưới cùng bên trái của thanh trạng thái, một số thống kê bảng được cung cấp—bảng có 33 cột và 296 hàng.

     ![Count of 33 columns, 296 rows](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image22.png)

1. Trong ngăn xem trước dữ liệu, hãy cuộn theo chiều ngang để xem lại tất cả các cột. Lưu ý rằng năm cột cuối cùng chứa các liên kết **Table** hoặc **Value**.

    *Năm cột này thể hiện mối quan hệ với các bảng khác trong cơ sở dữ liệu. Chúng có thể được sử dụng để nối các bảng lại với nhau. Bạn sẽ nối các bảng trong phòng thí nghiệm **Load Data in Power BI Desktop**.*


1. Để đánh giá chất lượng cột, trên tab dải băng **View**, từ bên trong nhóm **Data Preview**, hãy chọn **Column Quality**. Tính năng chất lượng cột cho phép bạn dễ dàng xác định tỷ lệ phần trăm giá trị hợp lệ, lỗi hoặc trống được tìm thấy trong cột.

     ![Column Quality selection in ribbon](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image23.png)

1. Lưu ý rằng cột **Position** có 94% hàng trống (null).

     ![Column quality showing 94% empty rows](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image24.png)

1. Để đánh giá phân phối cột, trên tab dải băng **View**, từ bên trong nhóm **Data Preview**, hãy chọn **Column Distribution**.

1. Xem lại cột **Position** và lưu ý rằng có bốn giá trị riêng biệt và một giá trị duy nhất.

1. Xem lại phân phối cột cho cột **EmployeeKey**—có 296 giá trị riêng biệt và 296 giá trị duy nhất.

    *Khi số lượng khác biệt và duy nhất giống nhau, điều đó có nghĩa là cột chứa các giá trị duy nhất. Khi lập mô hình, điều quan trọng là một số bảng mô hình có các cột duy nhất. Bạn có thể sử dụng các cột duy nhất này để tạo mối quan hệ một-nhiều mà bạn sẽ thực hiện trong phòng thí nghiệm **Model Data in Power BI Desktop**.*

     ![Column distribution showing 296 distinct, 296 unique values](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image26.png)

1. Trong **Queries**, chọn **DimEmployeeSalesTerritory**.

    *Bảng **DimEmployeeSalesTerritory** lưu trữ một hàng cho mỗi nhân viên và khu vực lãnh thổ bán hàng mà họ quản lý. Bảng hỗ trợ liên kết nhiều vùng cho một nhân viên. Một số nhân viên quản lý một, hai hoặc có thể nhiều khu vực hơn. Khi lập mô hình dữ liệu này, bạn sẽ cần xác định mối quan hệ nhiều-nhiều.*

1. Trong **Queries**, chọn **DimProduct**. Bảng **DimProduct** thông tin sản phẩm được bán bởi công ty.

1. Cuộn theo chiều ngang để hiển thị các cột cuối cùng. Lưu ý cột **DimProductSubcategory**.

    *Khi bạn thêm các phép biến đổi vào truy vấn này trong phòng thí nghiệm **Load Data in Power BI Desktop**, bạn sẽ sử dụng cột **DimProductSubcategory** để nối các bảng.*

1. Trong **Queries**, chọn **DimReseller**.

    *Bảng **DimReseller** chứa một hàng cho mỗi người bán lại. Người bán lại bán, phân phối hoặc gia tăng giá trị cho các sản phẩm của Adventure Works.*

1. Trong tab **View** , chọn **Data Preview**, tích chọn **Column Profile**.

1. Chọn tiêu đề cột **BusinessType** và để ý ngăn mới bên dưới ngăn xem trước dữ liệu.

1. Xem lại thống kê cột và phân phối giá trị trong ngăn xem trước dữ liệu.

    *Lưu ý vấn đề về chất lượng dữ liệu: có hai nhãn cho kho hàng (**Warehouse** và **Ware House** bị viết sai chính tả).*

     ![Value distribution for the BusinessType column](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image31.png)

1. Di con trỏ qua thanh **Ware House** và lưu ý rằng có năm hàng có giá trị này.

    *Bạn sẽ áp dụng một chuyển đổi để gắn nhãn lại năm hàng này trong phòng thí nghiệm **Load Data in Power BI Desktop**.*

1. Trong **Queries**, chọn **DimSalesTerritory** query.  

    *Bảng **DimSalesTerritory** chứa một hàng cho mỗi khu vực bán hàng, bao gồm **Corporate HQ** (headquarters). Các khu vực được chỉ định cho một quốc gia và các quốc gia được chỉ định cho các nhóm. Trong phòng thí nghiệm **Model Data in Power BI Desktop**, bạn sẽ tạo cấu trúc phân cấp để hỗ trợ phân tích ở cấp khu vực, quốc gia hoặc nhóm.*

1. Trong **Queries**, chọn **FactResellerSales**.

    *Bảng **FactResellerSales** chứa một hàng trên mỗi dòng đơn đặt hàng—một đơn đặt hàng chứa một hoặc nhiều mục hàng.*

1. Xem lại chất lượng cột cho cột **TotalProductCost** và nhận thấy rằng 8% số hàng trống.

    *Thiếu các giá trị cột **TotalProductCost** là một vấn đề về chất lượng dữ liệu. Để giải quyết vấn đề này, trong phòng thí nghiệm **Tải dữ liệu trong Power BI Desktop**, bạn sẽ áp dụng các phép biến đổi để điền vào các giá trị còn thiếu bằng cách sử dụng chi phí tiêu chuẩn của sản phẩm, được lưu trữ trong bảng **DimProduct** có liên quan.*

## **Get data from a CSV file**

Trong nhiệm vụ này, bạn sẽ tạo một truy vấn mới dựa trên các tệp CSV.

1. Để thêm truy vấn mới, trong cửa sổ **Power Query Editor**, trên tab dải băng **Home**, từ bên trong nhóm **New Query**, hãy chọn mũi tên xuống **New Source**, rồi chọn **Văn bản/CSV**.

1.Trong cửa sổ **Open**, điều hướng đến thư mục **D:\PL300\Resources** và chọn tệp **ResellerSalesTargets.csv**. Chọn **Mở**.

1. Trong cửa sổ **ResellerSalesTargets.csv**, hãy xem lại dữ liệu xem trước. Chọn **OK**.

1. In the **Queries** pane, notice the addition of the **ResellerSalesTargets** query.

1. Trong ngăn **Queries**, hãy chú ý đến việc bổ sung truy vấn **ResellerSalesTargets**.

    *Tệp CSV **ResellerSalesTargets** chứa một hàng cho mỗi nhân viên bán hàng mỗi năm. Mỗi hàng ghi 12 chỉ tiêu doanh số hàng tháng (tính bằng nghìn). Năm kinh doanh của công ty Adventure Works bắt đầu vào ngày 1 tháng 7.*

1. Lưu ý rằng không có cột nào chứa giá trị trống. Khi không có mục tiêu bán hàng hàng tháng, ký tự gạch nối sẽ được lưu trữ thay thế.

1. Xem lại các biểu tượng trong mỗi tiêu đề cột, ở bên trái tên cột. Các biểu tượng đại diện cho kiểu dữ liệu cột. **123** là số nguyên và **ABC** là văn bản.

     ![Picture 74](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image38.png)

1. Lặp lại các bước để tạo truy vấn dựa trên tệp **D:\PL300\Resources\ColorFormats.csv**.

    *Tệp CSV **ColorFormats** chứa một hàng cho mỗi màu sản phẩm. Mỗi hàng ghi mã HEX để định dạng màu nền và phông chữ.*

*Bây giờ, bạn sẽ có hai truy vấn mới, **ResellerSalesTargets** và **ColorFormats**.*

 ![Queries list](Linked_image_Files/01-all-queries-loaded.png)

### **Finish up**

Trong nhiệm vụ này, bạn sẽ hoàn thành phòng thí nghiệm.

1. Trên tab dải băng **View**, từ bên trong nhóm **Data Preview**, hãy bỏ chọn ba tùy chọn xem trước dữ liệu đã được bật trước đó trong lab này:

    - Column quality
    - Column distribution
    - Column profile

     ![Picture 76](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image40.png)

1. **Save** the Power BI Desktop file. When prompted to apply the pending changes, select **Apply Later**.

1. **Save** tệp Power BI Desktop. Khi được nhắc áp dụng các thay đổi đang chờ xử lý, hãy chọn **Apply Later**.

    *Mẹo: Áp dụng các truy vấn sẽ tải dữ liệu của chúng vào mô hình dữ liệu. Bạn chưa sẵn sàng để làm điều đó, vì có nhiều phép biến đổi phải được áp dụng trước.*
