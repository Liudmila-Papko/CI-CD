### Что такое CI/CD?
**CI/CD** — один из подходов agile-методологии. Эта методология включает в себя два основных принципа: Continuous Integration (непрерывная интеграция) и Continuous Delivery (непрерывная доставка).  

**CI/CD (Continuous Integration – непрерывная интеграция, Continuous Delivery/Deployment – непрерывная доставка/развертывание)** — это технология автоматизации тестирования и доставки новых модулей разрабатываемого проекта заинтересованным сторонам (разработчикам, аналитикам, инженерам качества, конечным пользователям и др.).
**Continuous Integration (CI)**  
Непрерывная интеграция — это процесс, при котором изменения в коде, внесенные разработчиками, регулярно интегрируются в общий репозиторий и проходят автоматическое тестирование.
**Continuous Delivery (CD)**  
Непрерывная доставка — это процесс, при котором изменения, прошедшие автоматическое тестирование, готовы к развертыванию в любой момент.  
**Пример потока CI/CD:**
- Разработчик делает изменения в коде и пушит их в репозиторий (GitHub, GitLab, Bitbucket и т. д.).
- Запускаются автоматические тесты (CI).
- Если тесты проходят, создается готовая сборка.
- Сборка проходит дополнительные проверки и отправляется на тестовые серверы (CD).
- В случае непрерывного развертывания, сборка автоматически деплоится в продакшн.  
### Зачем оно надо?
**Цель CI:**  
Обеспечить стабильность и совместимость новой версии продукта с минимальными задержками.  
**Цель CD:**  
Сделать каждую новую версию программного обеспечения доступной для развертывания.  
В рамках подхода решаются следующие задачи:  
автоматизация последовательной сборки, упаковки и тестирования программных продуктов;  
автоматизация развертывания приложения в различных окружениях;  
минимизация ошибок и уязвимостей программного продукта.  
**Польза CI/CD:**  
Быстрая доставка изменений.  
Раннее выявление багов.  
Снижение ручной работы за счет автоматизации.  
Упрощение процесса развертывания.  
Увеличение уверенности в стабильности системы.  
### Что такое Докер?
**Docker** — это платформа для разработки, доставки и запуска контейнерных приложений. Docker позволяет создавать контейнеры, автоматизировать их запуск и развертывание, управляет жизненным циклом.  
**Контейнеры** — это способ стандартизации развертки приложения и отделения его от общей инфраструктуры.  
Разработчики создают приложение, упаковывают все зависимости и настройки в некоторый единый образ. Затем этот образ можно запускать на других системах, не беспокоясь, что приложение не запустится.
Контейнеры позволяют упаковать в единый образ приложение и все его зависимости: библиотеки, системные утилиты и файлы настройки. Это упрощает перенос приложения на другую инфраструктуру.  
Docker-compose позволяет разворачивать и настраивать несколько контейнеров одновременно.  
**Компоненты Docker**  
- **Docker daemon**  
Это некоторый резидентный процесс, который запущен на хост-машине постоянно. Он владеет всей инфраструктурой, а также предоставляет интерфейс взаимодействия с контейнерами, включающего создание и удаление, запуск и остановку.
- **Docker client (клиент)**  
Это интерфейс командной строки для управления Docker daemon. Мы пользуемся этим клиентом, когда создаем и разворачиваем контейнеры, а клиент отправляет эти запросы в Docker daemon.
- **Docker image (образ)**  
Это неизменяемый файл (образ), из которого разворачиваются контейнеры. Приложения упаковываются именно в образы, из которых потом уже создаются контейнеры.
- **Docker container (контейнер)**  
Это уже развернутое из образа и работающее приложение.
- **Docker Registry**  
Это репозиторий с образами. Разработчики создают образы своих программ и выкладывают их в репозиторий, чтобы их можно было скачать и воспользоваться ими. 
- **Dockerfile**  
Dockerfile — это инструкция для сборки образа. Это простой текстовый файл, содержащий по одной команде в каждой строке. В нем указываются все программы, зависимости и образы, которые нужны для разворачивания образа.
```
FROM python:3 
COPY main.py /
CMD [ "python", "./main.py" ]
```
Первая строчка означает, что за основу мы берем образ с названием python версии 3 это называется базовый образ. Docker найдет его в docker registry, скачает и будет использовать за основу. Вторая строчка означает, что нужно скопировать файл main.py в корень файловой системы контейнера. Третья строчка означает, что нужно запустить python и передать ему в качестве параметра название файла main.py.

