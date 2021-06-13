# GIT 

##### First steps

```shell
git config --list  #show current configs

#main info
git config --global user.name "Your Name"
git config --global user.email "your_email@whatever.com"

#set prefixes       

#Unix
git config --global core.autocrlf input
git config --global core.safecrlf warn

#Windows
git config --global core.autocrlf true
git config --global core.safecrlf warn

#view of unicode
git config --global core.quotepath off

#initialization of repository   
git init  
```

##### Алиасы

```shell
#Для пользователей Windows:
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.br branch
git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"
git config --global alias.type 'cat-file -t'
git config --global alias.dump 'cat-file -p'
    
#Также, для пользователей Linux:
#Добавьте следующее в файл .gitconfig в вашем $HOME каталоге.
[alias]
co = checkout
ci = commit
st = status
br = branch
hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
type = cat-file -t/
dump = cat-file -p

```
##### Логи
```shell
git log
git log --pretty=oneline   #однострочный
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

git hist --all #Метка --all  означает, что мы видим все ветки. По умолчанию только текущая ветка. Добавление опции --graph в git log вызывает построение дерева коммитов с помощью простых ASCII символов.
    
git hist --max-count=1 # вывод последнего коммита
git cat-file -t <hash>
git cat-file -p <hash>
git cat-file -p <treehash>
git cat-file -p <libhash>
git cat-file -p <hellohash>
git cat-file -p <treehash> # вывод дерева каталогов
git cat-file -p <hellohash>


```

##### Main Activty

```shell
git add                           #добавление в отслеживание
git add .                         #добавление текущего каталога и подкаталогов 
git commit -m "First Commit"      #Если опустите метку -m, git перенесетс в редактор из переменной среды GIT_EDITOR
git status
git add lib/style.css
git add -u                         # принять все изменения



```

##### Ветки

```shell
# HEAD  - указатель на ветку в которой находимся

git checkout -b <branch_name>        #создать новую
git checkout <branch_name>           #переключиться на ветку
git branch -D <branch_name>
git push origin --delete <branch_name> #удалить на сервере

#git checkout -b <имяветки> является шорткатом для git branch <имяветки> за которым идет git checkout <имяветки>.
 
git branch -a                        #показать все ветки, в том числе удаленные
    
    
#СЛИЯНИЕ ВЕТОК
git checkout style
git merge master
    
#Перебазирование как альтернатива слиянию
git rebase master
#Слияние VS перебазирование. конечный результат перебазирования очень похож на результат слияния. Ветка style в настоящее время содержит все свои изменения, а также все изменения ветки master. Однако, дерево коммитов значительно отличается. Дерево коммитов ветки style было переписано таким образом, что ветка master является частью истории коммитов. Это делает цепь коммитов линейной и гораздо более читабельной.
#Когда использовать перебазирование, а когда слияние? Не используйте перебазирование Если ветка является публичной и расшаренной. Переписывание общих веток будет мешать работе других членов команды. Когда важна точная история коммитов ветки (так как команда rebase переписывает историю коммитов). Учитывая приведенные выше рекомендации, я предпочитаю использовать rebase для кратковременных, локальных веток, а слияние для веток в публичном репозитории.





git push -u origin master
$ git push origin master
git remote rm origin








git remote show rem

git log --oneline --decorate --graph --all    === полный граф веток и коммитов


Создание ветки локально и размещение в гитхабе
git push -u origin price
git checkout -b AlexeyBranch   === создали и сразу перешли
git push rem AlexeyBranch



git branch -v
git checkout origin/roll
git checkout master
git branch --no--merged
git branch -a  // показать ветки
git branch --merged
git branch -d lOrderRoll
git checkout master
git branch -D lRoll      //Deleted branch lRoll (was 09ba3aa).
git checkout -b roll origin/roll       //Branch roll set up to track remote branch roll from origin.
git checkout -b rollOrder origin/rollOrder //Branch rollOrder set up to track remote branch rollOrder from origin.
git checkout roll
git merge rollOrder

Отслеживание
git branch -f --track $BRANCH origin/$BRANCH
git push origin $BRANCH





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







```


##### Редактирование изменений
```shell
git checkout hello.html       #отмена локальных изменений (ели не было оgit add)
git reset HEAD hello.html     #отмена индексации  (git add) после нее можно git checkout hello.html для отмены изменений
git revert HEAD               #отмена предыдущего коммита с откатом изменений и созданием нового коммита. при этом коммит, который отменили сохраняется в истории
git reset --hard hash_name    #сброс всех коммитов к конкретному ПОТЕНЦИАЛЬНО ОПАСНАЯ ОПЕРАЦИЯ
git tag -d oops               #просто удаление тэга
git commit --amend -m "***"   #переписать комментарий к последнему коммиту
git checkout --               #откатить изменения до последнего коммита
```

##### История
```shell


# Тэги версий
git tag              #показать все тэги
git tag v1           #создать тэг
git checkout v1~1 // родитель тега v1
git hist master --all  #показатоь все тэги в логах



# Хэши

git checkout <hash>          #переход по хэшам коммитов
cat hello.html               #посмотреть файл
git checkout master          #вернуться к последней версии в ветке master  
  
git hist --max-count=1       #Поиск последнего коммита
    
git cat-file -t <hash>       #Вывод последнего коммита
git cat-file -p <hash>       #Вывод последнего коммита
    
git cat-file -p <treehash>   #вывод дерева хэшей
git cat-file -p <folderhash> #вывод каталога какого-нибудь
git cat-file -p <filehash>   #вывод файла

```

##### Репозитории
```shell
git clone hello cloned_hello      # клонирование репозиторя
git remote                        # имя удаленного репзитория по умолчанию
git remote show origin            # детальная информация 

git fetch                         # будет извлекать новые коммиты из удаленного репозитория, но не будет сливать их с вашими наработками в локальных ветках.
git merge origin/master           # слить извлеченные изменения

git pull                          # эквивалентна комбинации git fetch и git merge.
    
    
# локальную ветку, которая отслеживает изменения удаленной ветки.
git branch --track style origin/style
    

# ЧИСТЫЕ РЕПОЗИТОРИИ    

git clone --bare hello hello.git  #create pure repository

git remote add shared ../hello.git   # Добавление удаленного репозитория 

git push shared master  #отправка изменений в общий репозиторий

git branch --track shared master # отслеживание изменений

#Чистые репозитории (без рабочих каталогов) исп для расшаривания. Обычный git-репозиторий подразумевает, что вы будете использовать его как рабочую директорию, поэтому вместе с файлами проекта в актуальной версии, git хранит все служебные, «чисто-репозиториевские» файлы в поддиректории .git. В удаленных репозиториях нет смысла хранить рабочие файлы на диске, а все что им нужно — это дельты изменений и другие бинарные данные. Как правило, репозитории, оканчивающиеся на «.git» являются чистыми репозиториями. 
   
```


#####  Без пароля git config credential.helper store
```shell
git push https://github.com/name/repo.git/ 
```

##### ssh
```shell
ssh-keygen -t rsa -b 4096 -C "XXXXX_@mail.XX"
eval $(ssh-agent -s)
ssh-add ~/.ssh/Name
//добавка в агент
ssh-add ~/.ssh/id_rsa           // без PUB
ls -al ~/.ssh   // список ssh
ssh -T git@github.com  // привет юзер
```

##### Перемещение файлов
```shell
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


