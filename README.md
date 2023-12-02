# Полное руководство по Git  

Итак, здравствуйте, сегодня мы изучим Git. Для начала нам стоит скачать и установить Git на наш компьютер, предположим что вы используете Windows.


Для начала нам стоит перейти на официальный сайт [Git] (https://gitforwindows.org) , перейти на который вы можете нажав на Git.


Следующим этапом будет установка. 

Устанавливайте с параметрами по умолчанию, этого будет достаточно.
Итак, запускаем Git bash, сейчас мы научимся работать с файловой системой используя терминал bash.
---
Чтобы перейти в какую либо папку, необходимо прописать данную команду в консоль со следующими аргументами:
'''bash
cd dir_name  
'''

Где fir_name название необходимой нам папки, так же мы можем перейти и в сразу несколько папок вперёд, разделяя их последовательно /  Пример:

'''bash
cd C:/Users/Admin/Musik
'''

  В данном примере мы переходим в папку Musik, по пути C:/Users/Admin/.
  Так же мы можем прописывать диск в который мы переходим так:
'''bash
cd /c/..  
'''

Так же для перехода в папку пользователя мы можем вместо указания пути, использовать аргумент ~ (тильда), однако за ней тк же может идти путь папки
  Пример:  
'''bash
cd ~/Musik  
'''
Для указания в пути директории в которой мы находимся, указываем как аргумент . (точка), а для указания более высшей по иерархии папки- ..
  Пример:
'''bash
cd ./dir_name  

cd ..  
'''


## Изучаем новые команды


Следующим этапом будет просмотр папок, для просмотра того, в какой папке мы находимся, мы прописываем команду pwd.
Для просмотра содержания папки существует команда ls , так же в ней могут присутсвовать аргументы того, какую папку мы просмотрим.
Добавив к нему аргумент -a, увидим все скрытые файлы (в том числе с точкой в названии- .filename).

К слову, перейти в корневую директорию возможно указав аргументом / (слэш).

Для чтения файлов используем команду cat (кот).
Пример данных команд:  
'''bash 
pwd  
_//укажет папку, в которой мы находимся_  
ls .  
_//Покажет содержание указанной папки, в нашем случае в той, в которой мы находимся_  
ls -a ~  
_//Покажет все файлы, включая скрытые, в домашней директории_  
  
cat ~/mydir/Readson.txt  
_//Чтение файла Readson.txt_  
'''



## Взаимодействие с файлами и папками


В этой части мы научимся взаимодействовать с файлами. Первым чему мы научимся, это то как создать файл.

Для этого необходимо ввести команду touch (коснуться), а так же указать её имя.

Для того чтобы создать папку, необходимо ввести команду 
 
 Пример:
'''bash
touch newfile.txt  
_//Создаёт файл newfile с расширение txt в текущей папке_  
'''

Следующее чему мы научимся, это удалять файлы или папки

-Чтобы это сделать прописываем команду rm (remove). Используюя модуль -r, мы удаляем всё содержимое папки, а потом её.
 -Для удаления папки прописываем rmdir.  
 К слову о том, как папку создать, для этого необходима команда mkdir.  
  Пример:
'''bash
rm my_stupid_file  
_//Удаляет глупый файл?_  
rm -r Musik  
_//Удаляет всё содержимое папки Musik, а позже и её саму_  
rmdir Amigo  
_//Удаляет надоедливый браузер_  
'''


Так же мы можем выполнить сразу две команды последовательно, разделив их && (амперсант).
 Например:  
'''bash 
mkdir NewDirectory && touch NewDirectory  
_//Вначале создаём новую папке NewDirectiry, а позже переходим в неё_  
'''


##Создаём коммит

 Для начала мы инициализируем репозиторий командой git init.

Для создания коммита, необходимо добавить его в "планируемое", для этого через команду git add добавляем файл, также указав --all, можно добавить всё.

Теперь создаём сам коммит командой git commit -m "message" (message), в кавычках пропысываем свой комментарий.


Пример:  
'''bash
git init  
_//Инициализируем коммит в текущей папке_  
git add --all  
//Подготавливаем для коммита вообще все файлы репозитория  
git commit -m "Наш первый коммит"  
_//Создаёт первый коммит (master ветка)_  
'''

Отлично, коммит создан!


##Синхронизация локального репозитория с удалённым (Github)


Первым что нам стоит сделать, это зарегистрировать наш аккаунт на GitHub.

К слову, необходимо указать наше имя и указать адрес нашего компьютера (для того чтобы показать кто вносит изменения в работу проекта)
для этого необходимо прописать сделующие команды:  
'''bash
git сonfig --global user.name "Имя пользователя"  
git config --global user.email "Электронная почта пользователя"  
_//Для проверки указанных параметров, используем следующую команду:_  
git config --list  
'''

Все данные о пользователе хранятся в пользовательской директории в специальной папке.


Теперь свяжем локальный и удалённый репозитории.  
Для этого создаём ssh ключ с помощью следующей команды:  
'''bash
cd ~  
ls la .ssh  
_//Проверка наличия ssh ключей, если всё отлично- продолжаем_  
ssh-keygen -t ed25519 -C "Здесь указываем электроннюю почту, к которой привязываем ключ"  
_//При ошибке, вводим другую команду, ошибка возникает из за того, что наша ОС не поддерживает данный тип шифрования_  
ssh keyhen -t rsa -b 4096 -C "Эл. почта"  
'''

Далее указываем каталог для хранения ключа, по умалчанию его можно указать нажав клавишу Enter.
  Если желаем, то указываем кодовую фразу, что почти что пароль.

Проверить сгенерированы ли ключи можно следующей командой:  
'''bash 
ls -a ~/.ssh  
'''


На экране появляется два файла, один приватный, им не строит делить, другой публичный, имеет расширение .pub, приватный же неимеет расширения для файла.


Теперь скопируем файл следующими командами:  
'''bash
clip < ~/.ssh/id_rsa.pub  
_//Копирует в буфер обмена ssh ключ_  
_//Если же команда не работает, скопируем вручную_  
cat ~/.ssh/id_rsa.pub  
_//Данная команда выводит содержимое файла на экран, теперь мы копируем ssh ключ_  
'''


Теперь в настройках, в добавлении ssh ключа, переходим по ссылке и указываем ssh ключ.
  Проверям то, связали ли мы репозитории:  
'''bash
ssh -T git@github.com  
_//При первом разе вводим в терминал yes_  
yes  
'''


Если идентификаторы сошлись, всё отлично! Теперь связываем репозитории командой:  
'''bash
git remove add origin "Наш профиль GitHub (ссылка)"  
_//origin- может быть другим_  
'''


Теперь добавим основнкую ветку, используя команду:  
'''bash
git push -u origin master  
_//Иногда в случае ошибки стоит указывать вместо master- main_  
_//флаг -u указывается при первой отправке, в дальнейшем можно просто писать git push_  
'''


###### Итак, мы научились основам Git, научились манипулировать файловой системой через bush, а так же создавать коммиты, репозитории, генерировать ssh ключи,
###### а так же отправлять наш репозиторий и его изменения в GitHub!