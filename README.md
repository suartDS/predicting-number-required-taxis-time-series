# Строим ML Модели на PySpark для предсказания количества такси

Цель проекта
Описание: В нашем распоряжении около 10 млн записей о поездках такси в Чикаго и перед нами стоит задача предсказать количество заказов на следующий час в каждом округе. Решать будем с применением PySpark.

Цель проекта: Построить ML модель на Spark предсказания количества заказов на следующий час для каждого района

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