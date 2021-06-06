## Boot
```java
//загрузка множества пакетов по порядку
sudo apt-get install package-x package-y
```

## Полезные мелочи
```java
// Вырезать аудил из видео и конвертировать
ffmpeg -i input.mp4  -c:a copy aac.aac ; ffmpeg -i aac.aac output.mp3
// Открыть файл приложением по умолчанию
xdg-open XXX
// Получить путь расположения программы
which node
// Настройка BASH в терминале как основного редактора
	//add the following to your .bashrc :        
	 export VISUAL=vim;
	 export EDITOR=vim;

find which locate grep sed
clear echo sort sudo sudo chown
tar whatis
cd  домашний           cd - предыдущ  рабоч каталог            cd / корневой
ls -a     ls -l  ls -ltdahrst
file 
archlinux-java
tar zxvf jre-8u73-linux-x64.tar.gz
which java
history
ls --help
java -XshowSettings:properties -version 2>&1 > /dev/null | grep 'java.home'
sudo swapoff -a && swapon -a
sudo dmidecode --type memory

sudo apt install lm-sensors hddtemp
sudo sensors-detect
sensors
```
## Работа с alias	
```java
vim ~/.bashrc 
alias msrv='cd ~/yandex/msrv'
alias msrvi='cd ~/yandex/msrv; markserv'
или
alias msrvi='cd ~/yandex/msrv; markserv --livereloadport 35728'
```

## Информация о системе
```java
uname -a
sudo lshw     // аппаратное обеспечение 
lscpu         //информация об процессоре
lsblk 	      // список дисков и их разделов
lspci	      //инф о всех шинах PCI а также о всех устройствах, присоединенных к этим шинам, видеокартам, сетевым адаптерам)
lspci -t      //инф в виде дерева
lspci -v      //инф о каждом подключкнном устройстве
lsscsi	      // Вывести список устройств scsi/sata
sudo fdisk -l // о списке имеющихся разделов
sudo dmidecode -t memory // об оперативной памяти
sudo dmidecode -t bios // о биос
sudo dmidecode -t processor // о процессоре
lsusb          // о каждом подключенном устройстве
free -m        // свободная оперативка в системе
lscpu
screenfetch
lshw
hwinfo
lspci
inxi
lsblk
df                   // доступное дисковое пространство
pydf
free -m
```
## Файлы

```java
//Создание файла
touch filename.ext
cat > filename.ext // для выхода из режима записи CNTRL+d
echo > filename.ext
vim filename.ext
```


```java
//Переименование файла
mv old.ext new.ext
```


```java
//удаление  файла
rm file
rm -R folder //  удалить каталог со всеми подкаталогами и файлами в нем
rmdir empty  //  удалить пустой каталог
    
    
```
## Окружение 
```java
//Добавление переменной окружения
cd $HOME
vim .bashrc 
export PATH=/usr/java/<JDK Directory>/bin:$PATH
выйти и	сохранить
source .bashrc              
```
*Note that if you wish to set the PATH for all users, you need to log in as root in the bash shell and perform the above steps on the .profile file in the etc directory and not the __.bashrc__ file in the home directory.*

```java
//Добавление переменной только на время сессии терминала        
export PATH=$PATH:/path/to/dir
```
```java
//FILES

// /etc/environment       
Perfect for adding system-wide directories like
/usr/local/something/bin to PATH variable 
or defining JAVA_HOME. Used by PAM and SystemD.         

// /etc/environment.d/*.conf           
List of unique assignments Perfect for adding system-wide directories
like /usr/local/something/bin to PATH variable or defining JAVA_HOME.
The configuration can be split into multiple files,
usually one per each tool (Java, Go, NodeJS).
Used by SystemD that by design do not pass those values to user login shells.       

// /etc/xprofile        
Shell script executed while starting X Window System session.
This is run for every user that logs into X Window System.
It is a good choice for PATH entries that are valid for every user
like /usr/local/something/bin. The file is included by other script
so use POSIX shell syntax not the syntax of your user shell.

// /etc/profile and /etc/profile.d/*            
Shell script. This is a good choice for shell-only systems.
Those files are read only by shells in login mode.

// /etc/<shell>.<shell>rc.         
Shell script. This is a poor choice because
it is single shell specific. Used in non-login mode.
```
## USB

```java
// Форматировать флешку:     
df  //  вывод дисков  
sudo umount /dev/XXX   //  отмонтировать         	  
sudo mkfs.vfat -n 'Name' -I /dev/XXX           	
//другие файловые системы -  mkfs.ext4, mkfs.msdos, mkfs.vfat         	   
```

```java
// Восстановление флешки после ISO образа:   
sudo parted -l       // показать разделы 
fdisk -l             // найти имя монтирования (sdb например)
fdisk /dev/sd(x)     // 
d		     // to proceed to delete a partition
1		     // to select the 1st partition
d		     // to proceed to delete another partition
n		     // to make a new partition
p		     // to make this partition primary 
1		     // to make this the first partition
w		     // to write the new partition info to the USB 
umount /dev/sd(x)1
sudo mkfs.vfat -F 32 /dev/sd(x)1
```


## Пакетные менеджеры
```java
// PACMAN
pacman -S XXX    // установка     
pacman -Syu      // полное обновление системы    
pacman -Ss XXX  // 	поиск
pacman -U /путь/к/пакету/имя_пакета-версия.pkg.tar.xz    //Установить локальный пакет     
```

```java
// YAY
yay -S   XXX   // установить пакет
yay -Ss  XXX   // поиск пакета в официальных репозиториях
yay -Si  XXX   // поиск в aur  и официальных репозиториях
yay -Syu       // обновить все пакеты из aur
yay mplayer    // выберется меню выбора пакета при установке
yay -Ps	       // печатать статистику
```

## Сеть
```java
sudo lsof -i :80 // показать, чем занят порт
```


## РАЗНЫЕ ПРОГРАММЫ

### youtube-dl 
youtube-dl --help
youtube-dl -x --audio-format mp3  
youtube-dl -x --audio-format mp3 --playlist-start 1 --playlist-end 5
youtube-dl -x --audio-format mp3 --audio-quality 0
youtube-dl -x --audio-format mp3 --audio-quality 0 --playlist-start  --playlist-end  


### Личный список хороших программ

Намименование  | Описание                                                | Установка        | Запуск
---|---|---|---
Glow           | программа для отображения в темминале markdown разметки | yay -S glow      |
VIFM           | терминальный файловый менеджер                          |                  |
TILIX          | терминал                                                |                  |
Taskwarrior    | GTD в терминале                                         | pacman -S task   |
Moc            | music player                                            | pacman -S moc    | mocp
ranger         | терминальный файловый менеджер                          |                  | 
htop           | мониторинг системы                                      |                  |
gtop           | мониторинг системы                                      |                  |
psensor        | мониторинг системы           			         |                  |
glances        | мониторинг системы                                      |                  |
 
 
















