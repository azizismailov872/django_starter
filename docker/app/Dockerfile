FROM python:3.11-slim

# Установим системные зависимости, необходимые для mysqlclient и других библиотек
RUN apt-get update && apt-get install -y \
    build-essential \
    default-libmysqlclient-dev \
    libssl-dev \
    libffi-dev \
    python3-dev \
    pkg-config \
    gcc \
    && apt-get clean

# Установим рабочую директорию
WORKDIR /app

# Копируй файл requirements.txt и установи зависимости
COPY requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt


# Копируем оставшиеся файлы проекта (если есть)
COPY . /app/

# Команда для запуска сервера
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
