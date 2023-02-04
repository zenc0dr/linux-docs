# Главное меню

Иконки хранятся в следующих дерикториях:

**Глобально (root) **/usr/share/applications

**Локально** ~/.local/share/applications



**Пример файла doom.desktop**

```
Comment=
Terminal=false
Name=Doom
Exec=gzdoom /home/zen/.config/gzdoom/brutalv21.pk3
Type=Application
Icon=/home/zen/Mega/Documents/Doom/doom_icon.png
Categories=Game
```



**Если файл нужно зарегистрировать в системе**

```bash
./doom.desktop --register-app
```



**Программа для управления главным меню**

```bash
sudo apt install -y alacarte
```

