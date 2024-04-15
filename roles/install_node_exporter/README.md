Node Exporter не имеет конфигурационного файла и настраивается дополнительными ключами. Для того, чтобы каждый раз не перечитывать настройки systemd, список ключей вынесен в файл: /etc/sysconfig/node_exporter.<br>
```
tar xvfz node_exporter-0.18.1.linux-amd64.tar.gz
cd node_exporter-0.18.1.linux-amd64
mv node_exporter /usr/local/bin/

systemctl daemon-reload
systemctl start node_exporter
systemctl enable node_exporter
```
С помощью директивы: EnvironmentFile все переменные из указанного файла добавляются в env, что позволяет нам передавать список ключей для Node Exporter через переменную $OPTIONS без изменения службы.<br>
**Список наиболее востребованных ключей Node Exporter**<br>
```
--log.level
Default: info
```
Данный ключ устанавливает уровень логирования. Возможные уровни логирования:<br>
debug, info, warn, error.<br>
```
--log.format
Defult: logfmt
```
Данный ключ устанавливает формат логов. Доступные форматы: logfmt и json.
```
--web.listen-address
Default: ":9100"
```
Данный ключ устанавливает адрес и порт, по которому будет доступен Node Exporter.
```
--web.telemetry-path
Default: "/metrics"
```
Данный ключ устанавливает адрес, по которому доступны результаты экспозиции.
```
--web.disable-exporter-metrics
Default: -
```
Данный ключ устанавливает список метрик, которые будут исключены из экспозиции.<br>
Например, для исключения всех метрик, имя которых начинается с "go", значение ключа будет: go\*.<br>
Допускается использовать перечисление нескольких метрик, с запятой в качестве разделителя.<br>
Полный список ключей можно просмотреть с помощью команды help.
```
node_exporter --help
```
