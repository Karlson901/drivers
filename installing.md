# дай пошаговую установку из уже скачанного Linux-Driver.tar.gz без интернета

Да. Ниже — установка **полностью из уже скачанного** `Xerox_Phaser_3020_Linux-Driver.tar.gz`, без интернета. В источниках для Phaser 3020 указано, что архив распаковывается в каталог `uld`, а затем запускается `install-printer.sh` или `install.sh`.[^1][^2]

## Подготовка

1. Положи архив в, например, `~/Downloads/`.
2. Убедись, что у тебя есть права `sudo`.
3. Закрой старые очереди CUPS для этого принтера, если они уже созданы.[^3][^1]

## Распаковка

Перейди в папку с архивом и распакуй его:

```bash
cd ~/Downloads
tar -xvf Xerox_Phaser_3020_Linux-Driver.tar.gz
```

После распаковки обычно появляется папка `uld`.[^2][^1]

## Установка

Перейди в `uld` и запусти установку:

```bash
cd uld
sudo ./install-printer.sh
```

Если этого скрипта нет, попробуй:

```bash
sudo ./install.sh
```

В обсуждениях по Phaser 3020 именно эти команды приводятся как рабочие для локальной установки.[^1][^2]

## Если хочешь без авто-регистрации

Можно не запускать скрипт, а сначала посмотреть содержимое папки `uld` и найти PPD-файл вручную, после чего добавить принтер в CUPS через `lpadmin` или веб-интерфейс.[^3][^1]
Для тебя это полезно, если хочешь контролировать, куда именно ставится драйвер и какой PPD используется.[^4][^3]

## Проверка в CUPS

После установки:

1. Открой `http://localhost:631/`.
2. Удали старую очередь, если она есть.
3. Создай новую очередь для USB-принтера.
4. Выбери установленный PPD из пакета Xerox.[^5][^1]

## Если установка не проходит

Если `install-printer.sh` ругается на отсутствие зависимостей, значит скрипту нужны локальные системные пакеты, а не интернет.[^6][^1]
В таком случае посмотри, какие пакеты он просит, и поставь их из репозиториев твоей системы заранее.[^1][^3]

Если хочешь, я могу следующим сообщением дать тебе **готовую последовательность команд для Ubuntu/Debian**, включая удаление старой очереди CUPS и ручное добавление принтера.
<span style="display:none">[^10][^11][^7][^8][^9]</span>

<div align="center">⁂</div>

[^1]: https://mcgrp.ru/files/viewer/162514/37

[^2]: https://forum.zorin.com/t/printer-xerox-phaser-3020-does-not-work/61535

[^3]: https://aur.archlinux.org/packages/xerox-phaser-3020

[^4]: https://aur.archlinux.org/cgit/aur.git/tree/.SRCINFO?h=xerox-phaser-3020

[^5]: https://openprinting.github.io/cups/

[^6]: https://www.linux.org.ru/forum/linux-hardware/18232959

[^7]: http://download.support.xerox.com/pub/docs/3020/userdocs/any-os/ru/Phaser_3020_UG_RU.pdf

[^8]: https://www.fotosklad.ru/upload/iblock/f00/f0087d7d6b8db968d772c868615df8b2.pdf

[^9]: https://ru.scribd.com/document/498574315/Drivers-Downloads-Phaser-3020-Linux-Xerox

[^10]: https://wiki.dno-it.ru/2024/10/08/drajvery-dlya-printerov-i-mfu-xerox-dlya-linux-mos/

[^11]: https://cs.wikiversity.org/wiki/Laserové_tisk%C3%A1rny/Kychot/Xerox_Phaser_3020

