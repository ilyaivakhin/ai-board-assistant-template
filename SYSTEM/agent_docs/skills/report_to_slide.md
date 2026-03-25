# Навык report_to_slide

Навык извлекает текст из PDF‑отчётов, выделяет ключевые тезисы (5‑7 пунктов) и сохраняет их в виде Markdown‑файла. Затем передаёт полученный Markdown в модель OpenRouter `google/gemini-3.1-flash-image-preview` для генерации инфографики‑слайда (PNG). Результаты сохраняются в папке `Outputs/`.

## Как использовать
Поместите PDF‑файл в папку `Inputs/` и выполните:
`python SYSTEM/skills/report_to_slide/process.py Inputs/your_report.pdf`

Результаты:
- `Outputs/your_report.md` – Markdown с тезисами.
- `Outputs/your_report_slide.png` – сгенерированная инфографика.

## Требования
- pdfplumber
- requests
- python-dotenv

Убедитесь, что в корне проекта есть файл `.env` с переменной `OPENROUTER_API_KEY`.