---
title: Запуск трансляции радио в группе
date: 2026-02-11 12:00:00 +0200
categories: [Разделы, Telegram]
tags: [telegram]     
---

Вечная трансляция радио в Telegram

Для запуска "вечной" трансляции радио в группу телеграм нужно:

- Скачать программу ffmpeg
- Получить ключ трансляции в группу
- Найти сайт с потоком радио (например, [https://streams.bigfm.de](https://streams.bigfm.de/bigfm-usrap-128-mp3))
- Запустить скрипт, в котором указать:
  - Путь к программе ffmpeg
  - Сайт с потоком радио
  - Ключ трансляции

Общий вид скрипта

```bat
@echo off
:loop
E:\ffmpeg-8.0.1-essentials_build\bin\ffmpeg.exe -re -i https://streams.bigfm.de/bigfm-usrap-128-mp3 ^
  -c:a aac -b:a 192k ^
  -f flv "rtmps://dc4-1.rtmp.t.me/s/ваш ключ трансляции"
if errorlevel 1 (
    echo ===================== Ошибка! Перезапуск через 10 сек... =====================
    timeout /t 10 >nul
) else (
    echo ===================== Стрим упал. Перезапуск через 10 сек... =====================
    timeout /t 10 >nul
)
goto loop

```

Можно [скачать архив](https://gzublack.com/downloads/ffmpeg-8.0.1+%20script%20for%20TG%20RADIO.rar), где уже есть программа ffmpeg и скрипт .bat, который можно отредактировать под свои параметры и запустить "радио".
