# Individual reflection

## 1. Role cụ thể trong nhóm

Develop chính, thiết kế system architect, quyết định các tech-stack, phương án crawl web, crawl dữ liệu, đánh nhãn dữ liệu, xử lý dữ liệu, trực tiếp tham gia coding và hỗ trợ các thành viên trong nhóm phát triển

## 2. Đóng góp cụ thể

- Implement and design multi-agent với 2 agent, 4 tools và 1 function calling:

```yaml
- Tool get_car_specs: Tra cứu thông số kỹ thuật, ưu nhược điểm, đối tượng phù hợp của xe Vinfast, thông số, ưu/nhược điểm, use_case, đối tượng, reasoning,
- Tool load_model: Tạo môi trường ảo sandbox biên dịch giải mã các model hiển thị 3D, chọn các model, image theo context và indexing.
- Tool calculate_car_match: Tính toán mức độ phù hợp của các dòng xe Vinfast với nhu cầu khách hàng dựa trên nhiều tiêu chí của khách hàng: budget, use_case, seats, fuel_type. Tool call này sẽ sử dụng context thu thập trích xuất intent, entity từ context người dùng, thực hiện truy xuất vào vector_db FAISS gồm các dữ liệu chuẩn bị cho retrive. Thiết kế trên cơ sở RAG Architect.
- Tool DuckDuckGo web search: Thực hiện web search lên toàn bộ, tra cứu trích xuất các intent từ các bài đánh giá, review về xe Vinfast, tổng hợp lại và gửi vào LLM làm context đánh giá.
- Function summmerier tạo vòng loop cho Reinforcement Learning nâng cấp RAG context sau này. Tự động sử dụng LLM thứ 2 để tổng hợp tóm tắt lại các đánh giá bằng phương án hook langgraph state _stop. Sau đó tự động load update vector_db theo lập lịch.
```

- Xử lý làm sạch, đánh nhãn dữ liệu làm nguồn cho vector_db. Xây dựng pipeline RAG truy xuất thực hiện đảm bảo context đúng với yêu cầu người dùng ở mọi case.
- Thiết kế luồng graph, LLM calling tool, func, loop, đề xuất các phương án triển khai system architect, quản lý prompt version.
- Lên phương án chuẩn bị dữ liệu, trực tiếp phát triển Frontend, implement logic fe với js.

## 3. SPEC mạnh/yếu

- **Mạnh nhất:** User stories 4 paths cụ thể, có hướng giải quyết cho từng path.
- **Yếu nhất:** Sync thủ công mỗi tuần hoặc khi có campaign mới. Chưa tính toán được việc sync đảm bảo health hệ thống nếu khả năng triển khai thành product.

## 4. Đóng góp khác

- Debug và phân chia task trong việc dev, thực hiện review code và đưa các phương án thiết kế kiến trúc, phân tích triển khai cho các thành viên
- Tham gia test, handle một số các lỗi test đặc biệt như cần reasoning mạnh, context sâu. Review các test cho các thành viên và phương hướng sửa đổi fix.
- Design workflow loop tự cải thiện context của RAG system, đảm bảo hệ thống phải đúng trong tất cả các test case.

## 5. Điều học được

- Tham gia hackathon build nhanh một mvp, kĩ năng làm việc nhóm, kĩ năng phát triển, cách phân tích, đánh giá các vấn đề và phương hướng xử lý.

## 6. Nếu làm lại

- Thu thập đa dạng dữ liệu và làm giàu dữ liệu nhiều hơn, đánh nhãn, clean data hơn nữa.
- Hoàn chỉnh các tính năng, không nên quá chú trọng hoàn thiện cần táo bạo thử nghiệm hơn nữa.

## 7. AI giúp gì / AI sai gì

- **Giúp:** brainstorm các phương hướng xử lý, sử dụng AI coding tăng tốc độ build sản phẩm.
- **Sai/mislead:** AI sai ở chỗ đôi khi ở những bước rất quan trọng đối với kiến trúc hệ thống, thường đề xuất những phương án triển khai khác nhau, nếu không kĩ lưỡng có thể chọn sai phương án và làm hỏng cả một sản phẩm, ảnh hưởng đến các thành viên khác.
- **Bài học:** sử dụng AI là công cụ, không phải quyết định.
