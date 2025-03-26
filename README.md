Это тестовая лаба для тренировки работы с Prometheus и Grafana.
Здесь nginx-exporter собирает метрики с приложения nginx. Которые отпровляются в Prometheus и ресуется в Grafana.

Как запустить:
1) В конфиге nginx-conf-test.conf который монтируется в nginx поменяйтся hosts на ваши адреса
2) Для Prometheus установите таргет в prometheus.yml для nginx-exporter.
3) docker-compose up -d

Как тестировать:
1) Проверяем что nginx работает http://localhost:80
2) Заходим в Prometheus http://localhost:9090 
Во вкладке Status -> Tragets можно проверить состояние работы таргета nginx-exporter.
Во вкладке Graph можно отправить запросы на получение метрик:
nginx_connections_active
nginx_connections_reading
nginx_connections_writing
nginx_connections_waiting
3) Заходим в Grafana. http://localhost:3000. Пороль: admin. Логин: admin
В разделе Connections -> Data Source создаем нашего сборщик метрик. В поле connections: http://prometheus:9090. Дальше Save&Test.
В разделе Dashboards ипортируем готовую досту для nginx-exporter. Можно использовать код: 12708. Или поискать готовые доски: https://grafana.com/grafana/dashboards
Указываем созданный сборщик метрик -> Import.

Если что-то не работает, смотрите логи, разбирайтесь)
