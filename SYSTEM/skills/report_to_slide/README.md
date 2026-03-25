# Навык report_to_slide

## Описание
Навык извлекает текст из PDF‑отчётов, выделяет ключевые тезисы (5‑7 пунктов) и сохраняет их в виде Markdown‑файла. Затем передаёт полученный Markdown в модель OpenRouter `google/gemini-3.1-flash-image-preview` для генерации инфографики‑слайда (PNG). Результаты сохраняются в папке `Outputs/`.

## Вход
- PDF‑файл, расположенный в папке `Inputs/` (или путь, переданный скрипту).

## Выход
- `Outputs/<basename>.md` – Markdown‑файл с основными тезисами отчёта.
- `Outputs/<basename>_slide.png` – сгенерированная инфографика (слайд).

## Требования
Python‑пакеты, указанные в `requirements.txt`:
- `pdfplumber` – извлечение текста из PDF.
- `requests` – HTTP‑запросы к OpenRouter.
- `python-dotenv` – загрузка переменных окружения (API‑ключ).

## Как использовать
1. Убедиться, что в корне проекта есть файл `.env` с переменной:
   ```
   OPENROUTER_API_KEY=sk-or-v1-<your-api-key-here>
   ```
2. Положить PDF‑файл в папку `Inputs/`.
3. Запустить скрипт:
   ```bash
   python SYSTEM/skills/report_to_slide/process.py Inputs/your_report.pdf
   ```
   (можно также просто `python SYSTEM/skills/report_to_slide/process.py` – скрипт обработает все PDF в `Inputs/`).
4. Результаты появятся в папке `Outputs/`.

## Пример
После обработки `Inputs/Q1_report.pdf` получаем:
- `Outputs/Q1_report.md`
- `Outputs/Q1_report_slide.png`