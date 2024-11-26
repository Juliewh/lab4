# Лабораторная работа 4.

1. Создадим Dockerfile в директории lab4
2. Содержимое файла:

```
FROM ubuntu:latest
RUN apt-get update && apt-get install -y libaa-bin
ENV TERM=xterm
CMD ["aafire"]
```
3. Собираем образ:

```
docker build -t aafire .
```

4. Запускаем контейнер

```
docker run --rm aafire
```

5. Горим
![изображение](https://github.com/user-attachments/assets/4cc6e393-e64a-419b-a34c-c1a286850221)
