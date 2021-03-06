https://habr.com/ru/company/yandex/blog/469021/

как только у тебя появляется больше одного сервиса, неизбежно начинают возникать общие части: модели, утилиты, инструменты, куски кода, шаблоны, компоненты. Встает вопрос: куда все это девать? Конечно, можно копипастить, мы это умеем, но хочется же красиво.

Мы пробовали даже такую сущность, как SVN externals, для тех, кто помнит. Мы пробовали git-сабмодули. Мы пробовали npm-пакеты, когда они появились. Но все это было как-то долго, что ли. Ты поддерживаешь какой-нибудь пакет, находишь ошибку, вносишь исправления. Затем тебе нужно выпустить новую версию, пройтись по сервисам, обновиться на эту версию, проверить, что все работает, запустить тесты, обнаружить ошибку, вернуться обратно в репозиторий с библиотекой, поправить ошибку, выпустить новую версию, пройтись по сервисам, обновиться и так по кругу. Это просто превращалось в боль.



Тогда мы подумали, не съехаться ли нам в один репозиторий. Взять все наши сервисы и библиотеки, перенести и разрабатываться в одном репозитории. Обнаружилось достаточно много плюсов. Я не говорю, что этот подход идеальный, но с точки зрения компании и даже отдела из нескольких групп появляются значимые плюсы.

Лично для меня самое важное — атомарность коммитов, то, что я как разработчик могу одним коммитом поправить библиотеку, обойти все сервисы, внести изменения, запустить тесты, проверить, что все работает, запушить в мастер, и все это одним изменением. Не нужно ничего пересобирать, публиковать, обновлять.

Но если все так хорошо, почему в монорепозиторий еще не переехали все? Конечно, в нем есть и минусы.



Как сказала руководитель службы разработки API Яндекс.Карт Марина Перескокова — посадил дед монорепу, выросла монорепа большая-пребольшая. Это факт, не шутка. Если вы собираете много сервисов в одном монорепозитории, он неизбежно разрастается. А если мы говорим про git, который вытягивает все файлы плюс всю их историю за все время существования вашего кода, это довольно большой дисковый объем.

Вторая проблема — вливание в мастер. Ты подготовил пул-реквест, прошел ревью, уже готов его сливать. И выясняется, что кто-то успел вперед тебя и тебе нужно разрешать конфликты. Ты разрешил конфликты, опять готов вливать, и ты опять не успел. Эта задача решается, есть системы merge queue, когда специальный робот автоматизирует эту работу, выстраивает пул-реквесты в очередь, пытается разрешить конфликты, если может. Если не может — призывает автора. Тем не менее, такая проблема существует. Есть решения, которые ее нивелируют, но нужно иметь ее в виду.

Это технические моменты, но есть еще и организационные. Предположим, у вас несколько команд, которые делают несколько разных сервисов. Когда они переезжают в монорепозиторий, у них начинает размываться ответственность. Потому что они сделали релиз, выкатили в продакшен — что-то сломалось. Начинаем разбор полетов. Выясняется, что это разработчик из другой команды что-то закоммитил в общий код, мы это потянули, зарелизили, не увидели, все сломалось. И непонятно, кто ответственен. Это важно понимать и использовать все возможные способы: юнит-тесты, интеграционные тесты, линтеры — все, что можно, чтобы уменьшить эту проблему влияния одного кода на все остальные сервисы.

Интересно, а кто еще кроме Яндекса и других игроков использует монорепозиторий? Довольно много кто. Это React, Jest, Babel, Ember, Meteor, Angular. Люди понимают — проще, дешевле, быстрее разрабатывать и публиковать npm-пакеты из монорепозитория, чем из нескольких маленьких репозиториев. Самое интересное, что вместе с этим процессом начали развиваться инструменты работы с монорепозиторием. Как раз о них и хочу поговорить.

Все начинается с создания монорепозитория. Самый известный во фронтенд-мире инструмент для этого называется lerna.
