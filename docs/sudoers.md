# Sudoers - Запуск без ввода sudo

```
sudo subl /etc/sudoers
```

```
zen ALL=(ALL) NOPASSWD: /usr/sbin/sup
zen ALL=(ALL) NOPASSWD: /bin/apt

```

> В конце файла должен быть перенос строки, иначе будет ошибка
