# Полезные команды для RAS/RAC
Если нет возможности запустить стандартную консоль администрирования сервера 1С, [irac](https://github.com/arkuznetsov/irac), [OneS_ClusterAdmin](https://github.com/YanSergey/OneS_ClusterAdmin) и т.п., но есть доступ к ras/rac

### Запуск RAS на нестандартом порту

```sh
ras --port=2545 cluster buh-srv01
```

### Получение списка кластеров

```sh
rac localhost:2545 cluster list
```

### Получение списка баз в кластере

```sh
rac localhost:2545 infobase summary list --cluster=<cluster-guid>
```

### Получение списка сеансов в базе

```sh
rac localhost:2545 session list --cluster=<cluster-guid> --infobase=<infobase-guid>
```

### Установка блокировки сеансов на базу

```sh
rac localhost:2545 infobase update --cluster=<cluster-guid> --infobase=<infobase-guid> --infobase-user=<user> --infobase-pwd=<pwd> --denied-message="<msg>" --denied-from=<yyyy-MM-ddThh:mm:ss> --denied-to=<yyyy-MM-ddThh:mm:ss> --permission-code=<unlock_code> --sessions-deny=on --scheduled-jobs-deny=on
```

### Снятие блокировки сеансов

```sh
rac localhost:2545 infobase update --cluster=<cluster-guid> --infobase=<infobase-guid> --infobase-user=<user> --sessions-deny=off --scheduled-jobs-deny=off
```

### Завершение определенного сеанса

```sh
rac localhost:2545 session terminate --cluster=<cluster-guid> --session=<session-guid>
```
