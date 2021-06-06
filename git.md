# GIT 48

##### Начало работы

```java
git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"

//Установка окончаний
//Unix
git config --global core.autocrlf input
git config --global core.safecrlf warn

//Windows
git config --global core.autocrlf true
git config --global core.safecrlf warn

//Установка отображения unicode
git config --global core.quotepath off
    
git init  // инициализация
```


##### Главное 
```java
git add   // добавление в отслеживание
git add . // добавление текущего каталога и подкаталогов 
git commit -m "First Commit"
git status
git add lib/style.css
```
*Если вы опустите метку -m из командной строки, git перенесет вас в редактор по вашему выбору. Редактор выбирается из переменной среды GIT_EDITOR*


##### Редактирование изменений
```java
git checkout hello.html //отмена локальных изменений (ели не было оgit add)
    
git reset HEAD hello.html //отмена индексации  (git add) после нее можно git checkout hello.html для отмены изменений
    
git revert HEAD// отмена предыдущего коммита с откатом изменений и созданием нового коммита. при этом коммит, который отменили сохраняется в истории
    
git reset --hard hash_name // сброс всех коммитов к конкретному ПОТЕНЦИАЛЬНО ОПАСНАЯ ОПЕРАЦИЯ
    
    
git tag -d oops// просто удаление тэга

    
    
git commit --amend -m "***" // переписать комментарий к последнему коммиту
    
    
```


##### История
```java
git log
git log --pretty=oneline     /// однострочный
git log --pretty=oneline --max-count=2
git log --pretty=oneline --since='5 minutes ago'
git log --pretty=oneline --until='5 minutes ago'
git log --pretty=oneline --author=<your name>
git log --pretty=oneline --all
git log --all --pretty=format:"%h %cd %s (%an)" --since='7 days ago'

--pretty="..." — определяет формат вывода.
%h — укороченный хэш коммита
%d — дополнения коммита («головы» веток или теги)
%ad — дата коммита
%s — комментарий
%an — имя автора
--graph — отображает дерево коммитов в виде ASCII-графика
--date=short — сохраняет формат даты коротким и симпатичным

 git hist --all //Метка --all гарантированно означает, что мы видим все ветки. По умолчанию показывается только текущая ветка. Добавление опции --graph в git log вызывает построение дерева коммитов с помощью простых ASCII символов. Мы видим обе ветки (style и master), и то, что ветка master является текущей HEAD.
    
    
    
git hist --max-count=1 // вывод последнего коммита
git cat-file -t <hash>
git cat-file -p <hash>
git cat-file -p <treehash>
git cat-file -p <libhash>
git cat-file -p <hellohash>

git cat-file -p <treehash> // вывод дерева каталогов
git cat-file -p <hellohash> //
    

```


##### Алиасы

*Для пользователей Windows:*

```java
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
git config --global alias.type 'cat-file -t'
git config --global alias.dump 'cat-file -p'
    
    //Добавление опции --graph в git log вызывает построение дерева коммитов с помощью простых ASCII символов ДЛЯ ВСЕХ ВЕТОК
```

*Также, для пользователей Unix/Mac:*
*Добавьте следующее в файл .gitconfig в вашем $HOME каталоге.*



```java
[alias]
co = checkout
ci = commit
st = status
br = branch
hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
type = cat-file -t/
dump = cat-file -p
```

##### Хэши

```java
//переход по хэшам коммитов
git checkout <hash>
//посмотреть файл
cat hello.html
// вернуться к последней версии в ветке master    
git checkout master
  
    
//ПЕРЕМЕЩЕНИЯ ПО ХЭШАМ
git hist --max-count=1 //Поиск последнего коммита
    
git cat-file -t <hash> // Вывод последнего коммита
git cat-file -p <hash> // Вывод последнего коммита
    
git cat-file -p <treehash> // вывод дерева хэшей
git cat-file -p <folderhash>  // вывод каталога какого-нибудь
git cat-file -p <filehash> // вывод файла


```


##### Тэги версий

