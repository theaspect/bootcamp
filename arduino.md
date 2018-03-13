# Полезные вещи при работе с arduino
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

# Стандарты и Протоколы

## GPIO

## PWM
[Pulse width modulation](https://ru.wikipedia.org/wiki/%D0%A8%D0%B8%D1%80%D0%BE%D1%82%D0%BD%D0%BE-%D0%B8%D0%BC%D0%BF%D1%83%D0%BB%D1%8C%D1%81%D0%BD%D0%B0%D1%8F_%D0%BC%D0%BE%D0%B4%D1%83%D0%BB%D1%8F%D1%86%D0%B8%D1%8F) позволяет уменьшать эффективное напряжение на цифровых выходах [arduino](https://www.arduino.cc/en/Tutorial/PWM) [amperka](http://wiki.amperka.ru/%D0%BA%D0%BE%D0%BD%D1%81%D0%BF%D0%B5%D0%BA%D1%82-arduino:%D1%88%D0%B8%D0%BC?s[]=pwm)

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
# Контроллер зарядки одной ячейки аккмулятора FC-57 на базе ТР4056
Даташит [ТР4056](http://cds.linear.com/docs/en/datasheet/405642f.pdf)
[Описание](http://we.easyelectronics.ru/part/zaryadnoe-ustroystvo-dlya-li-ion--na-tr4056.html), [пример](http://www.instructables.com/id/SOLAR-POWERED-ARDUINO-WEATHER-STATION/) использования с солнечной батареей. [Комментарии](https://forum.arduino.cc/index.php?topic=405875.0) по поводу одновременной зарядки нескольких ячеек. Заряжает постоянным током, посепенно повышая напряжение до 4.2v, по достижению 4.2v постепенно понижает ток до наступления отсечки, где-то на 4.18v. Такой профиль заряда называется CC/CV (constant current, constant voltage). Альтернативные [контроллеры](http://electro-shema.ru/chertezhi/zaryadka-dlya-li-ion-akkumulyatorov.html).

# Инструменты
**TODO**

# Провода и коннекторы
**TODO**

# Химия

## Флюсы

## Изоляция
Самый простой и дешевый изолятор – цапон-лак. Растворяется ацетоном.
