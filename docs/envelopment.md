# Системное окружение

**Полезные ссылки:** https://losst.ru/peremennye-okruzheniya-v-linux



**Локально для конктертного пользователя**

```bash
$ sudo subl ~/.bashrc
```

**Глобально для всех пользователей**

```bash
$ sudo subl /etc/environment
```

**Применить переменные окружения**

```bash
$ source /etc/environment
```

**Писать**

```bash
export CD='Моё значение переменной'
```



Если у нас есть некий скрипт или бинарник и мы хотим запускать его через терминал не вводя полный путь к нему, нужно добавить в окружение папку в которой он находится

```bash
$ sudo subl ~/.profile
```

```bash
export PATH=~/.npm-global/bin:$PATH
```



**Применить**

```bash
$ source ~/.profile
```

