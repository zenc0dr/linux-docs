# WireGuard

https://serverspace.ru/support/help/kak-ustanovit-wireguard-vpn-client-na-ubuntu-linux/

## становка клиентского приложения WireGuard на Ubuntu

Установка WireGuard клиента происходит так же, как и на стороне сервера.

Войдите по SSH на Linux сервер, после входа в систему проверьте, обновлена ли машина, выполнив следующую команду:

```bash
sudo apt-get update && sudo apt-get upgrade
```

Теперь установите WireGuard, выполнив следующую команду:

```bash
sudo apt-get install wireguard
```



![Установка WireGuard](/home/zen/Documents/Mega/Documents/mytxt/docs-base/Linux/docs/wireguard.assets/vpn02-600x462.png)



## Генерация закрытого и открытого ключей

WireGuard работает путем шифрования соединения с помощью пары криптографических ключей. Пара ключей используется путем передачи открытого ключа другой стороне, которая затем может зашифровать свое сообщение таким образом, что оно может быть расшифровано только с помощью соответствующего закрытого ключа. Для обеспечения безопасности двусторонней связи каждая сторона должна иметь собственные закрытый и открытый ключи, так как каждая пара обеспечивает только односторонний обмен сообщениями.

Сгенерируйте пару открытого и закрытого ключей клиента, для этого выполните следующую команду:

```bash
wg genkey | tee private.key | wg pubkey > public.key
```

После этого создайте файл конфигурации клиента, в следующем каталоге:

```bash
sudo nano /etc/wireguard/wg0.conf
```

В файле пропишите:

```
[Interface] PrivateKey = <contents-of-client-privatekey> Address = 10.0.0.1/24 PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE ListenPort = 51820 [Peer] PublicKey = <contents-of-server-publickey> AllowedIPs = 10.0.0.2/32
```

Примечания: В строку publickey вставьте публичный ключ сервера, который мы сгенерировали в предыдущей статье, а в private key вставьте закрытый ключ клиента.

## Запуск WireGuard

Для запуска соединения введите следующую команду:

```bash
sudo wg-quick up wg0
```



![Запуск WireGuard ](/home/zen/Documents/Mega/Documents/mytxt/docs-base/Linux/docs/wireguard.assets/vpn1.png)



Теперь клиент может общаться с сервером, можно пропинговать сервер с клиента командой

```
ping 10.0.0.1
```



![WireGuard Пингование клиента](/home/zen/Documents/Mega/Documents/mytxt/docs-base/Linux/docs/wireguard.assets/vpn2.png)



Чтобы узнать статус соединения, выполните следующую команду:

```
sudo wg show
```

Вы получите все детали соединения, как показано ниже



![WireGuard VPN](/home/zen/Documents/Mega/Documents/mytxt/docs-base/Linux/docs/wireguard.assets/vpn3.png)



Поздравляю! Теперь ваш клиентский компьютер имеет доступ к VPN сети.



**Если возникла ошибка:** /usr/bin/wg-quick: line 32: resolvconf: command not found

https://superuser.com/questions/1500691/usr-bin-wg-quick-line-31-resolvconf-command-not-found-wireguard-debian

```bash
ln -s /usr/bin/resolvectl /usr/local/bin/resolvconf
```





**ChatGPT** Для настройки клиента WireGuard на Ubuntu 20.04 необходимо следующее:

1. Установите WireGuard: 
```bash
sudo apt install wireguard
```

2. Создайте конфигурационный файл WireGuard с именем `.conf` и добавьте в него необходимые настройки.

3. Запустите WireGuard с помощью файла настройки: 
```bash
sudo wg-quick up /etc/wireguard/<name>.conf
```

4. Проверьте статус WireGuard: 
``` bash
sudo wg
```

```
ln -s /usr/bin/resolvectl /usr/local/bin/resolvconf
```
