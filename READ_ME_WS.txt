Cấu hình chạy auto test api workspace - jmeter
1. Cài jemter
2. Cài Property file reader cho jemter: copy file tag-jmeter-extn-1.1.jar vào folder ../lib/ext 
3. Cài Parallel Controller cho jemter: copy file jmeter-parallel-0.12.jar vào folder ../lib/ext 
4. Tắt đi bật lại jemter.
5. Cấu hình giá trị cho các biến sử dụng khi chạy api - config: workspace_variable: 
	- TokenDelegatedPermission - token do mobile truyền lên 
	- LoginEmailArray - chuỗi các email đăng nhập khi sử dụng workspace, format: email1,email2,email3,...
	- LoginUserIDArray - chuỗi userID tương ứng với từng email trong chuỗi LoginEmailArray, format: userid1,userid2,.....
	- SubjectUpdateArray - chuỗi các subject có thể được chọn để update appoinment, format: subject1,subject2,subject3....
	- TimeSpan - Độ dài thời gian của các appointment - phút
	- Is365 - Mode Online or On-Premse
	- SearchResource_Text - Text tìm kiếm resource - vd: room301 -> search ra 1 tập room 3010 -> 3019
	- rowsPerPage - Số bản ghi load mỗi trang
	- FindColleague_Text - Text tìm kiếm Colleague -> vd: int -> search full intune
	- LoginEmailArrayBase64 - Chuỗi các email đăng nhập tương ứng với chuỗi LoginEmailArray nhưng được mã hóa base64
	- SearchResource_ResourceType - id resource type tìm kiếm
	- SearchAttendees_Text - Text tìm kiếm attendee lúc thêm appointment
6.Các cầu trên server:
	- Cấu hình push notification cho workspace.
	- Cấu hình các room có tiền tố giống nhau, khoảng 10 room: vd room3010 -> 3019
	- Cấu hình > 2 floor plan, chia và vẽ full các room vào các floorplan
	- Có thể add thêm Category, Find Colleague Option để xem kết quả trả về của api liên quan.
	- Có thể add thêm Confirm reservation vài resource + parameter ShowQRCode để test case chạy thêm các api liên quan đến confirm reservation.
7.Chạy phần test cho workspace 
	- ctrl + left click vào 3 thread group: "Search,Create - WS", "List,Detail,Master,Update,Confirm - WS", "FindColleague, Get List Appointment, Get Detail - WS"
	- right click -> start