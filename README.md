# -netology-ml-netology-ml
Выполнение домашнего задания  «Docker и микросервисная архитектура».

Dockerfile для создания контейнера с Python и Miniconda.

1. В качестве основы, берём образ continuumio/miniconda3:latest
2. Добавляем и делаем рабочей папкой /app
3. Создаём простой sh файл с названием 1.sh, который должен выдавать надпись “Hello Netology”.
4. Надо скопировать этот файл внутрь контейнера и выдать ему права на исполнение.
5. Запустить установку пакетов python mlflow boto3 pymysql.
6. В конце запустить на вывод файл 1.sh.
7. После чего собрать через docker build контейнер с тегом netology-ml:netology-ml

#Команды и путь выполнения ДЗ

1. Создание директории (командная строка): mkdir netology-docker
2. Перейти в директорию (командная строка): cd netology-docker
3. Создайте файл Dockerfile с таким содержимым (можно через командную строку иои через создание документа, но не текстовый формат (!!!!):

# Используем базовый образ Miniconda3
FROM continuumio/miniconda3:latest

# Создаем рабочую директорию
WORKDIR /app

# Создаем скрипт 1.sh с текстом "Hello Netology"
RUN echo 'echo "Hello Netology"' > /app/1.sh

# Даем права на выполнение скрипта
RUN chmod +x /app/1.sh

# Устанавливаем нужные пакеты Python
RUN conda install -y mlflow boto3 pymysql

# Запускаем 1.sh при старте контейнера
CMD ["/bin/sh", "/app/1.sh"]


4. Собираем контейнер (командная строка): docker build -t netology-ml:netology-ml .
5. Запускаем контейнер (командная строка): docker run --rm netology-ml:netology-ml
6. Ожидаем результат: Hello Netology
7. Вы прекрасны...)


![Лог сборки контейнера_результат](https://github.com/user-attachments/assets/d3d7c6de-20cb-4cec-a4c2-456fab596bb5)





