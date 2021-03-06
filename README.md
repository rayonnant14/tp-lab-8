

<img src="img/green.png" width="50" height="50">

# Cpp-lab-8

## Практикум №8 (Генератор текста)

### Задание

Разработать программу-генератор текста на основе цепи Маркова. 

### Краткие сведения из теории

Мы можем синтезировать текст, используя символы, сочетания символов, слова, сочетания слов, предложения.
Одной из разновидностей синтеза является частотный синтез.

Алгоритм частотного синтеза на уровне символов прост:

```
строка S =пустое слово
пока не достигнем строки заданной длины
  из таблицы символов выбираем символ C с вероятностью P(C)
  дописываем символ C к строке S
```

В результате образуется строка заданной длины, состоящая из символов.

Полученная строка, скорее всего, совершенно бессмысленна (и трудночитаема). Повысить читаемость можно, составляя текст из k-сочетаний, наиболее часто встречающихся в языке.

Например, в русском языке, часто встречаются следующие последовательности букв

```
СТ, НО, ЕН, ТО, НА, ОВ, НИ, РА, ВО, КО
СТО, ЕНО, НОВ, ТОВ, ОВО, ОВА
```

Для получения еще более читаемого текста нужно формировать текст либо из слов, либо из сочетаний слов.

Рассмотрим пример, основанный на **цепи Маркова**

Рассматриваемый алгоритм в качестве исходных данных будет использовать специальную таблицу префиксов, состоящих из двух слов и суффиксов, представляющих собой одно слово. Эта таблица образуется в результате анализа большого текстового файла.

Алгоритм генерирует фразы на выходе, случайным образом выбирая для определенного префикса следующий за ним суффикс.

Описание алгоритма:

```
поместить в W1 и W2 первые два слова
вывести W1 и W2
цикл:
  случайно выбрать W3 из набора суффиксов
  к префиксу W1 и W2
  заменить W1 и W2 на W2 и W3
  повторить цикл
```

### Использование стандартной библиотеки С++

В данной работе должны использоваться элементы стандартной библиотеки.


```c++
typedef deque<string> prefix;          // очередь префиксов
map<prefix, vector<string> > statetab; // префикс-суффиксы
```

В качестве параметров необходимо задать размер префикса (в словах) и объем генерируемого текста:

```c++
const int NPREF=2; // количество слов в префиксе
const int MAXGEN=1000; //объем текста на выходе
```

Процесс работы программы можно представить следующим образом:

- открывается входной файл на чтение
- файл читается по словам и в памяти создается таблица префиксов и суффиксов
- после обработки входного файла начинается процесс генерации выходного текста
- из таблицы берется первый префикс и случайно выбирается для него продолжение (в вифе суффикса)
- происходит переход на очередной префикс и для него снова выбирается суффикс
- генерация заканчивается либо при достижении заданного размера, либо при обработке последнего префикса

### Пример работы


Пример генерации текста на основе текста ''Сказка о Золотой рыбке''

```
Жил старик со своею старухой У самого синего моря; 
Они жили в ветхой землянке Ровно тридцать лет и три года. 
Старик ловил неводом рыбу, Старуха пряла свою пряжу. 
Раз он в море синее просилась, Дорогою ценою откупалась: 
Откупалась чем только пожелаю Не посмел я взять с неё корыто, 
Наше-то совсем раскололось". Отвечает золотая рыбка: 
"Не печалься, ступай себе с богом". Воротился старик ко старухе, 
Что ж он видит? Высокий терем. На крыльце стоит его старуха 
В дорогой собольей душегрейке, Парчевая на маковке кичка, 
Жемчуги огрузили шею, На руках золотые перстни, На ногах красные сапожки. 
Перед нею усердные слуги; Она бьёт их, за чупрун таскает. 
Говорит старик своей старухе: "Здравствуй, барыня-сударыня дворянка! 
Чай, теперь твоя душенька довольна". На него прикрикнула старуха, 
На конюшне служить его послала. Вот неделя, другая проходит, 
Ещё пуще старуха бранится, Не даёт старику мне покою: 
Надобно ей новое корыто; Наше-то совсем раскололось". 
Отвечает золотая рыбка: "Не печалься, ступай себе с богом! 
Добро! будет старуха царицей!" Старичок к старухе воротился 
Глядь: опять перед ним землянка; На пороге сидит его старуха, 
А пред нею разбитое корыто. корыто. 
```



 
## Список участников/веток

|  ФИО              | Имя ветки |
|-------------------|-----------|
|Альперович	Вадим | b1|
|Андрющенко	Александр|b2|
|Аросланкин	Артем|b3|
|Востряков	Дмитрий|b4|
|Горбачева	Арина|b5|
|Горшкова	Екатерина|b6||
|Доненко	Денис|b7|
|Исупова	Мария|b8|
|Кислицына	Анастасия|b9|
|Куклин	Максим|b10|
|Лесин	Николай|b11|
|Макридин	Максим|b12|
|Максимов	Антон|b13|
|Малинин	Василий|b14|
|Мартиросян	Елизавета|b15|
|Мурзаев	Роман|b16|
|Сазанов	Дмитрий|b17|
|Седунов	Илья|b18|
|Сиднева	Анастасия|b19|
|Ситникова	Владислава|b20|
|Слесарева	Василина|b21|
|Смольникова	Полина|b22|
|Тюлин	Владислав|b23|
|Филиппова	Марина|b24|
|Черноземова	Дарья|b25|
|Чернышев	Константин|b26|
|Черняев	Ярослав|b27|
|Втюрин Павел|b28|
|Славутин Александр|b29|
|Семкин Павел|b30|

## Алгоритм выполнения работы

Для выполнения работы необходимо:

1. Выполнить *fork* репозитария в свой аккаунт.
1. Выполнить клонирование репозитария из своего аккаунта к себе на локальную машину (`git clone`).
1. Создать ветку **git** с индивидуальным номером (`git branch имя_ветки`).
1. Сделать ветку активной (`git checkout имя`).
1. Необходимо разместить как исходные файлы с решениями задач, поместив **cpp** файлы в **src**, а заголовочные - в **include**. 
1. Добавить файлы в хранилище (`git add`).
1. Выполнить фиксацию изменений (`git commit -m "комментарий"`).
1. Отправить содержимое ветки в свой удаленный репозитарий (`git push origin имя_ветки`).
1. Создать пул-запрос в репозитарий группы и ждать результата от **Travis-CI**.

