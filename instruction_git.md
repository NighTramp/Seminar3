# Инструкция по работе с Git


## Предисвловие

Дорогой читатель, в данном пособии я постараюсь подробно рассказать о том, какие команды Git пригодятся в работе и как с этим всем жить.

## Git - что это? Зачем оно?

>Что же такое Git, если говорить коротко? Очень важно понять эту часть материала, потому что если вы поймёте, что такое Git и основы того, как он работает, тогда, возможно, вам будет гораздо проще его использовать. Пока вы изучаете Git, попробуйте забыть всё, что вы знаете о других СКВ, таких как Subversion и Perforce. Это позволит вам избежать определённых проблем при использовании инструмента. Git хранит и использует информацию совсем иначе по сравнению с другими системами, даже несмотря на то, что интерфейс пользователя достаточно похож, и понимание этих различий поможет вам избежать путаницы во время использования.</br></br>Источник: https://git-scm.com/book/ru/v2/Введение-Что-такое-Git%3F

### Перед начало работы

Как многие программисты перед началом работы пишут программу "Hello, world!", так и у Git есть команда, с помощью которой можно проверить работоспособность среды. Для этого необходимо прописать в терминале следующую компаду:

    git --version

Это команда в случае корректно установленной среды выведет вам версию Git. Так вы убедитесь, что Git есть на вашем устройстве и готов к работе.

### Представьтесь пожалуйста

Не справедлив, что Git представился вам, сообщил вам свою версию, а вы ничего в ответ ему не сказали. Будем вежливыми)

    git config --global user.name "<никнэйм>"

    git config --global user.email <адрес электронной почты>

Далее все ваши действия в Git буду подписаны этими данными. Вы всегда сможете узнать, кто и когда сделал то или иное изменение.

### Создание репозитория

Для начала работы с использованием контроля версии необходимо создать репозиторий.

>Репозиторий - место, где хранятся и поддерживаются какие-либо данные. Чаще всего данные в репозитории хранятся в виде файлов, доступных для дальнейшего распространения по сети.</br></br>Источник: https://ru.wikipedia.org/wiki/Репозиторий

Чтобы создать (инициализировать) новый репозиторий в текущей папке, нужно в терминале ввести команду:

    git init

### Проверка состояния репозитория

Следующая команда будет применяться очень часто. Ведь при работе с проектами любой сложности мы не всегда можем помнить всё. Данная команда подскажет, есть ли незафиксированные изменения.
    
    git status

### Добавление версионности

Любые действие совершенные внутри репозитория: создание\удаление\переименование файлов, изменения в коде хранящемся в файлах - всё это изменения.
Для того, чтобы Git добавил изменения внесенные в вами в систему для отслеживания необходимо после совершения изменений ввести команду: 

    git add <имя_файла.раширение_файла>

### Фиксация изменений

После добавления внесенных исменений в контроль версий необходимо зафиксировать (утвердить) внесенные изменения с добавлением комментария.
После этого ваши изменения зафиксируются системой контроля версий, и вы всегда сможете с помощью комментария понять, что это за действия.<br>Для фиксации изменений необходимо ввести команду:

    git commit -m "комментарий"

Так же можено ввести просто:

    git commit

Тогда коментарий вам будет предложено ввести в отдельно.

### А что же мы наделали?

Работаем, пишем, хотим посмотреть, а как же много мы успели написать, как много камитов мы создали? Или нам срочно надо вернуться к каким-то изменениям, но мы даже на знаем куда же нам возвращаться? Для этого существует команда:

    git log

Она выводит подробный список камитов.<br>
Если нам нужно вывести тот же список, но в менее подробном представлении, есть атрибут:

    git log --oneline

Такая команда выведет вам список комитов в минималистичном варианте.<br>

### А в чём разница?

Теперь мы знаем, как найти адреса наших комитов. И если уж это контроль версий, мы хотим знать, а что нового добавилось или удалилось в том или ином комите в сравнени с каким-то другим. Для этого существует команда:

    git diff <id_1> <id_2>

Если не указывать идентификаторов, то команда выдаст результат сравнения текущего состояния файла в текстовом редакторе, с последним закомиченным состоянием.<br>Если же прописать идентификаторы, то в результате мы увидим различия между двумя указанными закомиченными состояниями файла.

### Назад в будущее!

> \- Это не возможно!<br> \- Это наука!

А теперь мы знаем, как посмотреть "адреса" наших комитов и можем прыгнуть в прошлое, чтобы изменить что-то. Для того, чтобы перейти к нужному комиту, необходимо ввести команду:

    git checkout <идентификатор_комита>

Для возврата к последнему актуальному комиту в основной ветке нам достаточно вместо его идентификатора прописать имя ветки, в которой он находится. Например:

    git checkout master

master - частое наименование головной ветки проекта.<br><br>

\- Что за ветки такие? Вы слишком часто о них начали говорить.<br>
\- Не волнуйтесь, об этом подробнее будет дальше)

## Работа с ветками в Git

Ветки в git используются для совместной работы над проектом, а текже, для разделения общей задачи на подзадачи.

### Просмотр всех веток

Для просмотра всех веток испльзуется команда:

    git branch

Она покажет полный список существующих веток и выделит ту, на которой вы сейчас находитесь.

### Создание новой ветки

По началу у нас есть только одна ветка - основная. Чаще всего она называется main или master. Для того чтобы разделить задачу между несколькими людьми, нам нужно создать для каждой задачи свою ветку, свой изолированный вариант изменений.<br>
Чтобы создать новую ветку используется команда:

    git branch <имя_ветки>

### Слияние веток

Когда вы закончили работать над задачей и вам нужно добавить результаты из ветки задачи в основную ветку, вам нужно сделать слияние веток. Слияние происходит в ту ветку, в которой вы сейчас находитесь<br>
Для слияния веток используется команда:

    git merge <имя_ветки>

После чего изменения сделанные в указанной ветке будут добавлены в ту ветку в которой вы сейчас находитесь.<br>

**Важно!**

    При слиянии возможно возникновение конфликтов. В базовом варианте консоли слияние происходит по принципу добавления всех вариантов. После чего файл необходимо отредактировать, удалив "хвосты". Если же вы пользуетесь текстовыми редакторами, то в зависимости от реализации, могут предлагаться различные варианты слияния.

### Удаление веток

    - Поработал?
    - Убери за собой.

Если ветка уже не нужна, и работать вы с ней больше не планируете, её нужно удалить.<br>
Для удаления ветки используется команда:

    git branch -d <имя_ветки>

## Работа с удаленными репозиториями

# Заключение

Git - это не просто инструмент. Это ваш самый лучший друг в процессе разработки. Он ничего не забывает и ничего не прощает) Спросите его, и он всегда готов показать вам тот или иной момент вашего проекта. Не даст запутаться вам, и поможет организовать параллельную работу с другими. 
