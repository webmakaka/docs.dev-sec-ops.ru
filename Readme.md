# Исходники сайта [docs.dev-sec-ops.ru](https://docs.dev-sec-ops.ru)

<br/>

## Запустить локально с возможностью редактирования

Инсталлируете docker и docker-compose, далее:

```
$ cd ~
$ mkdir -p docs.dev-sec-ops.ru && cd docs.dev-sec-ops.ru
$ git clone --depth=1 https://github.com/webmakaka/docs.dev-sec-ops.ru.git .
$ docker-compose up
```

<br/>

Остается в браузере подключиться к localhost:80

<br/>

## (Устарело!)

<br/>

### Запустить docs.dev-sec-ops.ru на своем хосте с использованием docker контейнера:

```
$ docker run -i -t -p 80:80 --name docs.dev-sec-ops.ru marley/docs.dev-sec-ops.ru
```

<br/>

### Как сервис

```
$ sudo vi /etc/systemd/system/docs.dev-sec-ops.ru.service
```

вставить содержимое файла docs.dev-sec-ops.ru.service

```
$ sudo systemctl enable docs.dev-sec-ops.ru.service
$ sudo systemctl start  docs.dev-sec-ops.ru.service
$ sudo systemctl status docs.dev-sec-ops.ru.service
```

http://localhost:4006

<br/><br/>

---

<br/>

**Marley**

Any questions in english: <a href="https://docs.dev-sec-ops.ru/chat/">Telegram Chat</a>  
Любые вопросы на русском: <a href="https://docs.dev-sec-ops.ru/chat/">Телеграм чат</a>
