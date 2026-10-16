source .venv/Scripts/activate
uv run mkdocs build -f vi/mkdocs.yml --strict

uv run mkdocs serve -f vi/mkdocs.yml


uv run mkdocs serve -f vi/mkdocs.dev.yml