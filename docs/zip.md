# ZIP

https://www.cyberciti.biz/faq/how-to-zip-a-folder-in-ubuntu-linux/
https://ilso.ru/linux-how-to-archive-a-directory-in-a-zip-archive/

```sh
zip -r filename.zip folder
```

```sh
unzip filename.zip
```



### Опции

| Ключ | Описание                                                     |
| ---- | ------------------------------------------------------------ |
| -f   | освежить: только измененные файлы                            |
| -u   | обновление: только измененные или новые файлы                |
| -d   | удалить записи в zipfile                                     |
| -m   | удалить файлы после сжатия                                   |
| -r   | рекурсия по каталогам                                        |
| -j   | нежелательные (не записывать) имена каталогов                |
| -0   | только хранить                                               |
| -l   | конвертировать LF в CR LF (-ll CR LF в LF)                   |
| -1   | сжать быстрее                                                |
| -9   | сжать лучше                                                  |
| -q   | тихая работа                                                 |
| -v   | подробная информация                                         |
| -c   | добавить однострочные комментарии                            |
| -z   | добавить комментарий                                         |
| -@   | читать имена из стандартного ввода                           |
| -o   | сделать zip файл старым                                      |
| -x   | исключить следующие имена                                    |
| -i   | включать только следующие имена                              |
| -F   | исправить zip файл (-FF try harder)                          |
| -D   | не добавлять записи каталога                                 |
| -A   | настроить самораспаковывающийся архив                        |
| -J   | убрать префикс zip файла (unzipsfx)                          |
| -T   | проверка целостности zip файла                               |
| -X   | eXclude eXtra file attributes                                |
| -y   | хранить символические ссылки в виде ссылки вместо ссылочного файла |
| -e   | шифровать                                                    |
| -n   | не сжимать суффиксы                                          |
| -h2  | показать больше помощи                                       |