[![voltNik YouTube](http://voltnik.ru/voltnik-banner.jpg)](https://www.youtube.com/channel/UC4s13gPVOMQVX3P1ZpdUwjA?sub_confirmation=1)
![ПРЕВЬЮ](https://github.com/voltNik/GPS-speed-tracker/blob/master/gps-tracker-prev.jpg)
# Автономный GPS трекер. Возможности: Замер скорости, расстояния, максимального удаления, одометр.
* [Описание проекта](#chapter-0)
* [Папки проекта](#chapter-1)
* [Схема подключения](#chapter-2)
* [Материалы и компоненты](#chapter-3)
* [Как скачать и прошить](#chapter-4)
* [FAQ](#chapter-5)
* [Полезная информация](#chapter-6)

<a id="chapter-0"></a>
## Описание проекта
Полностью автономный GPS трекер для определения координат GPS + Глонасс. Зависит только от навигационных систем. Функционал прошивки позволяет замерять текущую скорость,
максимальную скорость, расстояние до нулевой точки, максимальное удаление от нулевой точки, есть одометр пройденного расстояния.
Длительное удержание кнопки записывает текущее местоположение в энергонезависимую память и начинает считать расстояние до этого места.
Ну и конечно это еще точные часы.

Для сборки используется следующий набор комлпектующих:
- контроллер Arduino Nano
- OLED экран 128х64 I2C
- GPS модуль UBLOX M8N
- повышающий преобразователь 3.7В до 5В
- 1шт кнопки
- аккумулятор 200 мАч и более
еще понадобится: цветной монтажный провод, макетнная плата 7x3.

Подробности сборки в ВИДЕО на канале voltNik: https://youtu.be/zGlRL-k8BpU

<a id="chapter-1"></a>
## Папки
- **libraries** - библиотеки для работы с проектом
- **speed_tracker_128x64** - прошивка для экрана 128х64
- **speed_tracker_128x32** - прошивка для экрана 128х32
- **3d-printer** - корпус для печати на 3D принтере

<a id="chapter-2"></a>
## Схема подключения
![СХЕМА2](https://github.com/voltNik/GPS-speed-tracker/blob/master/speed-tracker_bb.jpg)

<a id="chapter-3"></a>
## Материалы и компоненты
- контроллер Arduino Nano: http://ali.pub/28sn0v резерв: http://ali.pub/2351o1
- OLED экран 128х64: http://ali.pub/2351lp
- OLED экран 128х32: http://ali.pub/2dqpqe
- GPS модуль UBLOX M8N (GPS+Glonass): http://ali.pub/2dqpsj резерв1: http://ali.pub/2dqpti резерв2: http://fas.st/iDsaRu
- GPS модуль MN-880  (GPS+Glonass+Compass): http://fas.st/QRgENd
- GPS модуль NZ-GPS (только GPS): http://ali.pub/2dqpvu резерв: http://ali.pub/2dqpw8
- Повышающий преобразователь 10шт: http://ali.pub/23528u
- Микро повышающий преобразователь 10шт: http://ali.pub/2dqpr6
- Мини повышающий преобразователь 8шт: http://ali.pub/2dqprd
- кнопки 25шт: http://ali.pub/28sn4y резерв: http://ali.pub/235230
- Выключатели 20шт: http://ali.pub/2352gf
- монтажный провод 280м: http://ali.pub/27hcky
- черный корпус: http://ali.pub/29hz44 резерв: http://ali.pub/29hz4b
- дешевые макетные платы 10шт: http://ali.pub/29i0fy
Еще может пригодится:
- термоклеевой пистолет http://ali.pub/27hbfq резерв: http://ali.pub/27hbiu
 

<a id="chapter-4"></a>
## Как скачать и прошить
* Скачать архив с проектом
> На этой странице сверху справа зелёная кнопка **Clone or download**, жми её, там будет **Download ZIP**
* Установить библиотеки в:  
`C:\Program Files (x86)\Arduino\libraries\` (Windows x64)  
`C:\Program Files\Arduino\libraries\` (Windows x86) 
* Подключить Ардуино к компьютеру
* Запустить файл прошивки .ino
* Настроить COM порт и модель Arduino
* Настроить что нужно по проекту в файле прошивке
* Нажать загрузить

## Настройки в коде
     Особого смысла менять код не вижу. Код откомментирован. Единственное что может потребоваться изменить скорость работы с GPS модулем - параметр GPSBaud. Иногда они работают на 4800
     Переназначить пины подключения и компонент:
       #define RXPin 4  // UART подключение GPS
       #define TXPin 3  // UART подключение GPS
       #define BUTN1 7  // пин кнопки1
       #define OLED_RENEW 500  // как часто обновлять экран
       #define SERIAL_RENEW 1000  // как часто обновлять данные на serial
       #define GPSBaud 9600 // скорость обмена с GPS часто именно 9600, но встречается и 4800
       #define OLED_I2C_ADDRESS 0x3C // I2C адрес OLED экрана

<a id="chapter-5"></a>
## FAQ
### Основные вопросы
В: Как скачать с этого сайта?  
О: Вверху вверху справа зелёная кнопка **Clone or download**, её жми, там будет **Download ZIP**  

В: Скачался какой то файл .zip, куда его теперь?  
О: Это архив. Надо распаковать.  

В: Компьютер никак не реагирует на подключение Ардуины!  
О: Возможно у тебя зарядный USB кабель, а нужен именно data-кабель, по которому можно данные передавать  

В: Можно сделать по другому?  
О: Можно.  

В: Сколько стоит?  
О: Трекер не продается и на заказ не делаю. Его можно только сделать самому по инструкции и видеогайду.  

### Вопросы по этому проекту
В: А можно сделать из него GSM трекер?  
О: Да, нужно подключить GSM модуль и доработать прошивку на обработку команд SMS.  

В: Какая точность?  
О: 1-3 метра при средней видимости около 10 спутников.  

В: Как долго определяет координаты?  
О: Как и все трекеры при холодном старте 2-5 минут, при теплом старте секунд за 10-20.  


<a id="chapter-6"></a>
## Полезная информация
* [Мой сайт VOLTNIK.RU](http://voltnik.ru/)
* [Мой YouTube канал VOLTNIK](https://www.youtube.com/channel/UC4s13gPVOMQVX3P1ZpdUwjA?sub_confirmation=1)