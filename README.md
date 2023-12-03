# Полное руководство по Git  

Итак, здравствуйте, сегодня мы изучим Git. Для начала нам стоит скачать и установить Git на наш компьютер, предположим что вы используете Windows.


Для начала нам стоит перейти на официальный сайт [Git](https://gitforwindows.org "скачать Git!") , перейти на который вы можете нажав на Git.

---

Следующим этапом будет установка. 

Устанавливайте с параметрами по умолчанию, этого будет достаточно.
Итак, запускаем Git bash, сейчас мы научимся работать с файловой системой используя терминал bash.
---bash
Чтобы перейти в какую либо папку, необходимо прописать данную команду в консоль со следующими аргументами:  
```bash
cd dir_name  
```

Где fir_name название необходимой нам папки, так же мы можем перейти и в сразу несколько папок вперёд, разделяя их последовательно /  Пример:

```bash
cd C:/Users/Admin/Musik
```

  В данном примере мы переходим в папку Musik, по пути C:/Users/Admin/.
  Так же мы можем прописывать диск в который мы переходим так:
```bash
cd /c/..  
```

Так же для перехода в папку пользователя мы можем вместо указания пути, использовать аргумент ~ (тильда), однако за ней тк же может идти путь папки
  Пример:  
```bash
cd ~/Musik  
```
Для указания в пути директории в которой мы находимся, указываем как аргумент . (точка), а для указания более высшей по иерархии папки- ..
  Пример:
```bash
cd ./dir_name  

cd ..  
```


## Изучаем новые команды


Следующим этапом будет просмотр папок, для просмотра того, в какой папке мы находимся, мы прописываем команду pwd.
Для просмотра содержания папки существует команда ls , так же в ней могут присутсвовать аргументы того, какую папку мы просмотрим.
Добавив к нему аргумент -a, увидим все скрытые файлы (в том числе с точкой в названии- .filename).

К слову, перейти в корневую директорию возможно указав аргументом / (слэш).

Для чтения файлов используем команду cat (кот).
Пример данных команд:  
```bash
pwd  
//укажет папку, в которой мы находимся  
ls .  
//Покажет содержание указанной папки, в нашем случае в той, в которой мы находимся  
ls -a ~  
//Покажет все файлы, включая скрытые, в домашней директории  
  
cat ~/mydir/Readson.txt  
//Чтение файла Readson.txt  
```



## Взаимодействие с файлами и папками


В этой части мы научимся взаимодействовать с файлами. Первым чему мы научимся, это то как создать файл.

Для этого необходимо ввести команду touch (коснуться), а так же указать её имя.

Для того чтобы создать папку, необходимо ввести команду 
 
 Пример:
```bash
touch newfile.txt  
//Создаёт файл newfile с расширение txt в текущей папке  
```

Следующее чему мы научимся, это удалять файлы или папки

-Чтобы это сделать прописываем команду rm (remove). Используюя модуль -r, мы удаляем всё содержимое папки, а потом её.
 -Для удаления папки прописываем rmdir.  
 К слову о том, как папку создать, для этого необходима команда mkdir.  
  Пример:
```bash
rm my_stupid_file  
//Удаляет глупый файл?  
rm -r Musik  
_//Удаляет всё содержимое папки Musik, а позже и её саму_  
rmdir Amigo  
//Удаляет надоедливый браузер  
```


Так же мы можем выполнить сразу две команды последовательно, разделив их && (амперсант).
 Например:  
```bash
mkdir NewDirectory && touch NewDirectory  
//Вначале создаём новую папке NewDirectiry, а позже переходим в неё  
```


##Создаём коммит

 Для начала мы инициализируем репозиторий командой git init.

Для создания коммита, необходимо добавить его в "планируемое", для этого через команду git add добавляем файл, также указав --all, можно добавить всё.

Теперь создаём сам коммит командой git commit -m "message" (message), в кавычках пропысываем свой комментарий.


Пример:  
```bash
git init  
//Инициализируем коммит в текущей папке  
git add --all  
//Подготавливаем для коммита вообще все файлы репозитория  
git commit -m "Наш первый коммит"  
//Создаёт первый коммит (master ветка)  
```

Отлично, коммит создан!


## Синхронизация локального репозитория с удалённым (Github)


Первым что нам стоит сделать, это зарегистрировать наш аккаунт на GitHub.

К слову, необходимо указать наше имя и указать адрес нашего компьютера (для того чтобы показать кто вносит изменения в работу проекта)
для этого необходимо прописать сделующие команды:  
```bash
git сonfig --global user.name "Имя пользователя"  
git config --global user.email "Электронная почта пользователя"  
//Для проверки указанных параметров, используем следующую команду:  
git config --list  
```

Все данные о пользователе хранятся в пользовательской директории в специальной папке.


Теперь свяжем локальный и удалённый репозитории.  
Для этого создаём ssh ключ с помощью следующей команды:  
```bash
cd ~  
ls la .ssh  
//Проверка наличия ssh ключей, если всё отлично- продолжаем  
ssh-keygen -t ed25519 -C "Здесь указываем электроннюю почту, к которой привязываем ключ"  
//При ошибке, вводим другую команду, ошибка возникает из за того, что наша ОС не поддерживает данный тип шифрования  
ssh keyhen -t rsa -b 4096 -C "Эл. почта"  
```

Далее указываем каталог для хранения ключа, по умалчанию его можно указать нажав клавишу Enter.
  Если желаем, то указываем кодовую фразу, что почти что пароль.

Проверить сгенерированы ли ключи можно следующей командой:  
```bash
ls -a ~/.ssh  
```


На экране появляется два файла, один приватный, им не строит делить, другой публичный, имеет расширение .pub, приватный же неимеет расширения для файла.


Теперь скопируем файл следующими командами:  
```bash
clip < ~/.ssh/id_rsa.pub  
//Копирует в буфер обмена ssh ключ  
//Если же команда не работает, скопируем вручную  
cat ~/.ssh/id_rsa.pub  
//Данная команда выводит содержимое файла на экран, теперь мы копируем ssh ключ  
```


Теперь в настройках, в добавлении ssh ключа, переходим по ссылке и указываем ssh ключ.
  Проверям то, связали ли мы репозитории:  
```bash
ssh -T git@github.com  
//При первом разе вводим в терминал yes  
yes  
```


Если идентификаторы сошлись, всё отлично! Теперь связываем репозитории командой:  
```bash
git remove add origin "Наш профиль GitHub (ссылка)"  
//origin- может быть другим  
```


Теперь добавим основнкую ветку, используя команду:  
```bash
git push -u origin master  
//Иногда в случае ошибки стоит указывать вместо master- main  
//флаг -u указывается при первой отправке, в дальнейшем можно просто писать git push  
```


###### Итак, мы научились основам Git, научились манипулировать файловой системой через bush, а так же создавать коммиты, репозитории, генерировать ssh ключи,
###### а так же отправлять наш репозиторий и его изменения в GitHub!


# Изучение основных состояний файлов в Git  
У всех файлов Git есть четыре основных состояния, некоторые состояния подразумевают то, что файл может находится в нескольких таких состояниях сразу.  
Основные состояния:  
1. untracked (неотслеживаемый)  
2. tracked (отслеживаемый)  
3. staged (подготовленный)  
4. modified (модифицированный)   

Итак, untracked состояние характеризуется тем, что данный файл находится в рабочем проекте, и Git это видит, однако не следит за таким файлом, то 
есть он не попадает в commit.
Следующее состояние tracked есть у тех файлов, которые Git отслеживает. Так же они присутсвуют в коммитах и т.д.
Staged состояние файлов проявляется в случае применении на них команды git add filename. Такие файлы подготавлеваются для коммита.
И последнее состояние файлов- modified, отслеживаемый файл, который был изменён, и так же попадает в коммит.
Для того чтобы узнать в каком состоянии находятся файлы проекта, необходимо ввести данную команду в директории проекта:  
```bash  
git status  
```  
Интересный факт, некоторые файлы могут отображаться в отчёте дважды, к примеру за счёт того, что файл был изменён несколько раз, или изменён при состоянии "подготовленный".

### Отслеживаем коммиты  
Для того чтобы быстро просмотреть список коммитов своего проекта, существует данная команда:  
```bash  
git log  
```  
Первым полем коммита является его hash. Hash- это уникальный код каждого проекта, отличительной чертой hash-a является то, что на двух разных компьютерах
один и тот же hash будет в сущности иметь одно и тоже значение. Итак, hash это код определённой длинны, сгенерированный по определённому алгоритму, использующий как
источник к примеру фразу, такой код возможно преобразовать обратно в нашу фразу, используя алгоритм хэширования.  
Следующей строкой идёт имя автора и его электронная почта. Третьей строкой- дата создаия коммита. И последней строкой идёт сообщения коммита- 
в нём кратко и информативно описываются основные изменения. К изменениям можно отнести добавление нового функционала, а так же исправление ошибок старого и т.д.  
А для того чтобы получить сокращённый лог, существует такая вариация предыдущей команды:  
```bash  
git log --oneline  
```  
Данная команда выводит сокращённую информацию о наших коммитах, первым идёт hash коммита, он имеет сокращенную форму, то есть первые n цифр hash-a.
При этом длина hash-a рассчитывается автоматически. За hash-м имёт сообщение. Его размер составляет примерно от 30 до 72 символов.

### Форма сообщений комиитов  
В каждой организации имеются свои правила того, как стоит составлять сообщение коммита, это сделано для удобства просмотра сообщений в логах и т.д.
Но основными требованиями к сообщениям является их краткость, информативность, и общая форма поветствования.
К примеру во многих организациях начало сообщения коммита начинается так: Добавить (а не довил), исправить, и т.д. То есть первое слово глагол в инфиитиве.
Так же во многих организациях применяется Jara- система оргаизции проектов и задач, пример команды с её использованием:  
```bash  
git commit -m "LGS-239: Дополнить список пасхалок новыми числами"  
```  
Здесь же первым идёт тип исправления. 
Это корпаративный стиль оформления коммитов, существует так же GitHub стиль оформления. Пример этого:  
```bash  
$ git commit -m "Исправить #334, добавить график температуры"  
```  
Здесь же первым укаывается номер задачи, так же вместо этого может указываться тип исправления.


###### Вывод: в этот раз мы изучили статусы файлов в Git, узнали что такое hash. а так же потренировались оформлять коммиты. В следующий раз
###### мы изучим mermaid-схемы.