### Что такое контейнеризация?
**Контейнеризация** – это процесс развертывания программного обеспечения, который объединяет код приложения со всеми файлами и библиотеками, необходимыми для запуска в любой инфраструктуре.
### Что такое Jenkins? В каком месте там вообще Jenkins как сервис сборки
Jenkins — это фреймворк для непрерывной разработки, написанный на Java. 
Jenkins — это популярный инструмент с открытым исходным кодом для автоматизации процессов, связанных с интеграцией, доставкой и развертыванием программного обеспечения (CI/CD). Он используется для создания, тестирования, доставки и развертывания кода в автоматическом режиме.
Jenkins предоставляет гибкость в настройке процессов через плагины и скрипты, поддерживает множество языков программирования и может интегрироваться с популярными системами контроля версий, контейнеризацией, облаками и другими инструментами DevOps.
Где Jenkins используется как сервис сборки?
Jenkins играет ключевую роль на этапе сборки (build), который является частью процесса CI/CD:
Сервис сборки:
Jenkins управляет процессом автоматической сборки исходного кода. Это может включать:
Компиляцию кода (например, с помощью инструментов вроде Maven, Gradle для Java, или npm для JavaScript).
Сборку артефактов (например, .jar, .war, .apk, или контейнеров Docker).
Создание пакетов для развертывания.
Автоматизация всех шагов:
Jenkins автоматизирует следующие процессы:
Запуск задач сборки по триггерам (изменения в коде, расписание, вебхуки).
Проверка кода с помощью статического анализа или линтинга.
Выполнение тестов (юнит, интеграционных, нагрузочных).
Создание готовых к развертыванию сборок.
Централизация CI/CD-процессов:
В рамках CI Jenkins отвечает за интеграцию кода, а в рамках CD помогает доставить его в тестовые или рабочие окружения.

Как Jenkins работает как сервис сборки?
Основные шаги:
Триггер запуска задачи:
Пуш в репозиторий (например, GitHub или GitLab).
Вебхук из системы контроля версий.
Задача по расписанию (Cron).
Ручной запуск задачи.
Сборка проекта:
Выполнение шагов сборки, заданных в конфигурации Jenkins, например:
Компиляция исходного кода.
Упаковка в артефакт (ZIP, JAR, WAR, Docker-образ).
Подключение инструментов сборки (например, Maven, Gradle, Ant).
Тестирование:
Запуск юнит-тестов, функциональных и интеграционных тестов.
Генерация отчетов о результатах тестов.
Создание артефакта:
Сборка создается и сохраняется в артефактный репозиторий (например, Nexus, Artifactory, Docker Hub).
Развертывание (опционально):
После успешной сборки Jenkins может инициировать развертывание на тестовый или продакшн-сервер.

 Какие Envs вы знаете?
Envs (сокращение от "environments", окружения) в контексте разработки программного обеспечения — это различные среды, в которых приложение разрабатывается, тестируется, и разворачивается. Каждое окружение имеет свою конфигурацию, данные и параметры, чтобы соответствовать определенным этапам жизненного цикла разработки.
Основные типы окружений (Envs):
1. Development (Dev)
Окружение для разработки.
Используется программистами для написания и отладки кода.
Может быть запущено локально на машинах разработчиков или в облаке.
Обычно не имеет строгих ограничений на ресурсы.
Использует заглушки (моки) вместо реальных сервисов.
Пример:
Локальный сервер с минимальными ресурсами, где разработчики экспериментируют с новыми функциями.

2. Testing (Test)
Окружение для тестирования.
Используется для ручного или автоматического тестирования.
Приложение развертывается с целью выполнения функциональных, регрессионных и интеграционных тестов.
Данные обычно синтетические (сгенерированные), чтобы избежать воздействия на реальные системы.
Пример:
Сервер, настроенный для запуска юнит-тестов или интеграционных тестов.