```java
//показать все тэги
git tag
//создать тэг
git tag v1
//«родитель v1» - «первая версия, предшествующая v1».
git checkout v1^  // почему-то не хочет работать
//то же самое
git checkout v1~1 // работает
//показатоь все тэги в логах
git hist master --all

```



##### Ветки
```java
git checkout -b new_branch_name  // создать новую
git checkout branch_name  //  переключиться на ветку

/*git checkout -b <имяветки> является шорткатом для git branch <имяветки> за которым идет git checkout <имяветки>.*/
 
git branch -a // показать все ветки, в том числе удаленные
    
    
//СЛИЯНИЕ ВЕТОК
git checkout style
git merge master
    
//Перебазирование как альтернатива слиянию
git rebase master
 /*Слияние VS перебазирование
Конечный результат перебазирования очень похож на результат слияния. Ветка style в настоящее время содержит все свои изменения, а также все изменения ветки master. Однако, дерево коммитов значительно отличается. Дерево коммитов ветки style было переписано таким образом, что ветка master является частью истории коммитов. Это делает цепь коммитов линейной и гораздо более читабельной.

Когда использовать перебазирование, а когда слияние?
Не используйте перебазирование …
Если ветка является публичной и расшаренной. Переписывание общих веток будет мешать работе других членов команды.
Когда важна точная история коммитов ветки (так как команда rebase переписывает историю коммитов).
Учитывая приведенные выше рекомендации, я предпочитаю использовать rebase для кратковременных, локальных веток, а слияние для веток в публичном репозитории.
*/
```



##### Перемещение файлов
```java
	//1й способ
	mkdir lib
	git mv hello.html lib
	git status

	//2й способ
	mkdir lib
	mv hello.html lib
	git add lib/hello.html
	git rm hello.html


```



##### Репозитории



```java
git clone hello cloned_hello// клонирование репозиторя
git remote// имя удаленного репзитория по умолчанию
git remote show origin//  детальная информация 

git fetch// будет извлекать новые коммиты из удаленного репозитория, но не будет сливать их с вашими наработками в локальных ветках.
git merge origin/master//слить извлеченные изменения
//git pull эквивалентна комбинации git fetch и git merge.
    
    
//локальную ветку, которая отслеживает изменения удаленной ветки.
git branch --track style origin/style
    
//ЧИСТЫЕ РЕПОЗИТОРИИ    
 git clone --bare hello hello.git
/*
Чистые репозитории (без рабочих каталогов) обычно используются для расшаривания.
Обычный git-репозиторий подразумевает, что вы будете использовать его как рабочую директорию, поэтому вместе с файлами проекта в актуальной версии, git хранит все служебные, «чисто-репозиториевские» файлы в поддиректории .git. В удаленных репозиториях нет смысла хранить рабочие файлы на диске (как это делается в рабочих копиях), а все что им действительно нужно — это дельты изменений и другие бинарные данные репозитория.
Как правило, репозитории, оканчивающиеся на «.git» являются чистыми репозиториями. Мы видим, что в репозитории hello.git нет рабочего каталога. По сути, это есть не что иное, как каталог .git нечистого репозитория.
*/
//Добавление удаленного репозитория    
git remote add shared ../hello.git
```



#####  Без пароля
git config credential.helper store
git push https://github.com/AlexanderGulevich/komfort.git/ 
git push https://github.com/AlexanderGulevich/pricehandler.git/


##### ssh
ssh-keygen -t rsa -b 4096 -C "iscander_02@mail.ru"
eval $(ssh-agent -s)
ssh-add ~/.ssh/Alexey
//добавка в агент
ssh-add ~/.ssh/id_rsa           // без PUB
ls -al ~/.ssh   // список ssh
ssh -T git@github.com  // привет юзер


git config --global user.email "you@example.com"
git config --global user.name "Ваше Имя"




git add -u   ///// принять все изменения



git push -u origin master
$ git push origin master
git remote rm origin




 git config --list
$ git status


ветки

HEAD  - указатель на ветку в которой находимся
удаление
git branch -D <branch_name>
git push origin --delete <branch_name>

