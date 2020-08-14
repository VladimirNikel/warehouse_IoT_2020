# Администрирование складских помещений (ангара)

## Суть: 
> Имеется ангар, в нём произведено разделение на комнаты, в каждую комнату устанавливается конечное устройство с датчиками и lora-модулем. Со всех конечных устройств передаются данные собираемые с комнаты
![расположение устройств в ангаре](https://sun9-13.userapi.com/48xV6J1zNH9I4HNhDDLL26xvvNkn0E4JD6l_ng/NJ2jKLPE-U0.jpg)
![взаимодействие элементов между собой](https://sun9-64.userapi.com/HIFDK5W03gO3lhJ4O2pKFL6nfn3CzALq9XP3iQ/NHYcWcvG0ko.jpg)

## Инструкция по установке всего:
**1. Настройка среды разработки**

```
sudo apt install libusb-1.0-0-dev
sudo apt install cmake
sudo apt install gcc-arm-none-eabi
sudo apt install gtkterm
```

Далее переходим в любую удобную папку и выполняем следующую команду:

```
git clone https://github.com/unwireddevices/stm32flash
cd stm32flash
sudo make
sudo make install
```

**2. Основная работа**

* 2.1 Далее нужно скачать данный репозиторий.
* 2.2 Подключить плату UMDK-RF к компьютеру в режиме загрузчика (удерживать до подключения клавишу `boot/power`, после подключения отжать клавишу)
* 2.3 ...


**3. Взаимодействие с самим устройством**

* 3.1 Не подключая устройство к компьютеру наберите команду `ls /dev` в терминале - Вам отобразится список подключенных устройств. Пока его запоминать не надо.
Затем подключите устройство (базовую станцию) к компьютеру и снова выполните команду `ls /dev` и присмотритесь к устройствам с именем, начинающимся на _tty_ - чаще всего устройство будет иметь имя _ttyACM0_. Запомните имя подключенного устройства, оно пригодится вам позже.
* 3.2 Запускается gtkterm командой `sudo gtkterm`
* 3.3 В пункте `Configuration` выбирается `CR LF auto`
* 3.4 В пункте `Configuration` выбирается `Port` и производится настройка на прослушивание порта устройства (обычно: _ttyACM0_ - имя устройства из пункта 3.1) и выставляется скорость (_Baud Rate_) в значение `115 200`
* 3.5 При желании можно сохранить конфигурацию
* 3.6 При подключении устройства через порт USB будет отображена информация, поступающая с этого устройства. Также, через данное приложение можно посылать информацию на плату