3. Staging (Pre-production)
Окружение, максимально приближенное к боевому (продакшн).
Используется для финальной проверки перед развертыванием.
Повторяет конфигурацию продакшн-сервера, включая данные, настройки и интеграции.
Тестируются производительность и совместимость системы.
Пример:
Отдельный кластер, на котором симулируется боевой трафик и проверяется стабильность новой версии.

4. Production (Prod)
Боевое окружение.
Это среда, где приложение доступно реальным пользователям.
Максимально надежное, безопасное и масштабируемое.
Любые изменения проходят тщательное тестирование перед развертыванием.
Пример:
Серверы или облачные сервисы, обслуживающие трафик клиентов.
Почему важно разделение Envs?
Изоляция: Ошибки на одном уровне не затрагивают другие среды.
Контроль данных: Реальные данные из продакшна не попадают в тестовые среды.
Гибкость: Каждое окружение настроено для выполнения конкретных задач.
Безопасность: Тестирование проводится на безопасных данных и окружениях.

 Что делать, если ошибка появляется в локальной среде, но не появляется в dev/test?

Если ошибка воспроизводится в локальной среде, но не в Dev или Test, это обычно свидетельствует о различиях в конфигурации, данных, или окружении между локальной и другими средами. Вот пошаговый подход к решению проблемы:

1. Понять природу ошибки
Тип ошибки: Логическая, конфигурационная, зависимость или баг в коде.
Лог-файлы: Проверьте логи на локальной машине и Dev/Test, чтобы выявить, что отличается.
Условия воспроизведения: Убедитесь, что выполняете те же действия и используете те же входные данные, что и в других средах.
2. Проверить конфигурацию окружений
Файлы конфигурации: Сравните локальные файлы с конфигурацией Dev/Test.
Проверьте переменные среды: базы данных, API-ключи, порты, настройки.
Убедитесь, что используете правильные версии библиотек, фреймворков и инструментов.
Инструменты и зависимости:
Совпадают ли версии Node.js, Python, Java и других технологий?
Совпадает ли список зависимостей (например, package.json, requirements.txt)?
3. Сравнить данные
Проверьте данные, используемые в локальной среде, и на Dev/Test:
Различия в структуре базы данных.
Наличие/отсутствие данных, которые могут провоцировать ошибку.
4. Проверить настройки сервисов и инфраструктуры
Внешние сервисы:
Совпадает ли доступ к API, сторонним сервисам и внутренним инструментам?
Убедитесь, что используете правильные эндпоинты.
Контейнеризация и виртуализация:
Если локально используется Docker, убедитесь, что образы и контейнеры совпадают с Dev/Test.
Проверьте настройки контейнеров, таких как сеть, объемы, переменные среды.
5. Диагностика через CI/CD
Попробуйте воспроизвести ошибку в других средах (Dev/Test) путем интеграции вашего кода через CI/CD.
Если ошибка все равно не воспроизводится, это может указывать на специфику вашей локальной среды.
6. Проверка кода
Сравните ветку кода, на которой работает локальная среда, с той, что задеплоена в Dev/Test.
Возможно, в локальной ветке есть недавние изменения, которые еще не попали в Dev/Test.
7. Использовать дебаггинг
Локально: Установите точки останова (breakpoints) и проанализируйте процесс выполнения программы.
На Dev/Test: Воспользуйтесь логами и инструментами удаленного дебаггинга.
8. Унификация окружений
Если различия между локальной средой и Dev/Test значительны:

Настройте локальное окружение, максимально похожее на Dev/Test.
Используйте Docker для контейнеризации приложения.
Скопируйте конфигурацию и базу данных из Dev/Test.
Рассмотрите использование локальных эмуляторов или заглушек (моков) для внешних сервисов.
9. Коммуникация с командой
Обсудите проблему с коллегами. Возможно, кто-то сталкивался с похожей ситуацией.
Задайте вопросы разработчикам, тестировщикам или DevOps-инженерам.
10. Документируйте различия
Если удалось выявить причину, зафиксируйте проблему и решение:

