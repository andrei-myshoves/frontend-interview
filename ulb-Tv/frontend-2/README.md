- Что будет при в битие url и нажатие enter?
- https://youtu.be/hkrmyIecHR0?t=562
- Последовательность:

Проверка кеша (browser cache / DNS cache)

DNS-резолвинг → домен → IP

Установка TCP-соединения (3-way handshake)

TLS-handshake (если HTTPS)

Отправка HTTP-запроса

Сервер формирует ответ

Ответ приходит браузеру

Парсинг HTML

Загрузка ресурсов (CSS, JS, картинки)

Построение DOM + CSSOM → Render Tree

Layout → Paint → Composite

- Какие атрибуты загрузки скриптов?
- https://youtu.be/hkrmyIecHR0?t=657
- У <script> есть три важных:

defer

Загружает параллельно

Выполняет после загрузки HTML, но до DOMContentLoaded

Сохраняет порядок

 async

Загружает параллельно

Выполняет как только загрузится

Порядок не гарантируется

type="module"

автоматически включает defer

поддерживает import/export

- Если у нас есть какойто файл стилей большой на 50 мегабайт пока он грузится заблокирует нам рендеринг?
- https://youtu.be/hkrmyIecHR0?t=728
- Да, CSS блокирует рендеринг.

Пока браузер не скачает и не построит CSSOM, он не может:

отрисовать страницу

показать контент

То есть пользователь увидит белый экран.

- Корс что это такое ?
- https://youtu.be/hkrmyIecHR0?t=800
- CORS (Cross-Origin Resource Sharing) — механизм браузера, который контролирует, какие сайты могут отправлять запросы к другим доменам.

Если сервер не разрешает → браузер блокирует.

- Подход через токены?
- https://youtu.be/hkrmyIecHR0?t=902
- Аутентификация через:

Access token — короткоживущий

Refresh token — обновляет access token

Хранятся обычно:

access → memory / localStorage

refresh → httpOnly cookie

Используется в OAuth/JWT.

- Вопрос про спецефичтность селекторов?
- https://youtu.be/hkrmyIecHR0?t=1131
- Приоритет от большего к меньшему:

!important

Inline-style: style=""

ID: #id

Class, pseudo-class, attribute селекторы: .class, :hover, [attr]

Тег селекторы: div, h1

- (универсальный)

* все про event loop ?
* https://youtu.be/hkrmyIecHR0?t=1209
* JS работает в один поток, но браузер помогает.

Event Loop делает:

Выполняет код из стека

Если стек пуст — берёт задачи:

сначала микрозадачи

затем макрозадачи

- Что кроме промисов попадает к микрозадачам?
- https://youtu.be/hkrmyIecHR0?t=1368
- В microtask queue попадают:

Promise.then()

async/await

queueMicrotask()

Обработчики MutationObserver

В Node.js — process.nextTick

- Что кроме промисов может туда еще попадать?
- https://youtu.be/hkrmyIecHR0?t=1403
- См. выше — microtask queue = Promises, MutationObserver, queueMicrotask.
- Применение функции debounce на практике?
- https://youtu.be/hkrmyIecHR0?t=1447
- debounce — ограничение частоты вызовов функции.

Используется:

поиск "как пользователь печатает"

resize/scroll обработчики

автосохранение

фильтры по вводу

Пример: вызывать запрос только когда пользователь перестал печатать 500 мс.

- Модифицированый пример чтобы помимо консоли появлялся Боб?
- https://youtu.be/hkrmyIecHR0?t=1586
- см выше задачу
- Задача №2
- https://youtu.be/hkrmyIecHR0?t=1705
- см выше задачу
- Ревью ошибок и поправление?
- https://youtu.be/hkrmyIecHR0?t=1960
- опять же сомтреть видео
- Какие отличия типа эни от анкноу?
- https://youtu.be/hkrmyIecHR0?t=2300
- Отличие any от unknown
   any

Отключает типизацию полностью

Можно делать что угодно

 unknown

Крайне безопасный

Нельзя использовать, пока не проверишь тип

- Какие стэйт менеджерами приходилось работать?
- https://youtu.be/hkrmyIecHR0?t=2404
- :

Redux Toolkit

Zustand

MobX

Recoil

Jotai

Context API

Минимум — Redux Toolkit + Context API.
- Как следишь за частотой кода?
- https://youtu.be/hkrmyIecHR0?t=2469
- Линтеры (ESLint)

Форматтер (Prettier)

Code Review

Профилирую производительность

Следую архитектурным правилам проекта