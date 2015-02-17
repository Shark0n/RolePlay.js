# RolePlay
phpBB forum role play JS script

Скрипт RolePlay

Предназначен для использования в форумных играх 5druzey.ru/forum

Скрипт заменяет аватарки и имена игроков форумной ролевой игры только в нужных ветках форума.
- при наведении на аватарку и/или имя персонажа - появляется настоящее имя польователя форума
- при клике - переход к профилю пользователя форума
- можно задавать размер аватарок для подгонки под формата форума
- аватарки автоматически подгоняются по размеру и центрируются

Автор: Shark0n callups@gmail.com

Требования:
- движок форума phpbb 3.0.x
- jQuery 1.5.2 или выше

История версий:
- 1.0 2015.02.10 Рабочая версия скрипта для одной игры
- 1.1 2015.02.10 Переделан для использования одного скрипта для нескольких игр. Добавлены комментарии по коду.
- 1.2 2015.02.10 Повышено удобство инициализации скрипта, добавлены дополнительные настройки для игровых аватарок: высота и ширина
- 1.3 2015.02.10 Добавлены функции автоматической подгонки и центрирования изображения под заданные размеры аватарок: avatarHeight х avatarWidth
- 1.4 2015.02.17 Оптимизация скрипта. Добавлено округление для вычисляемых значений ширины и высоты картинок

INSTALLATION/УСТАНОВКА
=========
Начнем!
## 1. Скачать дистрибутив
Скачиваем архив дистрибутива https://github.com/Shark0n/RolePlay

### 1.1 Справа кнопка Download ZIP

### 1.2 Распаковываем архив


## 2. Редактируем скрипт для игры
Открываем в простом блокноте (не в Word!!!) файл скрипта roleplay.js

### 2.1 Редактируем тему игры
Для этого находим строку 

    gametitle = 'Случай в тихом океане';

Задаем свое название темы ветки на форуме - это будет название первой игры.

### 2.2 Редактируем игроков в файле
Каждый игрок описан тремя параметрами. В примере ниже, это:
- _**Shark0n**_ - логин пользователя на форуме, скрипт заменит его на вымышленное
- _**Бенджамин Тод**_ - вымышленное имя игрока
- _**http ://webnewsmedia.net/wp-content/uploads/2012/12/Detective-903x1024.jpg**_ - путь до файла с вымышленной аватаркой игрока
Для каждого игрока необходимо составить такую конструкцию:

	gamesArr[gametitle]['Shark0n'] = {
	'fakeNickname': 'Бенджамин Тод',
	'fakeAvatar': 'http://webnewsmedia.net/wp-content/uploads/2012/12/Detective-903x1024.jpg'
	};

Заменяем на своих игроков. Лишних удаляем, если не хватает - добавляем.

### 2.3 В один скрипт можно добавить несколькно игр.
Для этого необходимо повторить процедуры из пунктов 2.1 и 2.2

## 3. Загрузка на сервер

### 3.1 Заходим на хостинг через файловый менеджер (ftp или в браузере).
Создаем папку js (с правами chmod 755) в корне форума. Кладем roleplay.js в папку js 

### 3.2 Прописываем скрипт
Открываем для редактирования  /styles/prosilver/template/overall_header.html

Требуется библиотека jQuery. Ищем в файле поиском "jquery".
Если ничего не нашлось - требуется подключить библиотеку jQuery. Для этого находим </head> и вставляем свои строки, чтобы получилось так:

	<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.5.2/jquery.min.js"></script>
	<script type="text/javascript" src="/js/roleplay.js"></script>
	</head>

Если "jquery" нашлось, тогда вставляем только одну строку с нашим скриптов roleplay.js, чтобы было похоже на то, что выше.
Важный момент, чтобы наш скрипт шел ниже строки со скриптом "jquery".

Сохраняем изменения в файле overall_header.html

## 4. Проверка скрипта
Переходим на форум в тему с названием игры - при обновлении страницы темы с игрой аватарки и логины пользователей должны замениться на игровые.
Если у пользователя-игрока нет аватарки, то игровая аватарка все равно будет добавлена.


TROUBLESHOOTING/Устранение проблем
=========
### 1. Новые имена и аватарки не отображаются
Если изображения не поменялись, возможно требуется очистить кэш (cache) форума.
Заходим в панель администратора, на главной странице внизу должна быть кнопка Purge Cache/Очистить кэш
После очистки скрипт должен заработать.