Обновите документацию по настройке локального окружения.
Убедитесь, что конфигурации локальной среды актуальны.
Пример:
Если ошибка возникает из-за несовпадения версий Node.js:

Проверьте локальную версию через node -v.
Сравните с Dev/Test.
Убедитесь, что используете одинаковую версию через nvm или другую систему управления версиями.
Что делать, если ошибка появляется в среде разработки/тестирования, но не появляется в локальной среде? 
Если ошибка воспроизводится в среде разработки или тестирования (Dev/Test), но не в локальной среде, это может быть связано с различиями в конфигурациях, данных, окружении или нагрузке. Вот пошаговый подход для анализа и устранения проблемы:

1. Соберите информацию об ошибке
Логи:
Проверьте логи Dev/Test на наличие ошибок или предупреждений.
Сравните их с логами локальной среды.
Контекст ошибки:
Что вызывало ошибку (конкретные действия, запросы, данные)?
Когда ошибка происходит (время, нагрузка)?
Сообщения об ошибке:
Анализируйте стек ошибок, чтобы понять источник.
2. Проверить конфигурацию среды
Файлы конфигурации:

Сравните переменные среды (например, .env) локальной среды и Dev/Test.
Проверьте параметры базы данных, API-ключи, URL-адреса, сетевые настройки.
Сетевые настройки:

Убедитесь, что Dev/Test не использует дополнительные прокси, балансировщики нагрузки или фаерволы, которые отсутствуют в локальной среде.
Версии зависимостей:

Сравните версии фреймворков, библиотек и инструментов (например, через package.json или requirements.txt).
Убедитесь, что используете одинаковую версию языка программирования (Node.js, Python, Java и т. д.).
3. Сравнить данные
База данных:

Проверьте различия в данных между локальной и Dev/Test средами.
Убедитесь, что структура базы данных (схема) одинаковая.
Тестовые данные:

Убедитесь, что Dev/Test используют реальные данные, которые могут вызывать проблемы, не воспроизводимые на синтетических данных локально.
4. Проверить окружение и инфраструктуру
Нагрузка:

Dev/Test может испытывать нагрузку, которая не воспроизводится в локальной среде. Запустите нагрузочные тесты.
Контейнеры/виртуальные машины:

Проверьте настройки Docker/Kubernetes, если Dev/Test работают в контейнерах.
Сравните версии базовых образов и конфигурации.
Операционная система и серверные параметры:

Различия в ОС (Linux/Windows/MacOS) или их версиях могут влиять на поведение приложения.
5. Повторное воспроизведение ошибки
Локально с конфигурацией Dev/Test:

Импортируйте файлы конфигурации и данные из Dev/Test.
Если возможно, подключитесь к базе данных Dev/Test из локальной среды.
На Dev/Test с локальной конфигурацией:

Измените конфигурацию Dev/Test, чтобы использовать локальные параметры, и проверьте, исчезает ли ошибка.
6. Анализ кода
Сравните код, работающий на Dev/Test, с локальной веткой:
Убедитесь, что ваш локальный код синхронизирован с тем, что развернуто.
Возможно, изменения в коде еще не попали в локальную среду.
7. Использовать инструменты мониторинга и дебаггинга
Удаленный дебаггинг:

Настройте удаленный дебаггер (например, с помощью IDE, таких как Visual Studio Code или PyCharm).
Инструменты мониторинга:

Используйте APM-инструменты (например, New Relic, Dynatrace, Datadog) для анализа производительности и ошибок.
Снимки состояния (Snapshots):

Сделайте снимок состояния среды Dev/Test, чтобы увидеть, в каком моменте возникает ошибка.
8. Обратитесь к команде DevOps
Если проблема связана с настройкой инфраструктуры, запросите помощь DevOps-инженеров:

Они могут проверить журналы серверов, сетевые ограничения или конфигурации.
Убедитесь, что Dev/Test правильно синхронизированы с продакшн.
9. Документируйте проблему
Если удалось выявить причину, зафиксируйте различия и решение:

Обновите инструкции для Dev/Test и локальной среды.
Убедитесь, что такие ошибки минимизируются в будущем.
Пример:
Если ошибка связана с различием версий библиотек:

