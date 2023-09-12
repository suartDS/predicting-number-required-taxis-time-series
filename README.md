# Строим ML Модели на PySpark для предсказания количества такси

Цель проекта
Описание: В нашем распоряжении около 10 млн записей о поездках такси в Чикаго и перед нами стоит задача предсказать количество заказов на следующий час в каждом округе. Решать будем с применением PySpark.

Цель проекта: Построить ML модель на Spark предсказания количества заказов на следующий час для каждого района

## Исходные данные:

■ Данные за 2022 год:   
https://data.cityofchicago.org/Transportation/Taxi-Trips-2022/npd7-ywjz

■ Данные за 2023 год:
https://data.cityofchicago.org/Transportation/Taxi-Trips-2023/e55j-2ewb

## Описание данных

- Trip ID - A unique identifier for the trip.
- Taxi ID - A unique identifier for the taxi.
- Trip Start Timestamp - When the trip started, rounded to the nearest 15 minutes.
- Trip End Timestamp - When the trip ended, rounded to the nearest 15 minutes.
- Trip Seconds - Time of the trip in seconds.
- Trip Miles - Distance of the trip in miles.
- Pickup Census Tract - The Census Tract where the trip began. For privacy, this Census Tract is not shown for some trips. This column often will be blank for locations outside Chicago.
- Dropoff Census Tract - The Census Tract where the trip ended. For privacy, this Census Tract is not shown for some trips. This column often will be blank for locations outside Chicago.
- Pickup Community Area - The Community Area where the trip began. This column will be blank for locations outside Chicago.
- Dropoff Community Area -The Community Area where the trip ended. This column will be blank for locations outside Chicago.
- Fare - The fare for the trip.
- Tips -The tip for the trip. Cash tips generally will not be recorded.
- Tolls -The tolls for the trip.
- Extras - Extra charges for the trip.
- Trip Total - Total cost of the trip, the total of the previous columns.
- Payment Type - Type of payment for the trip.
- Company -The taxi company.

![Alt text](data:image/png;base64,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)