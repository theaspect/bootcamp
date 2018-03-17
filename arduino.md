# Конспект по электронике и Arduino
* Оглавление
{:toc}

# Начало работы
Всё необходимое я заказывал на AliExpress. Для начала будет очень полезным заказать
[https://ru.aliexpress.com/item/Free-shipping-RFID-learning-kit-upgraded-version-starter-kit-for-arduino/2044999580.html](StarterKit)
в комплекте идет Arduino Mega которая содержит огромное количество контактов, которых хватит на любой мыслимый проект и много памяти.
Немаловажным является совместимость со всеми операционными системами (об этом подробнее ниже).

# Почитать
* В комплекте идет электронная [книга c 32 проектами](http://wiki.keyestudio.com/index.php/Ks0077(78,_79)_keyestudio_ARDUINO_Super_Learning_Kit)
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

| Контроллер | Вольтаж | Пины | Схема | Комментарий |
|---|---|---|---|---|
| Arduino Mega <br/> [![Arduino Mega](https://store-cdn.arduino.cc/uni/catalog/product/cache/1/image/150x/f8876a31b63532bbba4e781c30024a0a/a/0/a000067_iso_.jpg)](https://store.arduino.cc/arduino-mega-2560-rev3) | 5v | 16A 54D | [![mega](http://www.pighixxx.com/test/wp-content/uploads/2014/11/mega-300x214.png)](http://www.pighixxx.com/test/portfolio-items/mega/?portfolioID=314)| Самый жирный из ардуин, проблем с подключением не было |
| Arduino Uno <br/> [![Arduino Uno](https://store-cdn.arduino.cc/uni/catalog/product/cache/1/image/150x/f8876a31b63532bbba4e781c30024a0a/a/0/a000066_front_1.jpg)](https://store.arduino.cc/arduino-uno-rev3) | 5v | 6A 14D | [![uno](http://www.pighixxx.com/test/wp-content/uploads/2014/11/uno-300x214.png)](http://www.pighixxx.com/test/portfolio-items/uno/?portfolioID=314)| Средний вариант, китайская версия требует драйвера |
| Arduino Nano <br/> [![Arduino Nano](https://store-cdn.arduino.cc/uni/catalog/product/cache/1/image/150x/f8876a31b63532bbba4e781c30024a0a/a/0/a000005_iso.jpg)](https://store.arduino.cc/arduino-nano) | 5v | 8A 22D | [![nano](http://www.pighixxx.com/test/wp-content/uploads/2014/11/nano-300x214.png)](http://www.pighixxx.com/test/portfolio-items/nano/?portfolioID=314)| Очень миниатюрный, китайская версия требует драйвера (linux работает и так) |
| ESP8266 ESP-01 <br/> [![esp-01](https://esp8266.ru/wp-content/images/esp8266-modules/thumbs/thumbs_ESP8266_ESP-01.jpg)](https://esp8266.ru/tag/esp-01/) | 3v3 |  | [![esp-01](http://www.pighixxx.com/test/wp-content/uploads/2015/09/ESP_Pinout_01_big-300x214.png)](http://www.pighixxx.com/test/portfolio-items/esp8266/?portfolioID=360) | Простейшая из варриаций ESP-8266, контроллер с WiFi, может понимать AT-команды, очень легко брикнуть, оживляется при помощи USB-TTL |
| micro:bit <br/> [![microbit](http://microbit.org/images/microbit-front.png)](http://microbit.org/) |  |  | [![microbit](http://www.pighixxx.com/test/wp-content/uploads/2017/02/microbit_pinout_v10-300x214.png)](http://www.pighixxx.com/test/portfolio-items/microbit/?portfolioID=360) | Детский контроллер, у китайцев нет, программируется как [scratch](https://makecode.com/) |
| Circuit Playground Express <br/> [![cpe](https://cdn-shop.adafruit.com/145x109/3333-03.jpg)](https://www.adafruit.com/product/3333) |  |  | [![cpe](https://cdn-learn.adafruit.com/assets/assets/000/047/156/large1024/circuit_playground_Adafruit_Circuit_Playground_Express_Pinout.png?1507829017)](https://learn.adafruit.com/adafruit-circuit-playground-express/pinouts) | Детский контроллер, у китайцев нет, программируется как [scratch](https://makecode.com/) |
| Onion Omega2 <br/> [![omega2](https://onion.io/wp-content/uploads/2017/01/o2-45-top-600x600.png)](https://onion.io) |  | D15 | <img src="https://github.com/OnionIoT/Onion-Media/raw/master/Pinouts/Omega2.png" width=100> | SoC на базе линукса, много разных [dock](https://onion.io/product-category/docks/) для подключения, в том числе Arduino |

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

# Стандарты и Протоколы

## GPIO

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
по-очереди включать каждый разряд. Поэтому sleep и низкое энергопотребление с такими индикаторами несовместимо.

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

## Транзистор
Используется для управления током. Делятся на биполярные и полевые. [Амперка](http://wiki.amperka.ru/%D1%81%D1%85%D0%B5%D0%BC%D0%BE%D1%82%D0%B5%D1%85%D0%BD%D0%B8%D0%BA%D0%B0:%D1%82%D1%80%D0%B0%D0%BD%D0%B7%D0%B8%D1%81%D1%82%D0%BE%D1%80%D1%8B)

В биполярных транзисторах выводы: База Base, Эмиттер Emitter, Коллектор Collector. В бп-транзисторах ток базы управляет током от эмиттера к коллектору. Делятся на pnp и npn транзисторы. NPN более эффективны и распространены в промышленности. PNP-транзисторы при обозначении отличаются направлением стрелки. Стрелка всегда указывает от P к N. PNP-транзисторы отличаются «перевёрнутым» поведением: ток не блокируется, когда база заземлена и блокируется, когда через неё идёт ток. PNP транзисторы открываются напряжением отрицательной полярности, NPN - положительной. PNP пропускают ток от эмиттера к коллектору, NPN - наоборот. В NPN транзисторах основные носители заряда - электроны, а в PNP - дырки, которые менее мобильны (мобильность - скорость переноса мощности), соответственно NPN транзисторы быстрее переключаются в общем случае.

В полевых транзисторах выводы: Сток Drain, Исток Source, Затвор Gate. В п-транзисторах напряжение затвора управляет током между истоком и стоком. Полевые транзисторы также называются МОП металл-оксид-полупроводник-транзисторами (MOS FET metal-oxide-semiconductor field-effect transistor). Изолированность затвора обуславливает высокую производительность и энергоэффективность такого типа транзисторов. Делятся на p-channel и n-channel.

<img src="https://i.stack.imgur.com/a0yBQ.jpg" /> N-channel подключается, в нижнем плече (low-side), а P-channel — в верхнем плече (high-side). [Подробнее](https://eax.me/mosfet-cheet-sheet/) При недостаточном напряжении могут быть большие энергопотери. Для управлением MOSFET ставят либо драйвер, либо через биполярный транзистор подключают к управляемому напряжению.

Выбор MOSFET для логического уровня: напряжение затвора должно быть Vgs=5v а не (Vgs=10v), Vds(max) и Ids(max) должны удовлетворять переключаемой нагрузке, сопротивление Rds(on) в Vgs=5v достаточно малое так чтобы рассеиваемая мощность I^2 * Rds(on) была достаточно малой, например >5W.

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

## 9g servo
![servo](http://wiki.keyestudio.com/images/3/31/7723.png) При установке угла в 180? **TODO** серво-привод начинал непрерывно вращаться

## CMOS Камера OV7670
Не пытался подключить. Есть книга на 200 страниц
[Beginning Arduino ov7670 Camera Development](https://www.amazon.com/Beginning-Arduino-ov7670-Camera-Development/dp/1512357987).
При этом есть две версии с Framebuffer и без, та которая с буфером помечена как FIFO и стоит в несколько раз дороже.
Отличительной особенностью является микросхема Averlogic AL4228-PBF, которая упрощает работу.

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

## Блок питания AC-DC transformer, AC Adapter, Rectifier
 
Преобразование идет в несколько этапов: сначала катушками индуктивности напряжение понижается до необходимого, затем через диодный мост выпрямляется, после этого сглаживается при помощи конденсаторов. [Принцип работы](https://www.youtube.com/watch?v=VZctTmmS-gA)

## Инвертор Invertor DC-AC 
4 транзистора и два сумматоров генерируют положительную и отрицательную часть синусоиы [Принцип работы](https://www.youtube.com/watch?v=qVeERT4nyz8)

# Прототипные платы (prototype breadboard)

## Текстолитовые

<img src="https://img.banggood.com/images/oaupload/banggood/images/40/86/ef082e74-2d84-414e-9fc7-59ae7c5f7c49.jpg" width=200 /> без дорожек
<img src="https://ae01.alicdn.com/kf/HTB1UbBnLpXXXXXgaXXXq6xXFXXXD/5-pcs-lot-universal-Stripboard-Veroboard-Seul-C-t-7x5-cm.jpg_640x640.jpg" width=200 /> и с дорожками
выполняются в множестве размеров

## No solder
<img src="https://cdn.sparkfun.com/assets/3/d/f/a/9/518c0b34ce395fea62000002.jpg" width=200 /> Поставляются вместе с ардуиновскими наборами, стыкуются друг с другом. 

# Провода и Коннекторы

## Rainbow ribbon wire
<img src="http://www.electroncomponents.com/image/cache/data/misc/EC_10Wire_Riboon_Cable-500x500.jpg" width=200/> 
<img src="http://thumb1.zeppy.io/d/l400/pict/192363894610/40-pcs-dupont-cables-m-f-m-m-f-f-jumper-breadboard-wire-gpio-ribbon-pi-arduino" width=200/>
Пучок из 20 проводов 10 цветов. Может продаваться либо мотком, либо нарезанным и обжатым коннекторами dupont длиной 10 или 20см. В комплекте коннекторы разных видов М-М М-П П-П.

## Pin headers
Бывают круглы и квадратные для распайки на плате
<img src="https://i.stack.imgur.com/lXhyd.jpg" width=200>
<img src="https://i.stack.imgur.com/QpxI7.jpg" width=200>

## Dupont
<img src="https://ae01.alicdn.com/kf/HTB1jRtPQXXXXXaDXXXXq6xXFXXXq/670pcs-set-2-54mm-Jumper-Wire-Cable-Pin-Header-Dupont-Connector-Dupont-Plastic-Shell-Plug-Dupont.jpg_640x640.jpg" width=200> <img src="https://www.bluetin.io/wp-content/uploads/2017/07/sn-28b-dupont-terminal-crimping-tool-kit.jpg" width=200 />
Коннекторы которые идут с Arduino в виде цветных проводов, как раз относятся к этому стандарту. Можно купить отдельно цветной жгут и отдельно коннекторы. Обжимаются специальным инструментом Crimper Tool с характерным M-образным профилем. Можно обжать пассатижами, но будет менее аккуратно. Разъемы группируются от 1 до 10, мама, папа и папа для распайки на плате. Коннекторы не фиксируются.

## XH2 Pitch terminal
<img src="https://ae01.alicdn.com/kf/HTB1F4PkOpXXXXcIXFXXq6xXFXXXo/40-Sets-Kit-in-box-XH2-54-Right-Angle-2p-3p-4p-5pin-2-54mm-Pitch.jpg_640x640.jpg" width=200 /> Коннекторы с защелками, могут быть очень тугими. Для обжимки используется crimping tool, можно обжать пассатижами. Идут комлпектами от 2 до 5 пинов.

## 9V Clip Barrel Male
<img src="https://i.ebayimg.com/images/g/N9oAAOSw5cNYUl~f/s-l300.jpg" width=200 />
Адаптер для батарей вида PP3 (крона) в   5.5 мм x 2.1 мм

# Инструменты
<img src="https://ae01.alicdn.com/kf/HTB1zivrawmTBuNjy1Xbq6yMrVXaT/DIYFIX-4-7-Mini-Electronic-Pliers-Diagonal-Side-Cutting-Pliers-Cable-Wire-Cutter-Repair-Pry-Open.jpg_640x640q90.jpg" width=200 /> Бокорезы (Diagonal Side Cutter Plier) для откусывания торчащих кончиков

# Пайка

## Паяльные принадлежности (soldering iron)
<img src="https://rukminim1.flixcart.com/image/832/832/j44h7680/soldering-iron/h/b/z/complete-kit-of-60w-soldering-iron-with-adjustable-temp-5x-bits-original-imaev2ptr9wzbs5f.jpeg?q=70" width=200 /> На Aliexpress огромное количество паяльников, в том числе регулируемых (adjustable) по температуре 200-450 C.

С паяльником в комплекте могут идти сменные жала (soldering iron heads). Моей ошибкой было поставить самое тонкое в итоге паять было неудобно, поставил потолще.

<img src="https://ae01.alicdn.com/kf/HTB1dvX2oCYH8KJjSspdq6ARgVXag/Useful-Solid-Metal-Base-Soldering-Iron-Bracket-Stand-Holder-Support-Station-Frame-Portable-for-Electrical-Working.jpg_640x640.jpg" width=200 /> К паяльнику обязательно нужна стойка (soldering iron frame/stand/holder)

Для очистки жала (solder tip cleaners) используется либо целлюлозная губка (sponge), которая используется в намоченном состоянии, либо медная стружка (steel wire). Нсли не очищать жало, то сгоревший флюс будет ухудшать качество пайки.

<img src="https://c.76.my/Malaysia/1set-hand-soldering-iron-stand-helping-magnifying-tool-small-chewhoung-1109-11-chewhoung@1.jpg" width=200> Третья рука (Helping Third Hand Clip Tool Soldering Stand), много разных видов, в том числе в 2 и 4 крокодилами, гибкие и жесткие. Используется, для удержания платы при пайке.

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