Проверьте локальную и Dev/Test версии через npm ls, pip freeze или аналогичные команды.
Обновите зависимости в локальной среде, чтобы они совпадали с Dev/Test.
Перепроверьте воспроизведение ошибки.
Что делать, если вы находитесь в той же ветке, но разработчик не может воспроизвести эту проблему? 
Если вы и разработчик работаете в одной и той же ветке, но он не может воспроизвести проблему, это может быть связано с различиями в локальных окружениях, данных, конфигурации или зависимости от специфических шагов воспроизведения. Вот что можно сделать в такой ситуации:

1. Подтвердите одинаковость контекста
Убедитесь, что используете одну ветку:

Проверьте, что оба локальных репозитория синхронизированы с веткой (используйте команды git fetch и git pull).
Проверьте коммит через git log или git rev-parse HEAD, чтобы убедиться, что оба используете одинаковую ревизию.
Сравните окружения:

ОС: Разные операционные системы (Linux, Windows, MacOS) могут вести себя по-разному.
Версии инструментов: Сравните версии языка программирования, фреймворков и библиотек (node -v, python --version, npm ls или pip freeze).
2. Сравните конфигурации
Файлы конфигурации:

Проверьте файлы вроде .env, config.json, или settings.yaml, чтобы убедиться, что используете одинаковые переменные среды и параметры.
Параметры запуска:

Сравните команды запуска приложения. Например, использование разных флагов (--debug, --prod) может повлиять на результат.
Подключение к внешним сервисам:

Проверьте, что оба подключаетесь к одним и тем же базам данных, API или сторонним сервисам.
3. Убедитесь в корректности воспроизведения
Действия для воспроизведения:

Пересмотрите шаги для воспроизведения проблемы. Убедитесь, что вы и разработчик выполняете их одинаково.
Запишите пошаговую инструкцию: от запуска приложения до конкретных действий, которые вызывают проблему.
Данные для теста:

Убедитесь, что вы используете одинаковые входные данные (например, запросы или файлы).
Если данные из базы, убедитесь, что они синхронизированы.
4. Передайте свои условия разработчику
Сделайте снимок среды:

Если вы работаете в контейнере или виртуальной машине, поделитесь своей конфигурацией. Например, используйте docker-compose.yml или Vagrantfile.
Снимите логи:

Сохраните логи приложения и передайте их разработчику. Логи могут показать ошибки или предупреждения, которые разработчик не видит.
Снимите скриншоты или видео:

Запишите, как вы воспроизводите проблему. Это поможет исключить разночтения в шагах.
5. Попробуйте воспроизвести проблему в другой среде
Запустите приложение в другой среде:
На Dev/Test сервере.
В контейнере (например, Docker) с идентичной конфигурацией.
Это поможет понять, проблема локальная или воспроизводится везде.
6. Изолируйте проблему
Отладка с разработчиком:

Совместно попробуйте отладить код. Например, с помощью console.log или других методов отладки.
Закомментируйте подозрительные участки:

Если подозреваете, что ошибка вызвана конкретным модулем или функцией, временно закомментируйте их.
7. Обратитесь за помощью
Если проблему не удается воспроизвести, привлеките коллег для анализа. Возможно, кто-то из команды сталкивался с похожей ситуацией.
8. Используйте универсальные инструменты для диагностики
Инструменты мониторинга:
Подключите логи и профилирование (например, APM-инструменты вроде New Relic или Sentry).
Версионирование окружения:
Используйте Docker или Virtualenv, чтобы убедиться, что окружения идентичны.
Пример решения:
Проблема: У вас ошибка в запросе к базе данных, но разработчик не может ее воспроизвести.

Проверьте, используете ли вы и разработчик одну и ту же базу данных.
Убедитесь, что данные идентичны (например, одинаковое количество записей).
Сравните запросы (например, с помощью логов SQL).


Виртуализация создает полноценные виртуальные машины (VM) с собственной операционной системой.
Контейнеризация изолирует приложения в контейнерах, которые используют ядро хостовой операционной системы.









https://selectel.ru/blog/what-is-docker/
https://habr.com/ru/companies/slurm/articles/691876/