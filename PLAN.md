# Kế hoạch dịch và build bản tiếng Việt

Mục tiêu: dịch tài liệu tiếng Anh trong `en/docs` thành một website tiếng Việt
độc lập tại đường dẫn `/vi/`.

## 1. Tạo cấu trúc bản dịch

Chạy tại thư mục gốc repository:

```bash
cp -R en/docs vi/docs
cp en/mkdocs.yml vi/mkdocs.yml
```

Sau đó dịch nội dung Markdown trong `vi/docs` và cập nhật `vi/mkdocs.yml`.

## 2. Cấu hình `vi/mkdocs.yml`

Giữ dòng kế thừa cấu hình chung:

```yaml
INHERIT: ../mkdocs.yml
```

Đặt các giá trị riêng cho bản tiếng Việt:

```yaml
site_name: Hello Algo
site_url: https://ten-mien-cua-ban/vi/
site_description: "Giáo trình cấu trúc dữ liệu và giải thuật có minh họa"
docs_dir: ../build/vi/docs
site_dir: ../site/vi
edit_uri: tree/main/vi/docs

theme:
  custom_dir: ../build/overrides
  language: vi
  font:
    text: Inter
```

- Dịch các nhãn trong `nav:` để dịch mục lục.
- Dịch các chuỗi giao diện như `Dark mode`, `Light mode`, `Recently Added`.
- Cập nhật `extra.alternate` để có mục chuyển sang `Tiếng Việt` với `link: /vi/` và `lang: vi`.

Nếu chỉ host tiếng Việt ở domain gốc (không có `/vi/`), dùng `site_url` là
`https://ten-mien-cua-ban/` và `site_dir: ../site`.

## 3. Cài công cụ bằng uv

Project hiện chưa có `pyproject.toml`; cài dependency vào môi trường ảo cục bộ:

```bash
uv venv
uv pip install 'mkdocs-material==9.5.5' mkdocs-glightbox
```

Hai dependency này khớp với `Dockerfile` hiện tại.

## 4. Chuẩn bị thư mục build

`mkdocs.yml` không đọc trực tiếp từ `vi/docs`; nó đọc bản staging tại
`build/vi/docs`. Trước khi preview hoặc build, chạy:

```bash
mkdir -p build
rm -rf build/overrides build/vi/docs
cp -R overrides build/overrides
mkdir -p build/vi
cp -R vi/docs build/vi/docs
```

Lệnh `rm -rf` trên chỉ xóa output/staging được tạo lại bên trong `build/`,
không đụng đến nội dung nguồn trong `vi/docs`.

## 5. Preview khi dịch

```bash
uv run mkdocs serve -f vi/mkdocs.yml
```

Mở `http://127.0.0.1:8000/vi/`. Sau khi sửa Markdown, hãy chạy lại bước 4 để
đồng bộ `vi/docs` sang `build/vi/docs` (hoặc thay bằng script đồng bộ sau này).

## 6. Build kiểm tra và deploy

```bash
uv run mkdocs build -f vi/mkdocs.yml --strict
```

Website tĩnh được tạo tại `site/vi/`. Upload nội dung thư mục này lên static
hosting. `site/` đã được `.gitignore`, nên không commit output build.

## 7. Việc nên làm tiếp theo

1. Tạo `vi/mkdocs.yml` và dịch navigation trước.
2. Dịch theo từng chapter trong `vi/docs`.
3. Chạy build với `--strict` trước mỗi lần deploy để bắt lỗi link/cấu hình.
4. Khi quy trình ổn định, thêm `pyproject.toml` và `uv.lock` để CI và máy khác
   dùng đúng phiên bản dependency.
