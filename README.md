# Шпаргалка. Базовые команды в консоли


Чтобы вам было удобнее взаимодействовать с командной строкой, мы подготовили шпаргалку. В ней собраны все команды, о которых мы рассказали в уроках, и их полезные вариации. 


# Навигация


pwd (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;


ls (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;


ls -a — покажи также скрытые файлы и папки, названия которых начинаются с символа .;


cd first-project (от англ. change directory, «сменить директорию») — перейди в папку first-project;


cd first-project/html — перейди в папку html, которая находится в папке first-project;


cd .. — перейди на уровень выше, в родительскую папку;


cd ~ — перейди в домашнюю директорию (/Users/Username);


cd / — перейди в корневую директорию.


# Работа с файлами и папками


## Создание


touch index.html (англ. touch, «коснуться») — создай файл index.html в текущей папке;


touch index.html style.css script.js — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;


mkdir second-project (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.


## Копирование и перемещение


cp file.txt ~/my-dir (от англ. copy, «копировать») — скопируй файл в другое место;


mv file.txt ~/my-dir (от англ. move, «переместить») — перемести файл или папку в другое место.


## Чтение


cat file.txt (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.


## Удаление


rm about.html (от англ. remove, «удалить») — удали файл about.html;


rmdir images (от англ. remove directory, «удалить директорию») — удали папку images;


rm -r second-project (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.


# Полезные возможности


Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (&&).


У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (↑) и вниз (↓).
Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать Tab. Если файл или папка есть в текущей директории, командная строка допишет путь сама.
Например, вы находитесь в папке dev. Начните вводить cd first и дважды нажмите Tab. Если папка first-project есть внутри dev, командная строка автоматически подставит её имя. Останется только нажать Enter.
Команд так много — как их запомнить?
Терминал — мощный инструмент с практически бесконечным количеством команд и параметров. Не переживайте, если не можете запомнить их все. Использовать поисковики или заглядывать в шпаргалку — абсолютно нормально. Даже специалисты с большим опытом часто обращаются к интернету, чтобы вспомнить вариации той или иной команды.

# Что такое хеш. Хеширование коммитов


Хеширование (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать набор данных и получить их «отпечаток» (англ. fingerprint).


Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на предыдущий, или родительский (англ. parent), коммит.


Git хеширует (преобразует) информацию о коммите с помощью алгоритма SHA-1 (от англ. Secure Hash Algorithm — «безопасный алгоритм хеширования») и получает для каждого коммита свой уникальный хеш — результат хеширования.
Обычно хеш — это короткая (40 символов в случае SHA-1) строка, которая состоит из цифр 0 — 9 и латинских букв 
A—F (неважно, заглавных или строчных). Она обладает следующими важными свойствами:


- если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый;
- если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже изменится (причём сильно).


Чтобы убедиться в этом, можно поэкспериментировать с SHA-1 на этом сайте — попробуйте ввести в поле input (англ. «ввод») разные символы, слова или предложения и понаблюдайте, как меняется хеш в поле output (англ. «вывод»).


# Хеш — основной идентификатор коммита


Git хранит таблицу соответствий хеш → информация о коммите. Если вы знаете хеш, вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов. Можно сказать, что хеш — основной идентификатор коммита.


При работе с Git хеши будут встречаться вам регулярно. Их можно будет передавать в качестве параметра разным Git-командам, чтобы указать, с каким коммитом нужно произвести то или иное действие.


Все хеши и таблицу хеш → информация о коммите Git сохраняет в служебные файлы. Они находятся в скрытой папке .git в репозитории проекта.


# Лог


лог (от англ. log — «журнал [записей]»). После вызова git log появляется список коммитов.


Разберём элементы, из которых состоит описание:


- строка из цифр и латинских букв после слова commit — это хеш коммита;
- Author — имя автора и его электронная почта;
- Date — дата и время создания коммита;


в конце находится сообщение коммита.


Получить сокращённый лог можно с помощью команды git log с флагом --oneline (англ. «одной строкой»). В терминале появятся только первые несколько символов хеша каждого коммита и их комментарии.


Сокращённый лог полезен, если в репозитории уже много коммитов — например, сотни или тысячи. В этом случае можно быстро найти нужный по описанию.


Сокращённый хеш (то есть первые несколько символов полного) можно использовать точно так же, как и полный. Для этого команда git log --oneline автоматически подбирает такую длину сокращённых хешей, чтобы они были уникальными в пределах репозитория и Git всегда мог понять, о каком коммите идёт речь.


Обратите внимание: если выход из просмотра логов не произошёл автоматически, нажмите клавишу Q (от англ. Quit — «выйти») в английской раскладке клавиатуры.


# Файл HEAD


При вызове команды git log вы также могли заметить надпись (HEAD -> master) после хеша одного из коммитов. В этом уроке расскажем, что она означает.


Файл HEAD (англ. «голова», «головной») — один из служебных файлов папки .git. Он указывает на коммит, который сделан последним (то есть на самый новый).


В этом можно убедиться с помощью терминала. Перейдите в папку .git командой cd. Посмотрите содержимое файла HEAD командой cat.


Внутри HEAD — ссылка на служебный файл: refs/heads/master (или refs/heads/main в зависимости от названия ветки). Если заглянуть в этот файл, можно увидеть хеш последнего коммита.


Когда вы делаете коммит, Git обновляет refs/heads/master — записывает в него хеш последнего коммита. Получается, что HEAD тоже обновляется, так как ссылается на refs/heads/master.


При работе с Git указатель HEAD используется довольно часто. Мы уже упоминали, что многие команды Git принимают в качестве параметра хеш коммита. Если нужно передать последний коммит, то вместо его хеша можно просто написать слово HEAD — Git поймёт, что вы имели в виду последний коммит.


# Статусы файлов в Git


До появления Git системы контроля версий выделяли только два статуса у файлов: «уже закоммичен» и «ещё не закоммичен». Например, в Subversion (самой популярной VCS до эпохи Git) не нужно было выполнять команду — аналог git add, а можно было просто сделать коммит (svn commit). Эта команда по умолчанию добавляла в коммит все новые и изменённые файлы.


Такое поведение интуитивно более понятно. Зато Git даёт больше контроля за состоянием файлов. Хотя сначала это может показаться сложным, со временем вы оцените удобство более явного подхода.


## Статусы untracked/tracked, staged и modified


Одна из ключевых задач Git — отслеживать изменения файлов в репозитории. Для этого каждый файл помечается каким-либо статусом. Рассмотрим основные.


- untracked (англ. «неотслеживаемый»)


Мы говорили, что новые файлы в Git-репозитории помечаются как untracked, то есть неотслеживаемые. Git «видит», что такой файл существует, но не следит за изменениями в нём. У untracked-файла нет предыдущих версий, зафиксированных в коммитах или через команду git add.


- staged (англ. «подготовленный»)


  После выполнения команды git add файл попадает в staging area (от англ. stage — «сцена», «этап [процесса]» и area — «область»), то есть в список файлов, которые войдут в коммит. В этот момент файл находится в состоянии staged.


- tracked (англ. «отслеживаемый»)


Состояние tracked — это противоположность untracked. Оно довольно широкое по смыслу: в него попадают файлы, которые уже были зафиксированы с помощью git commit, а также файлы, которые были добавлены в staging area командой git add. То есть все файлы, в которых Git так или иначе отслеживает изменения.


- modified (англ. «изменённый»)


Состояние modified означает, что Git сравнил содержимое файла с последней сохранённой версией и нашёл отличия. Например, файл был закоммичен и после этого изменён.


# Типичный жизненный цикл файла в Git

HEAD -- это голова.


Коммит -- это всему голова.


Статусы файлов:


```mermaid
graph LR;
  untracked -- "git add" --> staged;
  staged    -- "change"  --> modified;
  staged    -- "git commit" --> tracked;
  tracked -- "change" --> modified;
  modified -- "git add" --> staged;
``` 
 







