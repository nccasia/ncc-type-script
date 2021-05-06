Metadata Reflection
Các ngôn ngữ như C#, Java ... đều hỗ trợ metadata cho Class , cũng như các hàm API để đọc và ghi metadata cho Class.

Việc đọc , ghi metadata này rất hữu ích khi ta muốn thực hiện logic dựa trên việc kiểm tra thông tin về kiểu (type inference) của class cũng như property trong run-time.

Hiện tại, javascript thuần hỗ trợ type inference rất nghèo nàn 😦 với chỉ một số quen thuộc:

typeof và instanceof (trả về kiểu của object được kiểm tra)
Object.getOwnPropertyDescriptor() , Object.keys() (trả về danh sách các property hay key của object)
Tương tự với việc Decorator được hứa hẹn sẽ xuất hiện chính thức trong ES7, metadata reflection cũng được hứa hẹn ít nhất sẽ xuất hiện dưới dạng prototype kể từ ES7, và được implement chính thức vào javascript sau.

Tuy nhiên, từ bây giờ, ta có thể sử dụng thư viện reflect-metadata để sử dụng các API này. Hiện tại, bộ API này đã hỗ trợ việc đọc và ghi metadata cho đối tượng thông qua các hàm:

defineMetadata: thêm 1 metadata key cho target.
hasMetadata: kiểm tra tồn tại của 1 metadata dựa theo key.
getMetadata : lấy ra 1 metadata dựa theo key.
deleteMetadata: xóa 1 metadata.
getMetadataKeys:
...
Kết hợp với decorator , ta có thể giải quyết 1 số bài toán cần tới việc kiểm tra xử lý đối tượng trong run-time dựa theo thông tin về Class hay Type của đối tượng đó.


https://viblo.asia/p/typescript-decorator-va-metadata-reflection-m68Z0w2dKkG
