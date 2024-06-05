# Pakun_Ryazanov_pg
# Описание
PostgreSQL состоит из Docker-контейнеров : Master, Slave и Arbiter.
Slave повышается до мастера, если теряется связь Slave -> Master и подтверждается Arbiter.
Если у Slave нет связи с Master и Arbiter, то переключение не происходит.
Каждую секунду Slave проверяет связь Slave -> Master и Arbiter -> Master.
Раз в 6 секунд Master проверяет связь Master -> Slave и Master -> Arbiter. В случае отсутствия обеих связей происходит блокировка всех входящих подключений на Master через iptables, путём изменения политики по умолчанию на DROP.
# Запуск
Запуск кластера: ```docker compose up```
Запуск тестирования кластера ```python writer.py```