создание
git branch testing         === создание
git checkout testing     === переключение на существующую ветку
логи
git log --oneline --decorate        ===в какой ветке находимся


f30ab (HEAD, master, testing) add feature #32 - ability to add new
34ac2 fixed bug #1328 - stack overflow under certain conditions
98ca9 initial commit of my project
           Видны ветки “master” и “testing”, которые указывают на коммит f30ab.


git remote show rem

git log --oneline --decorate --graph --all    === полный граф веток и коммитов


Создание ветки локально и размещение в гитхабе
git push -u origin price


git checkout -b AlexeyBranch   === создали и сразу перешли

git push rem AlexeyBranch

Сделать старый коммит в ветке коммитом  HEAD
git checkout <branch-to-modify-head>
 git reset --hard <commit-hash-id-to-put-as-head> 
git push -f


$ git branch -v
$ git checkout origin/roll
$ git checkout master
$ git branch --no--merged
$ git branch -a  // показать ветки
$ git branch --merged
$ git branch -d lOrderRoll
$ git checkout master
$ git branch -D lRoll      //Deleted branch lRoll (was 09ba3aa).
$ git checkout -b roll origin/roll       //Branch roll set up to track remote branch roll from origin.
$ git checkout -b rollOrder origin/rollOrder //Branch rollOrder set up to track remote branch rollOrder from origin.
$ git checkout roll
$ git merge rollOrder

Отслеживание
git branch -f --track $BRANCH origin/$BRANCH
git push origin $BRANCH



$ git checkout --    // откатить изменения до последнего коммита


$ git pull --all  
$ git pull origin price // 
$ git reset --hard HEAD
$ git fetch origin

$ git commit -m "merge roll and roolOrder"
$ git push origin
$ git push origin --delete rollOrder
$ git remote rm origin

//выложить первый коммит создав репозиторий в на гитхабе
git remote add origin https://github.com/USER/demo.git
git push -u origin master

remote branch

remove your folder: git rm -r folder-name.
git remote show origin

git fetch rem     === получил изменения с rem==теперь изменения доступны по rem/master и т.п.
git merge rem/master   ==слить с текущей веткой

git pull rem    ====(если настроено отслеживание ===> fetch+merge автоматом)
git remote show rem
git remote rename origin rem   === переименование алиаса
git remote rm origin     === удалить ссылку



    1. Добавьте файл в .gitignore
    2. git rm --cached --ignore-unmatch имя файла - удаляем файл только из репозитория, и физически файл сохранится на диске
    3. git commit -am "Message"
    4. git push origin {branch name}
    5. 







mkdir     cd hello  // Создание директории
touch  hello.html  // Создание файла
 cd ../
git init      //  создает репозиторий
git add hello.html    //добавляет файл в репозиторий   
git commit -m "my first commit"      //коммит
git сheckout  //  отмена изменений
git add   // добавление изменений в репозиторий








git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"
git config --global core.autocrlf true
git config --global core.safecrlf true

история коммитов
git log
git log --pretty=oneline
git log --pretty=oneline --max-count=2
git log --pretty=oneline --since='5 minutes ago'
git log --pretty=oneline --until='5 minutes ago'
git log --pretty=oneline --author=<your name>
git log --pretty=oneline --all
git log --all --pretty=format:"%h %cd %s (%an)" --since='7 days ago'
git log --pretty=format:"%h %ad | %s%d [%an]" --graph --date=short

    • --pretty="..." — определяет формат вывода.
    • %h — укороченный хэш коммита
    • %d — дополнения коммита («головы» веток или теги)
    • %ad — дата коммита
    • %s — комментарий
    • %an — имя автора
    • --graph — отображает дерево коммитов в виде ASCII-графика
    • --date=short — сохраняет формат даты коротким и симпатичным
алиасы
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
git config --global alias.type 'cat-file -t'
git config --global alias.dump 'cat-file -p'


heroku
https://devcenter.heroku.com/articles/getting-started-with-nodejs#deploy-the-app

 





```

```