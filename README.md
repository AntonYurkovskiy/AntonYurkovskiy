# Антон Юрковский

**Автоматизирую работу с документами и данными на Python:** разбор анкет, PDF и почты, перенос данных между системами, загрузка в учётные системы по API.

Работаю в морской отрасли, поэтому знаю документы экипажа и рабочие процессы изнутри. Знаю умею практикую в бюрократию и процессный подход крупных корпораций, постоянно декомпозирую безнес-процессы и оптимизирую их, понимаю что можно срезать для достижения конкретного результата. Делаю инструменты, которые заменяют ручной ввод: с логами, повторами при сбоях и тестами.

## Готовый кейс: перенос анкет моряков в crewing-систему

**[MARITIME-DATA-PARSER](https://github.com/AntonYurkovskiy/MARITIME-DATA-PARSER)** — массовая загрузка данных моряков из HTML-анкет в систему Заказчика через REST API.

| Было | Стало |
|---|---|
| Анкеты лежат файлами, данные переносят в crewing-систему вручную: основные данные, адреса, родственники, контракты, документы, фото | Запуск одной командой: файлы разбираются, данные приводятся к единому виду, проверяются и уходят в систему по API блоками |
| Повторный ввод даёт дубли | Обработанные файлы запоминаются, повторный запуск их пропускает |
| Сбой связи — потерянная запись | Автоповтор запросов при ошибках сервера (до 10 попыток), справочники API кэшируются |
| Непонятно, что загрузилось | JSON-отчёт и лог по каждому запуску |

Как устроено: конфигурируемые блоки загрузки (`blocks_config.yaml`), каждый проходит этапы «разбор → нормализация → проверка → сборка запроса → отправка». Новый блок добавляется без переписывания ядра. Проект покрыт 395 автотестами.

## В разработке

Эти две системы ещё не завершены (находятся в опытной эксплуатации). Демо на синтетических данных покажу по запросу.

- **Разбор заявок(заказ работы) и ваучеров(выполнение работы) из почты и PDF.** Письма по IMAP → разбор заявок и вложений → распознавание ваучеров (Tesseract, TrOCR для рукописных полей) → сопоставление заявки и ваучера → расчёт по тарифам с курсом ЦБ и производственным календарём → выгрузка в Excel. FastAPI.
- **Контроль сроков документов экипажа.** Реестр документов и их сроков, напоминания в Telegram заранее (за 90 / 60 / 30 дней), график ротации, разбор сканов документов.

## Что могу сделать

- Парсер или скрипт с загрузкой данных по API: с логами, повторами и защитой от дублей.
- Перенос базы анкет и данных: из HTML, Excel, выгрузок старой системы — в вашу систему или в таблицу по вашему шаблону.
- Разбор PDF, сканов и писем в Excel.
- Telegram-бот напоминаний о сроках документов.

Работаю по фиксированному объёму и сроку, один круг правок включён, гарантия 14 дней. Персональные данные не вывожу за контур клиента: решение ставится на вашей стороне, демонстрирую только на выдуманных данных.

## Стек

Python · FastAPI · REST API · SQL (PostgreSQL, SQLite) · pandas · Docker · Telegram Bot API · Tesseract / TrOCR · pytest, ruff, mypy

## Учебные проекты по анализу данных

Специализация Data Science, SkillFactory. Высшее техническое образование.

* [Анализ резюме из HeadHunter](https://github.com/AntonYurkovskiy/Project_1_hhVacancyAnalysis)
* [Анализ вакансий из HeadHunter (SQL)](https://github.com/AntonYurkovskiy/Project_2_SQL_hh_analiysis)
* [Проект для компании Booking: рейтинг отелей (EDA, feature engineering)](https://github.com/AntonYurkovskiy/Project_3_EDA_FE_BookingHotelsRating)
* [Финтех: выявление наиболее лояльных клиентов банка (ML)](https://github.com/AntonYurkovskiy/Project_4_ML_BankDeposits)
* [Предсказание продолжительности поездки на такси в Нью-Йорке (ML)](https://github.com/AntonYurkovskiy/Project_5_NY_City_Taxi_Trip_Duration)

## Связаться

- Telegram: [@YuAntonYu](https://t.me/YuAntonYu)
- E-mail: antonyurkovskiy@yandex.ru

---

## English

I automate document and data work in Python: parsing forms, PDFs and email, migrating data between systems, and loading it into business systems via API. I work in the maritime industry, so I know crew documents and workflows first-hand.

**Delivered:** [MARITIME-DATA-PARSER](https://github.com/AntonYurkovskiy/MARITIME-DATA-PARSER) — bulk loading of seafarer records from HTML résumés into a crewing system (360Crewing) via REST API. Blocks are sent separately (main info, addresses, relatives, contracts, documents, photo), with deduplication, automatic retries and a JSON report per run. 395 automated tests.

**In development** (demo on fictional data available on request): email and PDF intake with voucher OCR and tariff calculation; crew document expiry tracking with Telegram reminders.

**Stack:** Python, FastAPI, REST API, SQL (PostgreSQL, SQLite), pandas, Docker, Telegram Bot API, Tesseract / TrOCR, pytest.

**Contact:** [Telegram @YuAntonYu](https://t.me/YuAntonYu) · antonyurkovskiy@yandex.ru
