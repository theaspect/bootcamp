# Конспект по электронике и Arduino
* Оглавление
{:toc}

# Начало работы
Всё необходимое я заказывал на AliExpress. Для начала будет очень полезным заказать
[StarterKit](https://ru.aliexpress.com/item/Free-shipping-RFID-learning-kit-upgraded-version-starter-kit-for-arduino/2044999580.html)
в комплекте идет Arduino Mega которая содержит огромное количество контактов, которых хватит на любой мыслимый проект и много памяти.
Немаловажным является совместимость со всеми операционными системами (об этом подробнее ниже).

[Магазин](https://www.seeedstudio.com) магазин специализирующийся на IoT.

# Почитать
* В комплекте идет электронная [книга c 32 проектами](http://wiki.keyestudio.com/index.php/Ks0077(78,_79)_keyestudio_Super_Learning_Kit_for_Arduino)
(желтая книжечка это просто листок со списком деталей). Не смотря на качество кода, который оставляет желать лучшего, всё работает.
Если что-то не заводится нужно просто проверить подключение.
Самым главным минусом является отстутствие пояснений к тому, почему это сделано именно так (подробности будут ниже).
Где-то с середины я уже старался писать код сам и экспериментировать.
Для реальных проектов я использовал заказанные детали, чтобы комплект деталей из кита остался полноценным.

* Пока шел кит, я купил себе книгу [Джереми Блум. Изучаем Arduino. Инструменты и методы технического волшебства](http://www.ozon.ru/context/detail/id/31350922/)
после которой некоторые вещи типа устранения дребезга кнопок, pull-up и pull-down резисторов для меня не были открытием.

* [10 Ways to Destroy An Arduino](https://www.rugged-circuits.com/10-ways-to-destroy-an-arduino/) крайне полезная статья про то что не стоит делать с arduino и почему. А еще всегда внимательно прислушивайтесь к запахам: если вовремя выдернуть питание, устройство может не пострадать. После отключения внимательно прощупайте на предмет источника запаха и высокой температуры – это может подсказать какой участок схемы собран неправильно.

* [Электроника для начинающих 2-е издание](https://www.ozon.ru/context/detail/id/8752090/)

# Контроллеры

[Более подробная таблица](https://www.arduino.cc/en/Products/Compare)

| Контроллер | Вольтаж | Пины | Схема | Комментарий |
|---|---|---|---|---|
| Arduino Mega <br/> [![Arduino Mega](https://store-cdn.arduino.cc/uni/catalog/product/cache/1/image/150x/f8876a31b63532bbba4e781c30024a0a/a/0/a000067_iso_.jpg)](https://store.arduino.cc/arduino-mega-2560-rev3) | 5v | 16A 54D | [![mega](http://www.pighixxx.com/test/wp-content/uploads/2014/11/mega-300x214.png)](http://www.pighixxx.com/test/portfolio-items/mega/?portfolioID=314)| Самый жирный из ардуин, проблем с подключением не было |
| Arduino Uno <br/> [![Arduino Uno](https://store-cdn.arduino.cc/uni/catalog/product/cache/1/image/150x/f8876a31b63532bbba4e781c30024a0a/a/0/a000066_front_1.jpg)](https://store.arduino.cc/arduino-uno-rev3) | 5v | 6A 14D | [![uno](http://www.pighixxx.com/test/wp-content/uploads/2014/11/uno-300x214.png)](http://www.pighixxx.com/test/portfolio-items/uno/?portfolioID=314)| Средний вариант, китайская версия требует драйвера |
| Arduino Nano <br/> [![Arduino Nano](https://store-cdn.arduino.cc/uni/catalog/product/cache/1/image/150x/f8876a31b63532bbba4e781c30024a0a/a/0/a000005_iso.jpg)](https://store.arduino.cc/arduino-nano) | 5v | 8A 22D | [![nano](http://www.pighixxx.com/test/wp-content/uploads/2014/11/nano-300x214.png)](http://www.pighixxx.com/test/portfolio-items/nano/?portfolioID=314)| Очень миниатюрный, китайская версия требует драйвера (linux работает и так) |
| ESP8266 ESP-01 <br/> [![esp-01](https://esp8266.ru/wp-content/images/esp8266-modules/thumbs/thumbs_ESP8266_ESP-01.jpg)](https://esp8266.ru/tag/esp-01/) | 3v3 |  | [![esp-01](http://www.pighixxx.com/test/wp-content/uploads/2015/09/ESP_Pinout_01_big-300x214.png)](http://www.pighixxx.com/test/portfolio-items/esp8266/?portfolioID=360) | Простейшая из варриаций ESP-8266, контроллер с WiFi, может понимать AT-команды, очень легко брикнуть, оживляется при помощи USB-TTL. Для прошивки необходимо знать размер флеш-памяти: если чип pn25f08 – это 1MB |
| micro:bit <br/> [![microbit](http://microbit.org/images/microbit-front.png)](http://microbit.org/) |  |  | [![microbit](http://www.pighixxx.com/test/wp-content/uploads/2017/02/microbit_pinout_v10-300x214.png)](http://www.pighixxx.com/test/portfolio-items/microbit/?portfolioID=360) | Детский контроллер, у китайцев нет, программируется как [scratch](https://makecode.com/). [пример1](http://tech.microbit.org/bluetooth/apps-and-examples/) [пример2](https://lancaster-university.github.io/microbit-docs/) |
| Circuit Playground Express <br/> [![cpe](https://cdn-shop.adafruit.com/145x109/3333-03.jpg)](https://www.adafruit.com/product/3333) |  |  | [![cpe](https://cdn-learn.adafruit.com/assets/assets/000/047/156/large1024/circuit_playground_Adafruit_Circuit_Playground_Express_Pinout.png?1507829017)](https://learn.adafruit.com/adafruit-circuit-playground-express/pinouts) | Детский контроллер, у китайцев нет, программируется как [scratch](https://makecode.com/) [https://github.com/adafruit/Adafruit_CircuitPlayground](C++ и Arduino)|
| Onion Omega2 <br/> [![omega2](https://onion.io/wp-content/uploads/2017/01/o2-45-top-600x600.png)](https://onion.io) |  | D15 | <img src="https://github.com/OnionIoT/Onion-Media/raw/master/Pinouts/Omega2.png" width=100> | SoC на базе Linux Embedded Development Environment (Open WRT), много разных [dock](https://onion.io/product-category/docks/) для подключения, в том числе Arduino |
| Adafruit M4 Express [![M4 Express](https://cdn-shop.adafruit.com/970x728/3382-06.jpg)](https://www.adafruit.com/product/3382) | | | | Контроллер от Adafruit в формфакторе Arduino |
| Sino:bit V1.0 [![Sino:bit](https://www.elecrow.com/media/catalog/product/cache/1/small_image/150x150/9df78eab33525d08d6e5fb8d27136e95/s/i/sinobit_smiling_face_2.jpg)](https://www.elecrow.com/sino-bit-v1-0.html) | | | | Китайская версия mirco:bit отличающаяся большим количеством светодиодов в матрице чтобы отображать иероглифы |

## Чипы

* [Atmel ATmega640/V-1280/V-1281/V-2560/V-2561/V](http://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-2549-8-bit-AVR-Microcontroller-ATmega640-1280-1281-2560-2561_datasheet.pdf)
* [ATmega328/P](http://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-42735-8-bit-AVR-Microcontroller-ATmega328-328P_Datasheet.pdf)

## Управление питанием
Подробный [разбор](http://www.gammon.com.au/power) различных режимов энергосбережения. В самом простом режиме SLEEP_MODE_IDLE чип проснется через 1 миллисекунду и его необходимо опять усыпить. Мои замеры представлены для Arduino Nano

| Метод | Потребляемый ток mA |
|---|---|
| Blink | 28.8 <-> 29.2 |
|---|---|
| Prescale | |
| 1 | 28.2 |
| 2 | 23.6 |
| 4 | 21.0 |
| 8 | 20.0 |
| 16 | 19.2 |
| 32 | 18.7 |
| 64 | 18.5 |
| 128 | 18.4 |
| 256 | 18.3 |
|---|---|
| all_disable() | 26.4 |
|---|---|
| power idle | 21.4-21.8 |
| power down + watchdog  | 14.8-15.0 |
|---|---|
| No regulator | 9.6 - 9.8 |

## Прерывания

Для экономии энергии и вычислительных ресурсов можно повесить прерывание на таймер или на [изменение](https://www.arduino.cc/reference/en/language/functions/external-interrupts/attachinterrupt/) сигнала на определенном пине. Отслеживается растущий, падающий, высокий, низкий и изменяющиеся сигналы. На один пин можно повесить только одно прерывание. Этот же механизм позволяет считывать длины сигналов через функцию [pulseIn](https://www.arduino.cc/reference/en/language/functions/advanced-io/pulsein/) для применения в PWM.

## Таймеры

Подробное [описание](http://www.gammon.com.au/timers) таймеров в чипах Atmega328 и то как выводить тактовые генераторы напрямую на пины.

## USB HID Human Input Device

Некоторые версии arduino имеют встроенную [поддержку](https://www.arduino.cc/en/Reference/HID) HID, т.е. при подключении к компьютеру они будут определяться как мышь, клавиатура или джойстик. Для версий которые не поддерживают HID можно спаять переходник из трёх резисторов и двух диодов зенера и использовать библиотеку [v-usb](https://www.obdev.at/products/vusb/index.html).

# Среды разработки

## Mongoose-os

Среда [разработки](https://mongoose-os.com), адаптированная для IoT и чипов ESP8266 и ESP32. Для прошивки необходимо в момент включения подключать GPIO-0 к GND. Обычный запуск работает и так, резисторы не нужны. <img src="http://2.bp.blogspot.com/-zjQRKTrXsDY/VhVl9FM1mxI/AAAAAAAAAB0/gvPSxU8LCgA/s640/ESP%2Bin%2Bflashing%2Bmode.jpg" width=200 />
[подробнее](https://github.com/jandelgado/NodeMCU/wiki/ESP8266-01-overview-and-flashing-instructions) [инструкция от espressif](https://github.com/espressif/esptool/wiki/ESP8266-Boot-Mode-Selection).  После прошивки пароль к AP будет Mongoose адрес http://192.168.4.1. ESP-01 доступно 1MB памяти, что очень ограничивает возможности Mongoose. В терминале нужно внимательно смотреть за логами, при ошибках скорее всег придется заливать прошивку заново.

## Atmel studio

Среда разработки на базе visual stuidio от [atmel](https://www.microchip.com/avr-support/atmel-studio-7).

## Avrdude

[Программа](http://savannah.nongnu.org/projects/avrdude) для прошивки чипов при помощи различных программаторов.

# Стандарты и Протоколы

## MQTT

Message Queuing Telemetry Transport. Отрытый протокол очереди сообщений, использующийся для IoT. Есть бесплатные брокер от [adafruit](io.adafruit.com).

## GPIO

General Purpose Input-Output цифровой порт ввода-вывода, служит для передачи сообщений между цифровыми устройствами.

## PWM

[Pulse width modulation](https://ru.wikipedia.org/wiki/%D0%A8%D0%B8%D1%80%D0%BE%D1%82%D0%BD%D0%BE-%D0%B8%D0%BC%D0%BF%D1%83%D0%BB%D1%8C%D1%81%D0%BD%D0%B0%D1%8F_%D0%BC%D0%BE%D0%B4%D1%83%D0%BB%D1%8F%D1%86%D0%B8%D1%8F) позволяет уменьшать эффективное напряжение на цифровых выходах [arduino](https://www.arduino.cc/en/Tutorial/PWM) [amperka](http://wiki.amperka.ru/%D0%BA%D0%BE%D0%BD%D1%81%D0%BF%D0%B5%D0%BA%D1%82-arduino:%D1%88%D0%B8%D0%BC?s[]=pwm)

## PFM

[Pulse frequency modulation](https://en.wikipedia.org/wiki/Pulse-frequency_modulation) альтернативный вид модуляции. Используется в преобразователях напряжения.

## Serial UART USART

[Universal asynchronous receiver-transmitter](https://ru.wikipedia.org/wiki/%D0%A3%D0%BD%D0%B8%D0%B2%D0%B5%D1%80%D1%81%D0%B0%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D0%B0%D1%81%D0%B8%D0%BD%D1%85%D1%80%D0%BE%D0%BD%D0%BD%D1%8B%D0%B9_%D0%BF%D1%80%D0%B8%D1%91%D0%BC%D0%BE%D0%BF%D0%B5%D1%80%D0%B5%D0%B4%D0%B0%D1%82%D1%87%D0%B8%D0%BA) вариант universal synchronous and asynchronous receiver-transmitter. Обычный последовательный порт для связи между устройствами. Обязательно необходимо согласовать скорость 300; 600; 1200; 2400; 4800; 9600; 19200; 38400; 57600; 115200; 230400; 460800; 921600. [arduino](https://www.arduino.cc/reference/en/language/functions/communication/serial/) Ардуино может иметь аппаратный порт, а может эмулировать. Во втором случае больших скоростей передачи данных не добиться. Можно купить usb-ttl uart adapter для прошивки устройств. 

## TTL
Transistor-transistor logic. Общее наименование подключения между транзисторами и микросхемами.

## SPI
[Serial Peripheral Interface](https://ru.wikipedia.org/wiki/Serial_Peripheral_Interface) шина для подключения устройств. Имеются [несколько](https://www.maximintegrated.com/en/app-notes/index.mvp/id/3947) вариантов подключения в простейшем на каждое устройство выделяется по 1 пину для адресации. [амперка](http://wiki.amperka.ru/js:spi) [arduino](https://www.arduino.cc/en/Reference/SPI)

## I2C
[Inter-Integrated Circuit](https://ru.wikipedia.org/wiki/I%C2%B2C) шина для подключения низкоскоростных устройств. 7-битная адресация позволяет подключить к шине до 127 устройств. [амперка](http://wiki.amperka.ru/js:i2c) [arduino](https://www.arduino.cc/en/Reference/Wire)

## I2S
[Inter-IC Sound](https://ru.wikipedia.org/wiki/I%C2%B2S) стандарт для подключения аудио-устройств. Не путать с I2C

## LP (LowPower), LoRa (Long Range), LoRaWAN (Высокоуровневый протокол управления доступом к среде, medium access control, MAC)
Стандарт связи для IoT, который за счет низкой скорости (0.3 kbit/s to 50 kbit/s) позволяет охватывать до 10км. [wiki](https://en.wikipedia.org/wiki/LPWAN). [LoRa](https://en.wikipedia.org/wiki/LoRa) проприетарный формат модуляции. Используются нелицензируемые частоты 169 MHz, 433 MHz, 868 MHz, 915 MHz в зависимости от страны. Для [России](http://mobilradio.ru/information/artikles/433-868mhz.htm) это 433MHz (до 10мВт) и 864-865/868,7-869,2 MHz (до 25мВт). Эти диапазоны хорошо проникают в условиях городской застройки. Длины волн 70 и 35см позволяют применять компактные антенны. 868 MHz используется для станционарных устройств.

Чипы стандарта LoRa: SX1276 (138 - 1020 MHz), SX1277 (138 - 1020 MHz), SX1277 (138 - 510 MHz).
RFM69 [другая модуляция](https://learn.adafruit.com/adafruit-rfm69hcw-and-rfm96-rfm95-rfm98-lora-packet-padio-breakouts/overview).
[aliexpress](https://ru.aliexpress.com/store/1795152). Универсальный модуль [433/470/868/915MHz RHF76-052 SX1276 LoRa Module with Ultra Long Distance](https://www.elecrow.com/433-470-868-915mhz-rhf76-052-sx1276-lora-module-with-ultra-long-distance.html)  для всех частот но стоит $13.

SX1276/77/78/79 <-> RFM95/96/97/98(W)

## Pull-up Pull-down

# Распиновка

## USB
<img src="https://cs8.pikabu.ru/post_img/2016/04/14/5/1460619313193062117.png" width="200" />

## 18650
<img src="http://img.bidorbuy.co.za/image/upload/user_images/822/432822/432822_140519083341_img_1013.jpg" width="100"/> анод у батарери выделен вдавленным кольцом. Максимальный ток 4.35v, заряжают до 4.2v теряя 15-20% емкости. При длительном хранении рекомендуется заряжать до 3.7v-3.8v что составляет 70%-80% заряда. Минимальное напряжение до переразряда 3.0v-2.7v, переразряд приводит к необратимым химическим процессам, с повышением внутреннего сопротивления. Схемы [защиты](http://electro-shema.ru/chertezhi/zashita-li-ion-ot-glubokogo-razryada.html) от переразряда. Маркировка ICR -  аккумулятор на основе кобальта, INR -  аккумулятор на основе никеля и марганца, IMR -  аккумулятор на основе марганца, IFR - железофосфатный, NCR - специфическая маркировка аккумуляторов Panasonic - аккумулятор на основе никеля и кобальта c оксидом алюминия в качестве изолятора. [маркировка даты выпуска](http://batterex.com.ua/index.php?route=journal2/blog/post&journal_blog_post_id=13).

## 5mm LED
Самый распространенный диод красного цвета, напряжение 1.85v-2.5v, ток 20mA. Короткая нога - (катод), длинная нога + (анод). Соответственно прямой ток от длинной ноги к короткой. [даташит](https://learn.adafruit.com/all-about-leds/the-led-datasheet). Рассчитать сопротивление резистора можно по формуле:  
R = (VS - VL) / I  
VS - напряжение источника питания (В).  
VL - напряжение питания светодиода (обычно 2 вольта и 4 вольта для голубых и белых светодиодов).  
I - ток светодиода (например 10 мА = 0.01 А или 20 мА = 0.02 А)  
Следовательно для 5v (5-2)/0.02 = 150 Ohm. Ближайший стандартный резистор 220 Ohm

# Сенсоры

## Датчик влажности резистивный
![Soil moisture sensor](http://wiki.keyestudio.com/images/5/51/7734.png) для меня настоящим открытием стал гальванический эффект.
Этот датчик растворяется в момент использования. Первый датчик я подключил напрямую к 5v и одна из ног полностью растворилась за неделю.
Второй датчик я подключил к цифровому пину и напряжение подаю только на момент измерения, держится пару тройку недель, но тоже растворяется – даже при цифровом 0 все равно подается ток 1mV. На цикл подать напряжение на пин, замерить, убрать напряжение с пина уходит 125uS. Предлагают по-очереди менять направление тока. Пробовал подключить через транзистор – не сильно помогло, коррозия съедает датчик сама по себе. Умельцы заменяют ноги на два графитовых карандаша [раз](https://usamodelkina.ru/9103-indikator-vlazhnosti-pochvy.html) либо покупают [графитовый](https://mysku.ru/blog/aliexpress/56072.html)
Я сразу заказал [пачку датчиков](https://ru.aliexpress.com/store/product/Soil-Moisture-Sensor/1950989_32532715392.html).

## Датчик влажности емкостный
<img src="https://images-na.ssl-images-amazon.com/images/I/61zUklVDaKL._SY355_.jpg" width=100/> используется переменный ток чтобы измерять влажность почвы без непосредственного контакта за счет изменения диэлектрической проницаемости почвы. [Стоит дороже](https://ru.aliexpress.com/wholesale?SearchText=+capacitive+soil+moisture+sensor) но должен быть менее подвержен коррозии. Самодельная [версия](http://gygrosensor.ucoz.ru/publ/sensor_80mhz/1-1-0-20) на базе 80Mhz [кварцевого генератора](https://ru.wikipedia.org/wiki/%D0%9A%D0%B2%D0%B0%D1%80%D1%86%D0%B5%D0%B2%D1%8B%D0%B9_%D0%B3%D0%B5%D0%BD%D0%B5%D1%80%D0%B0%D1%82%D0%BE%D1%80)

## Датчик дыма
![Gas sendor](http://wiki.keyestudio.com/images/0/01/7629.png) при работе нагревается

## Клапаны solenoid water valve
Переключается при помощи реле мгновенно, для подавление негативного эффекта, неоходимо использовать гаситель или компенсатор гидроудара (water hammer arrestor) либо медленно закрывающийся клапан anti-waterhammer valve. Редуктор давления тоже помогает. Как и реле бывает двух видов: normally open NO (для закрытия нужно подать ток) и normally close NC (для открытия нужно подать ток). Очень важно обратить внимание на диаметр резьбы: перед покупкой убедитесь, что в сантехнических магазинах есть необходимые адаптеры (в строительных выбор может быть очень ограничен). Соленоиды в клапанах не предназначены для длительной работы, поэтому необходимо либо отводить тепло, либо использовать короткие циклы работы.

# Индикаторы

## Дисплей на 4 цифры
![4x Dispaly](http://wiki.keyestudio.com/images/f/fe/7618.png) ![8x8 display](http://wiki.keyestudio.com/images/8/8f/7619.png)
неожиданным открытием для меня стало то, что в каждом разряде цифры отнюдь не запоминаются и нужно очень быстро
по-очереди включать каждый разряд. Поэтому sleep и низкое энергопотребление с такими индикаторами несовместимо. Для решения этой проблемы используются драйвера [7-сегментный дисплей на базе MAX6954](https://www.maximintegrated.com/en/app-notes/index.mvp/id/3210), [64-диодная матрица на базе MAX7221](https://www.maximintegrated.com/en/products/power/display-power-control/MAX7221.html)

## Текстовый дисплей
![lcd](http://wiki.keyestudio.com/images/9/95/7620.png) самые популярны LCD1602 и LCD2004.
Как и с батарейками название говорит само за себя: LCM1602 – 16 символов в 2 строки. Прямое подключние к ардуине потратит 16 пинов,
что для mega еще терпимо, то для nano вообще грустно. Да и подключение очень муторное и нечревато ошибками.
Поэтому не парьтесь и сразу закупайте сразу [I2C адаптер](https://ru.aliexpress.com/item/LCD-16x2-16x4-20x2-20x4-adaptor-to-I2C/32635555276.html),
а в дальнейшем лучше сразу покупать с припаянными модулями [1602](https://www.aliexpress.com/item/LCD1602-I2C-LCD-1602-module-Blue-screen-IIC-I2C-for-arduino-LCD1602-Adapter-plate/32707720115.html)
или [2004](https://www.aliexpress.com/item/IIC-I2C-TWI-Serial-LCD-2004-20x4-Display-Shield-Blue-Backlight-for-Arduino/32599904427.html).

<img src="http://4.bp.blogspot.com/_qiZ6auXA3gw/TUq5YqTk3GI/AAAAAAAAAsU/durFeJPXcJE/s1600/lcd.jpg" width=200> Отдельным вызовом является несколько стандартных распиновок у адаптера на базе pca8574 и пока вы не укажете правильную,
вы будете видеть на экране мусор и кракозябры, которые на самом деле китайские символы. Я убил огромное количество времени, пока не понял как его правильно подключать.
Самые распространенные конфигурации для [en,rw,rs,d4,d5,d6,d7,bl]: [2,1,0,4,5,6,7,3] и [4,5,6,0,1,2,3,7].
Для отображения данных использую библиотеку [NewLiquidCrystal](https://bitbucket.org/fmalpartida/new-liquidcrystal/wiki/Home).

# Детали

## Диод-зенера или стабилитрон

Применяется для ограничения напряжения в цепи. Включается обратно по сравнению с обычным диодом. [Описание](https://www.youtube.com/watch?v=djpfEyHTTI8).

## Диод шоттки

Основное отличие – низкое падение напряжение и высокая скорость переключения, но ценой более высокого обратного тока. [Описание](https://www.youtube.com/watch?v=bXEyCf1P0UU)

## Оптрон, опторэле, оптопара

Пара элементов состоящая из излучателя и датчика. Применяется для передачи сигналов, разделения высоковольтной части схемы и управляющей. [Вики](https://ru.wikipedia.org/wiki/%D0%9E%D0%BF%D1%82%D1%80%D0%BE%D0%BD)

## Конденсатор
[Объяснение](https://www.youtube.com/watch?v=WytU5uj78-4) зачем ставят электролитические и емкостные конденсаторы в параллель.

## Транзистор
Используется для управления током. Делятся на биполярные и полевые. [Амперка](http://wiki.amperka.ru/%D1%81%D1%85%D0%B5%D0%BC%D0%BE%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D0%BA%D0%B0:%D1%82%D1%80%D0%B0%D0%BD%D0%B7%D0%B8%D1%81%D1%82%D0%BE%D1%80%D1%8B)

В биполярных транзисторах выводы: База Base, Эмиттер Emitter, Коллектор Collector. В бп-транзисторах ток базы управляет током от эмиттера к коллектору. Делятся на pnp и npn транзисторы. NPN более эффективны и распространены в промышленности. PNP-транзисторы при обозначении отличаются направлением стрелки. Стрелка всегда указывает от P к N. PNP-транзисторы отличаются «перевёрнутым» поведением: ток не блокируется, когда база заземлена и блокируется, когда через неё идёт ток. PNP транзисторы открываются напряжением отрицательной полярности, NPN - положительной. PNP пропускают ток от эмиттера к коллектору, NPN - наоборот. В NPN транзисторах основные носители заряда - электроны, а в PNP - дырки, которые менее мобильны (мобильность - скорость переноса мощности), соответственно NPN транзисторы быстрее переключаются в общем случае.

В полевых транзисторах выводы: Сток Drain, Исток Source, Затвор Gate. В п-транзисторах напряжение затвора управляет током между истоком и стоком. Полевые транзисторы также называются МОП металл-оксид-полупроводник-транзисторами (MOS FET metal-oxide-semiconductor field-effect transistor). Изолированность затвора обуславливает высокую производительность и энергоэффективность такого типа транзисторов. Делятся на p-channel и n-channel.

<img src="https://i.stack.imgur.com/a0yBQ.jpg" width=200 /> N-channel подключается, в нижнем плече (low-side), а P-channel — в верхнем плече (high-side). [Подробнее](https://eax.me/mosfet-cheet-sheet/) При недостаточном напряжении могут быть большие энергопотери. Для управлением MOSFET ставят либо драйвер, либо через биполярный транзистор подключают к управляемому напряжению.

Выбор MOSFET для логического уровня: напряжение затвора должно быть Vgs=5v а не (Vgs=10v), Vds(max) и Ids(max) должны удовлетворять переключаемой нагрузке, сопротивление Rds(on) в Vgs=5v достаточно малое так чтобы рассеиваемая мощность I^2 * Rds(on) была достаточно малой, например >5W.

Биполярные низкочастотные pnp транзисторы: Vcbo BD343 -22V BD346 -32V BD348 -45V

## Операционный усилитель LM358
[Схема](http://hardelectronics.ru/lm358.html) включения. Описание [принципов](http://cxem.net/beginner/beginner96.php) усиления.

## IR-пульт
![IR](http://wiki.keyestudio.com/images/6/6b/7722.png) в комплект к пульту не входила батарейка типоразмера СК2025
и пришлось идти покупать отдельно. Что интересно, 20 – это диаметр в мм, а 25 – толщина в 2.5мм. Очень удобно запоминать.

## Рэле
![Relay](http://wiki.keyestudio.com/images/f/f0/7627.png) применяется для безопасного соединения двух разных линий питания,
там где транзистора не хватит. Поскольку соединение замыкается и размыкается физическим переключателем, то на голой релешке
в момент размыкания появится обратный ток, который может пожечь контакты на вашей ардуине. Ток этот утилизируют при помощи диода.
На модуле эти диоды _вроде как_ есть и можно подключать прямо так. Более мощная линия помимо земли содержит два контакта:
NO (normally open – разомкнуто) и NC (normally closed - замкнуто) важно не перепутать подключение,
иначе при выключенном контроллере то что подключено к рэле будет постоянно работать.

## DS3231 Часы реального времени
![realtime](http://wiki.keyestudio.com/images/c/cc/7732.png) прежде чем начать пользоваться, необходимо установить время.
Для простоты, если не требуется большая точность, можно взять время компиляции при помощи макросов
[__DATE__ и __TIME__](http://www.l8ter.com/?p=417) и распарсить их. После этого можно залить основную прошивку.
Шедшие с kit часы не запоминали время, возможно я не полностью вытащил перемычку под батарейкой.
Для работы с часами через i2c используется [библиотека](https://github.com/rodan/ds3231). Аккуратный модуль у
[RobotDyn](https://ru.aliexpress.com/item/RTC-Real-Time-Clock-DS1307-module-with-battery/32530897478.html).

По протоколу I2C работают DS1307, PCF8563 или DS3231, у DS1302 самопальный протокол поэтому придется задействовать дополнительны пины.

## 9g servo
![servo](http://wiki.keyestudio.com/images/3/31/7723.png) При установке угла в 180? **TODO** серво-привод начинал непрерывно вращаться

## CMOS Камера OV7670 (может быть с AL433 FIFO)

<img src="http://wp.sps.esy.es/wp-content/uploads/2016/04/HMC3_bufnal.jpg" width=200 />

Не пытался подключить. Есть книга на 200 страниц
[Beginning Arduino ov7670 Camera Development](https://www.amazon.com/Beginning-Arduino-ov7670-Camera-Development/dp/1512357987).
При этом есть две версии с Framebuffer и без, та которая с буфером помечена как FIFO и стоит в несколько раз дороже.
Отличительной особенностью является микросхема Averlogic AL4228-PBF, которая упрощает работу. Поток данных быстро сохраняется в буфер, потом можно медленно считать. Описание [подключения](http://wp.sps.esy.es/spselectro/%D1%81%D0%B0%D0%BC%D0%BE%D0%B4%D0%B5%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F-%D0%BA%D0%B0%D0%BC%D0%B5%D1%80%D0%B0-%D1%87%D0%B0%D1%81%D1%82%D1%8C-3-%D0%BC%D0%BE%D0%B4%D1%83%D0%BB%D1%8C-%D0%B2%D0%B8/) к arduino mini без буфера. Еще одно [описание](http://www.instructables.com/id/OV7670-Without-FIFO-Very-Simple-Framecapture-With-/).

## Ультразвуковой сенсор HC-SR04

<img src="https://cdn.sparkfun.com//assets/parts/1/1/6/6/8/13959-01a.jpg" width=200 />

Работает на расстоянии 2-400cm. Управляется 4 пинами VCC, GND, Trig, Echo. [Библиотека](https://playground.arduino.cc/Code/NewPing)

## Мультиплексор (MUX) CD74HC4067

<img src="https://www.elecrow.com/media/catalog/product/cache/1/image/9df78eab33525d08d6e5fb8d27136e95/1/4/14393620000_1.jpg" width=200 />

[Вики](https://ru.wikipedia.org/wiki/%D0%9C%D1%83%D0%BB%D1%8C%D1%82%D0%B8%D0%BF%D0%BB%D0%B5%D0%BA%D1%81%D0%BE%D1%80_(%D1%8D%D0%BB%D0%B5%D0%BA%D1%82%D1%80%D0%BE%D0%BD%D0%B8%D0%BA%D0%B0)

Позволяет 5 пинами (4 цифровой для выбора устройства и 1 АЦП для передачи данных) управлять 16-ю устройствами.

# Модули

## RC-контур Resistor + Capacitor

Используется для фильтрации переменного тока. Подробная [статья](http://easyelectronics.ru/kondensator-i-rc-cepochka.html). [Low-pass filter](https://ru.wikipedia.org/wiki/%D0%A4%D0%B8%D0%BB%D1%8C%D1%82%D1%80_%D0%BD%D0%B8%D0%B6%D0%BD%D0%B8%D1%85_%D1%87%D0%B0%D1%81%D1%82%D0%BE%D1%82) фильтр нижних частот, отсекает все частоты ниже среза, аналогично [high-pass filter](https://ru.wikipedia.org/wiki/%D0%A4%D0%B8%D0%BB%D1%8C%D1%82%D1%80_%D0%B2%D0%B5%D1%80%D1%85%D0%BD%D0%B8%D1%85_%D1%87%D0%B0%D1%81%D1%82%D0%BE%D1%82) отсекает частоты выше среза.

## LC
** TODO **
## LR
** TODO **

## Tristate buffer

В схемотехнике третье состояние в дополнение к логическому 0 и 1 – высокоимпедансное. Не путать с тернарной логикой. Позволяет убирать весь выход с элемента, чтобы защитить общую шину. Для того чтобы убрать помехи и шум используются pull-up и pull-down резисторы. [wiki](https://en.wikipedia.org/wiki/Three-state_logic)

## Контроллер зарядки одной ячейки аккмулятора FC-57 на базе ТР4056
<img src="https://universal-solder.com/wp-content/uploads/2017/10/tp4056_4.jpg" width=200 />

Даташит [ТР4056](http://cds.linear.com/docs/en/datasheet/405642f.pdf) [Описание](http://we.easyelectronics.ru/part/zaryadnoe-ustroystvo-dlya-li-ion--na-tr4056.html), [пример](http://www.instructables.com/id/SOLAR-POWERED-ARDUINO-WEATHER-STATION/) использования с солнечной батареей. [Комментарии](https://forum.arduino.cc/index.php?topic=405875.0) по поводу одновременной зарядки нескольких ячеек. Заряжает постоянным током, посепенно повышая напряжение до 4.2v, по достижению 4.2v постепенно понижает ток до наступления отсечки, где-то на 4.18v. Такой профиль заряда называется CC/CV (constant current, constant voltage). Альтернативные [контроллеры](http://electro-shema.ru/chertezhi/zaryadka-dlya-li-ion-akkumulyatorov.html). Больше информации про [контроллеры](https://eax.me/diy-solar-powerbank/) заряда. Обратите внимание, что есть [контроллеры](https://www.amazon.com/gp/product/B00QGVP944/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B00QGVP944&linkCode=as2&tag=opegreene-20&linkId=V2KV7AHSF566NFLP) с защитой от разряда (overcharge-discharge/surge protection) в этом случае будет 4 выходных контакта пара на аккумулятор и пара на нагрузку. В идеале на кажду ячейку нужен свой регулятор.

## Повышающий конвертер на базе [mt3608](http://prom-electric.ru/media/MT3608.pdf)
В поиске DC-DC step-up Boost Converter. На самой микросхеме преобразователя маркировка F16S. Работает в паре с контроллером заряда. [Али](https://ru.aliexpress.com/item/Free-Shipping-DC-3V-to-5V-USB-Output-charger-step-up-Power-Module-Mini-DC-DC/1610373693.html?ws_ab_test=searchweb0_0,searchweb201602_2_10152_10151_10065_10344_10068_10342_10343_10340_10341_10543_10696_10084_10083_10618_10307_10301_5711215_10313_10059_10534_100031_10103_10627_10626_10624_10623_10622_5711315_10621_10620_5722415_10125,searchweb201603_2,ppcSwitch_7&algo_expid=52ec73d4-780c-4dc1-8b03-0249d0b698f5-6&algo_pvid=52ec73d4-780c-4dc1-8b03-0249d0b698f5&priceBeautifyAB=0)
Вариантов очень много. Для удобства можно отрезать USB порт и подпаяться напрямую к крайним пинам. Принцип работы – LC цепь, при помощи транзистора с обратной связью в [LC-контуре](https://ru.wikipedia.org/wiki/%D0%9A%D0%BE%D0%BB%D0%B5%D0%B1%D0%B0%D1%82%D0%B5%D0%BB%D1%8C%D0%BD%D1%8B%D0%B9_%D0%BA%D0%BE%D0%BD%D1%82%D1%83%D1%80) идет накачка конденсатора катушкой индуктивности. Если нужно повысить напряжение – повышается частота, на катушке появляется большее напряжение, если наоборот нужно уменьшить, то частота понижается, соотвветственно уменьшается напряжение на катушке. По сути PFM. [Принцип работы](https://www.youtube.com/watch?v=FRG01YOEQGY)

## Стабилизатор напряжения (понижающий) Voltage Regulator на базе транзисторов [L78XX](http://datasheet.octopart.com/L7805CV-STMicroelectronics-datasheet-7264666.pdf) или Linear Power Regulator

В маркировке XX это целевое напряжение, например L7805CV. Принцип работы PWM. В простейшем подключении лишнее напряжение рассеивается в виде тепла, поэтому транзиторам может понадобиться радиатор (heat sink). В даташите представлено большое количество схем подключения для разных видов регуляции. Одной из зарактеристик является падение напряжния, т.е. минимальная разница напряжений на входе и выходе. Например если падение 2V для 5v стабилизатора, то при подаче 5 вольт, напряжение на выходе упадет на 2 вольта. Часто в схему включают два конденсатора: электролитический большой емкости и 1-2 керамических меньшей. Электролитический – более дешевый и запасает большую емкость, а керамический позволяет фильтровать высокие частоты, с которыми не справляется электролитический. [Принцип работы](https://www.youtube.com/watch?v=GSzVs7_aW-Y). На тех же принципах строятся линейные [регулируемые](https://eax.me/diy-power-supply/) источники тока Power Supply.

## Импульсные регуляторы тока Switched-mode power supply [LM2678](http://www.ti.com/lit/ds/symlink/lm2678.pdf)

Более энергоэффективные на больших разницах напряжения, чем линейные регуляторы просто рассеивающие излишнюю мощность. [Принцип](https://www.youtube.com/watch?v=CEhBN5_fO5o) работы. Очень много подвидов: buck, boost, buck-boost, cuk, charge pump и др. Используется для защиты транзистора используется диод-шоттки.

## Регулятор напряжения на базе MP1584
<img src="https://i.ebayimg.com/images/g/NeEAAOSwJ7RYYk5w/s-l300.jpg" width=200 /> 4.5-28V на вход и 1.8-26V на выход. Может быть фиксированный либо регулируемый при помощи потенциометра

## Драйвер для двигателей [TB6612FNG](https://www.sparkfun.com/datasheets/Robotics/TB6612FNG.pdf)
<img src="https://camo.githubusercontent.com/80ad6f9f1a855da5c081bfeeb105beaf0ac08e04/68747470733a2f2f63646e2e737061726b66756e2e636f6d2f2f6173736574732f70617274732f332f312f352f372f30393435372d3031622e6a7067" width=200 />

[Библиотека](https://github.com/sparkfun/SparkFun_TB6612FNG_Arduino_Library) [подключение](https://learn.sparkfun.com/tutorials/tb6612fng-hookup-guide) позволяет управлять двумя двигателями током до 1.2А. Вращая двигатели раздельно CW (ClockWise) и CCW (CounterClockWise), тормозя и останавливая. На всё 7 пинов. [Вики](http://wiki.sunfounder.cc/index.php?title=TB6612_DC_Motor_Driver_Module) с библиотекой.

## Драйвер для двигателей [L298](https://www.theengineeringprojects.com/2017/07/introduction-to-l298.html)

<img src="https://www.theengineeringprojects.com/wp-content/uploads/2017/07/L298-Pinout.jpg" width=200 />

## Драйвер для двигателей LV8406T

[Сравнение с предыдущими драйверами](https://forum.makeblock.com/t/the-review-of-dc-motor-drivers-l298n-tb6612fng-and-lv8406t/372/5)

## Блок питания AC-DC transformer, AC Adapter, Rectifier
 
Преобразование идет в несколько этапов: сначала катушками индуктивности напряжение понижается до необходимого, затем через диодный мост выпрямляется, после этого сглаживается при помощи конденсаторов. [Принцип работы](https://www.youtube.com/watch?v=VZctTmmS-gA)

## Инвертор Invertor DC-AC 
4 транзистора и два сумматоров генерируют положительную и отрицательную часть синусоиы [Принцип работы](https://www.youtube.com/watch?v=qVeERT4nyz8)

## Программатор на базе CH340
Китайский UART встроенный в дешевые arduino, требует установки [драйверов](https://kig.re/2014/12/31/how-to-use-arduino-nano-mini-pro-with-CH340G-on-mac-osx-yosemite.html). Смотри FT232RL.

## Программатор на базе чипа FT232RL от компании FTDI. USB To TTL Serial, UART (Universal Asynchronous Receiver-Transmitter)

<img src="https://ae01.alicdn.com/kf/HTB1JWLumbYI8KJjy0Faq6zAiVXaF/Basic-Breakout-Board-For-FTDI-FT232RL-USB-To-TTL-Serial-IC-Adapter-Converter-Module-For-Arduino.jpg" width=200 />
Многие чипы работают на 3.3v логике, прошить через Arduino может не получиться из-за того что необходимо понижать TX линию от arduino. Залить прошивку у меня через arduino так и не получилось, поскольку брикнуть ESP-01 очень легко, вам обязательно понадобится это устройство. На таких программаторах часто есть переключатель 5v-3.3v. Обратите внимание на разъем: может приехать mini USB.

При помощи этого устройства можно программировать чипы на базе CH340, можно собирать специальную схему, но для ручной прошивки достаточно подключить VCC -> VCC, GND -> GND, TX -> RX, RX -> TX. В Arduino IDE выбрать Programmer ArduinoISP, нажать на RST, в Arduino IDE нажать Upload. Как только появится надпись UploTM1637ading тут же отпустить RST. Более сложная версия подключается через конденсатор DTR-RST, эта версия позволяет автоматически сбрасывать и прошивать.

## Драйвер 7-сегментных дисплеев TM1637 (digital tube)

<img src="https://img.staticbg.com/thumb/view/oaupload/banggood/images/6D/80/b92e22f3-1046-448a-93d4-13378c114add.jpg" width=200 />

7-сегментные дисплеи это 8 без точки. [Описание](https://playground.arduino.cc/Main/TM1637). Управляется при помощи 4 пинов CLC, DIO, VCC, GND. [Библиотека](https://github.com/avishorp/TM1637)

## Драйвер для матриц 16х24 [HT1632C](https://www.adafruit.com/product/555)

<img src="https://cdn-shop.adafruit.com/970x728/555-00.jpg" width=200>

Работает по интерфейсу SPI и позволяется объединать в цепочку до 8 панелей

# Serial bluetooth BK3231
Описание AT [команд](https://forum.allaboutcircuits.com/threads/unknown-bluetooth-module-with-bk3231-chip.123933/)

# Прототипные/макетные платы (prototype breadboard)

## Текстолитовые

<img src="https://img.banggood.com/images/oaupload/banggood/images/40/86/ef082e74-2d84-414e-9fc7-59ae7c5f7c49.jpg" width=200 /> без дорожек
<img src="https://ae01.alicdn.com/kf/HTB1UbBnLpXXXXXgaXXXq6xXFXXXD/5-pcs-lot-universal-Stripboard-Veroboard-Seul-C-t-7x5-cm.jpg_640x640.jpg" width=200 /> и с дорожками
выполняются в множестве размеров

## Беспаеная макетка No solder
<img src="https://cdn.sparkfun.com/assets/3/d/f/a/9/518c0b34ce395fea62000002.jpg" width=200 /> Поставляются вместе с ардуиновскими наборами, стыкуются друг с другом. 

# Провода и Коннекторы

## AWG (American Wire Gauge)

Американский стандарт диаметров проводов [таблица](https://www.icsgroup.ru/library/consult/detail.php?ID=9329). Еще один документ описывающий провода 10 стандартных цветов [ul1007/ul1569](http://www.elandcables.com/electrical-cable-and-accessories/cables-by-standard/ul1007-cable-and-wire). В качестве перемычек на борде удобно использовать одножильные AWG22 (0.643mm/0.325mm2) и AWG24 (0.511mm/0.205mm2). Подойдет также КСПВ 4x0.64 Alarm Security Cable Paritet кабель для системы передач с оболочкой из винила.

## Rainbow ribbon wire
<img src="http://www.electroncomponents.com/image/cache/data/misc/EC_10Wire_Riboon_Cable-500x500.jpg" width=200/> 
<img src="http://thumb1.zeppy.io/d/l400/pict/192363894610/40-pcs-dupont-cables-m-f-m-m-f-f-jumper-breadboard-wire-gpio-ribbon-pi-arduino" width=200/>
Пучок из 20 проводов 10 цветов. Может продаваться либо мотком, либо нарезанным и обжатым коннекторами dupont длиной 10 или 20см. В комплекте коннекторы разных видов М-М М-П П-П.

## Гребенки, цанговое гнездо штыревое Pin headers
Бывают круглы и квадратные для распайки на плате, идут комплектами по 40-пинов
<img src="https://i.stack.imgur.com/lXhyd.jpg" width=200>
<img src="https://i.stack.imgur.com/QpxI7.jpg" width=200>

## Dupont
<img src="https://ae01.alicdn.com/kf/HTB1jRtPQXXXXXaDXXXXq6xXFXXXq/670pcs-set-2-54mm-Jumper-Wire-Cable-Pin-Header-Dupont-Connector-Dupont-Plastic-Shell-Plug-Dupont.jpg_640x640.jpg" width=200> <img src="https://www.bluetin.io/wp-content/uploads/2017/07/sn-28b-dupont-terminal-crimping-tool-kit.jpg" width=200 />
Коннекторы которые идут с Arduino в виде цветных проводов, как раз относятся к этому стандарту. Можно купить отдельно цветной жгут и отдельно коннекторы. Обжимаются специальным инструментом Crimper Tool с характерным M-образным профилем. Можно обжать пассатижами, но будет менее аккуратно. Разъемы группируются от 1 до 10, мама, папа и папа для распайки на плате. Коннекторы не фиксируются.

## XH2P Pitch terminal, JST Connectors

<img src="http://i.imgur.com/6mTsil8l.png" width=200 />
<img src="https://ae01.alicdn.com/kf/HTB1F4PkOpXXXXcIXFXXq6xXFXXXo/40-Sets-Kit-in-box-XH2-54-Right-Angle-2p-3p-4p-5pin-2-54mm-Pitch.jpg_640x640.jpg" width=200 />

Коннекторы с защелками, могут быть очень тугими. Для обжимки используется crimping tool, можно обжать пассатижами. Идут комлпектами от 2 до 5 пинов. Вики [перечисление](https://en.wikipedia.org/wiki/JST_connector) всех серий.

## 9V Clip Barrel Male
<img src="https://i.ebayimg.com/images/g/N9oAAOSw5cNYUl~f/s-l300.jpg" width=200 />
Адаптер для батарей вида PP3 (крона) в   5.5 мм x 2.1 мм

## Сокет, слот, 80 зшт 1.27mm Pitch Right Angle Card Edge Connector, cartridge slot

<img src="https://www.toby.co.uk/uploads/images/large/2867.jpg" width=200 />
Специальный разъем для подсоединения целой платы. Отличаются шагом разъема 1.27mm/0.05in и количеством пинов. Пины могут быть выведены одинково с двух сторон.

[Магазин](https://www.toby.co.uk/board-to-board-pcb-connectors/card-edge-connetors/vec-valcon-127mm-pitch-right-angle-card-edge-connector/)

# Инструменты

## Бокорезы
<img src="https://ae01.alicdn.com/kf/HTB1zivrawmTBuNjy1Xbq6yMrVXaT/DIYFIX-4-7-Mini-Electronic-Pliers-Diagonal-Side-Cutting-Pliers-Cable-Wire-Cutter-Repair-Pry-Open.jpg_640x640q90.jpg" width=200 /> Бокорезы (Diagonal Side Cutter Plier) для откусывания торчащих кончиков

## Инструмент для снятия изоляции. Wire Stripper

<img src="https://images-na.ssl-images-amazon.com/images/I/612qEV3k57L._SL1500_.jpg" width=200 />
<img src="https://system.zoco.cl/upload/93408801/template/fernapet1/114359314615690100615512435501327993535.jpg" width=200 />

Бывает двух основных видов: простые клещи с пазами для соответствующих диаметров, простой общимкой и болторезом. Зажали и дернули. Не очень удобно для маленьких проводов. И автоматическая которая аккуратно снимает изоляцию без необходимости дергать или тянуть. Может быть регулируемый упорт чтобы снимать изоляцию нужного размера. Так же позволяет снять изоляцию в середине кабеля.

## Мультиметр
<img src="http://s-line.ru/upload/iblock/f77/f77188faacdc034b2fd0f2939ba4af1d.jpg" width=200 />
Необходимы инструмент для измерения тока, напряжения, сопротивления. В комлекте идут щупы иголкой. Дополнительно можно приобрести щупы с крючком для проводов и крокодильчатые для более удобного измерения. hFE - измерение показателей транзисторов в 8-гнездовом разъеме current gain or amplification factor of a transistor при токе базы 10uA и Vce 2.8v. ->|- показывает падение напряжения на диоде. Прозвонка если сопротивление <20-30 Ohm вы услышите звук. Квадратная синусоида – сигнал 50hz 5v 50kOhm сопротивления между V и Com.

# Роботы

## Лента для перемещения Popbelt S2M-6mm toothed timing belt
<img src="https://statics3.seeedstudio.com/product/114990161%201_02.jpg" width=200 />

# Пайка

[Инструкция](https://learn.sparkfun.com/tutorials/how-to-solder-through-hole-soldering) от SparkFun

## Паяльные принадлежности (soldering iron)
<img src="https://rukminim1.flixcart.com/image/832/832/j44h7680/soldering-iron/h/b/z/complete-kit-of-60w-soldering-iron-with-adjustable-temp-5x-bits-original-imaev2ptr9wzbs5f.jpeg?q=70" width=200 /> На Aliexpress огромное количество паяльников, в том числе регулируемых (adjustable) по температуре 200-450 C.

С паяльником в комплекте могут идти сменные жала (soldering iron heads). Моей ошибкой было поставить самое тонкое в итоге паять было неудобно, поставил потолще.

<img src="https://ae01.alicdn.com/kf/HTB1dvX2oCYH8KJjSspdq6ARgVXag/Useful-Solid-Metal-Base-Soldering-Iron-Bracket-Stand-Holder-Support-Station-Frame-Portable-for-Electrical-Working.jpg_640x640.jpg" width=200 /> К паяльнику обязательно нужна стойка (soldering iron frame/stand/holder). Есть компактные циркониевые стойки <img src="https://images-na.ssl-images-amazon.com/images/I/41sZ0vNvdUL._SY463_.jpg" width=200 />

<img src="https://ae01.alicdn.com/kf/HTB1j3M1Xi0TMKJjSZFNq6y_1FXaB/FEITA-10pcs-pack-High-quality-599-029-Soldering-Iron-Tip-Cleaner-Cleaning-Wire-Sponge-Balls-for.jpg_640x640.jpg" width=200 />
Для очистки жала (solder tip cleaners) используется либо целлюлозная губка (sponge), которая используется в намоченном состоянии, либо медная стружка (steel wire). Нсли не очищать жало, то сгоревший флюс будет ухудшать качество пайки.

<img src="https://statics3.seeedstudio.com/product/Desoldering%20Wick_01.jpg" width=200 /> Для впитывания олова используется desoldering wire.

<img src="https://c.76.my/Malaysia/1set-hand-soldering-iron-stand-helping-magnifying-tool-small-chewhoung-1109-11-chewhoung@1.jpg" width=200 /> Третья рука (Helping Third Hand Clip Tool Soldering Stand), много разных видов, в том числе в 2 и 4 крокодилами, гибкие и жесткие. Используется, для удержания платы при пайке.

Пинцет с очень тонким кончиком (Anti-static Curved/Straight-Tip Forceps/Tweezers), для пайки очень мелких (например smd) деталей.

## Флюсы
Для удобства можно использовать канифоль, растворенную в спирте. Пузырек содержит кисточку.

Флюсы для пайки аллюминия можно использовать только в проветриваемом помещении.

Активные флюсы обязательно необходимо смывать иначе кислота разъест место пайки.

[1](http://elwo.ru/publ/instrumenty_radioljubitelja/vidy_fljusov/25-1-0-278)
[2](http://elektronika-muk.ru/konspekt/vidy-pripoja-i-fljusa.html)
[3](http://photonik.ru/index.php/optika/127-spravochnaya-elektronshchika-samodelshchika/285-obzor-khimii-dlya-pajki)
[4](http://cxem.net/master/105.php)

## Смывка флюса

Изопропиловый спирт продается в радиотехнических магазинах

## Изоляция
Самый простой и дешевый изолятор – цапон-лак. Растворяется ацетоном.

<img src="http://gafferstapesolutions.com/wp-content/uploads/2015/11/Non-Reflective-Gaffer-Tape-e1446964479805.jpg" width=200 />
gaffer tape или армированный скотч на тряпичной основе

electrical/insulating tape обычная изолента, [цвета](https://en.wikipedia.org/wiki/Electrical_tape) используются для кодирования проводов.

## Термостойкий коврик, Heat Insulation Silicone Pad Desk Mat
<img src="https://img.fasttechcdn.com/745/7455700/7455700-2.jpg" width=200 />
