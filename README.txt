План разработки с этапами:
Этап 1
создать сингл версию переводчика(запускается на одном компе, по сети не взаимодействует)
в левое окно текст считывается из txt
текст разбивается на блоки
сохраняется в локальную бд
пустые блоки в противоположном окне соответствуют позициям переводимых блоков
проект имеет автосейв по таймеру раз в 5 минут
иметь возможность сохранить перевод в txt

тз по гуи:
1 основное окно:
    2 рабочие области,
    кнопка "сохранить",
    кнопка "выйти",
    выпадающее меню в верхней панели с кнопками:
        сохранить перевод в txt,
        создать новый проект,
        открыть проект,
        удалить проект
2 окно создания проекта:
    ввод названия проекта
    ввод автора оригинала
    ввод ссылки откуда взято
    выбор файла txt
3 окно открыть проект
4 окно удалить проект

тз по бд:
1 база локальных проектов:
    id
    id блока
    название проекта
    автор оригинала
    ссылка откуда взято
2 база проекта:
    id блока
    английский блок
    блок перевода
    под_id_блока(на случай если переведённая часть сильно больше и её пришлось бить на части)
    статус перевода(?)

тз по логике:
1 наладить взаимодействие с бд
2 наладить взаимодействие с гуи
3 написать парсер txt с разбиением на блоки
4 написать сборщик txt из бд


P.S. запускаем программу, открывается окно с пустыми, не активными областями, далее открываем или создаём проект
если открываем то
    подгружаем данные из бд в гуи.
если создаём то
    открываем окно создания проекта,
    после заполнения полей запросом создаём бд или таблицу(я хз)
    считываем файл,
    разбиваем на блоки,
    записываем в бд и отрисовываем в гуи
далее программа работает на манер блокнота и раз в 5 минут сохраняет новые переведённые блоки в бд


Этап 2
добавляется распознавание текста с пдф и возможность загрузить книгу
добавляется клиент серверное взаимодействие и авто синхрон локальный и серверный происходят одновременно
на сервере проекты в состоянии перевода так же хранятся в бд
на клиенте появляется функционал сохранения готового проекта pdf

тз по гуи:
1 нарисовать окно авторизации/регистрации:
    логин
    пароль
    ник

тз по бд:
1 на сервере добавить базу/таблицу пользователей:
    id
    логин
    пароль
    ник
    дата регистрации
2 на сервере сделать таблицу истории входов
    id
    пользователь
    дата входа
    дата выхода
    ip
    версия по(?)
3 добавить базу проектов на сервер и базу/таблицу каждого из проектов по аналоги с клиентскими

тз по логике:
1 сервер
2 проверка валидности учётных данных
3 модуль регистрации пользователя
4 модуль аутентификации пользователя
5 модуль сверки проектов для синхронизации
6 корректное отключение отвалившихся пользователей
7 клиент серверное взаимодействие в клиенте
8 первичная проверка валидности учётных данных
9 модуль локального хранения учётных данных
10 модуль синхронизации проектов с сервером
11 модуль для работы с пдф в обе стороны



P.S. запускаем программу, открывается окно с пустыми, не активными областями,
происходит подключение к серверу, если сохранённых логина и пароля нет то появляется окно ввода учётных данных или регистрации
логинимся или регистрируемся
сохраняем учётные данные и на локальной бд
при подключении к серверу делается автоматический синхрон проектов с сервером
далее открываем или создаём проект
если открываем то
    подгружаем данные из локальной бд в гуи.
если создаём то
    открываем окно создания проекта,
    после заполнения полей запросом создаём бд или таблицу(я хз)
    считываем файл или парсим pdf
    разбиваем на блоки,
    записываем в бд и отрисовываем в гуи
далее программа работает на манер блокнота и раз в 5 минут сохраняет новые переведённые блоки в бд
по возможности по таймеру синхронится с сервером
