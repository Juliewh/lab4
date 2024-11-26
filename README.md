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

4. Запускаем контейнер:

```
docker run --rm aafire
```

5. Горим:
![изображение](https://github.com/user-attachments/assets/4cc6e393-e64a-419b-a34c-c1a286850221)

6. В Dockerfile пишем:

```
FROM ubuntu:latest
RUN apt-get update && apt-get install -y libaa-bin iputils-ping
ENV TERM=xterm
CMD ["/bin/bash"]
```

7. Собираем образ:

```
docker build -t myfire .
```

8. Запускаем два контейнера:

```
docker run -dit --name container1 myfire
docker run -dit --name container2 myfire
```

9. Создаем сеть с помощью команды:

```
docker network create myNetwork
```

10. Подключаем контейнеры к сети:

```
docker network connect myNetwork container1
docker network connect myNetwork container2
```

11. Проверяем настройки сети, чтобы убедиться, что оба контейнера подключены к созданной сети:

```
docker network inspec myNetwork
```

12. Подключаемся к первому контейнеру и испольщуем `ping` для проверки связи со вторым контейнером (IP адреса мы узнали из проверки настройки сети):

```
docker exec -it container1 bash
ping 172.18.0.3
```

![изображение](https://github.com/user-attachments/assets/80a4135f-6bc5-4037-afc4-fcacf1a6ab95)

13. Аналогично проверяем второй контейнер:

```
docker exec -it container2 bash
ping 172.18.0.2
```
![изображение](https://github.com/user-attachments/assets/f882595f-4018-48f2-b257-3b7e1fa7a46b)

## 14. Все супер, все работает!
