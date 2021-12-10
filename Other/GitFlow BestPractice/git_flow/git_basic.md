# Базовые команды для git

**Содержание**
- [Получение SSH](#ssh)
- [Push / Pull](#pp)
- [Создание ветки](#b)
- [Установка удаленного репозитория](#ro)

_tdb_


## Начало работы

### Получение SSH, чтобы Git нас узнал
<a href='ssh'></a>

1. Шаг создания ключа

```bash
# переменная с нашим email из конфига
EMAIL=$(git config user.email)

# создаем SSH ключ (для нашего ПК и Git хоста)
ssh-keygen -t rsa -b 4096 -C "$EMAIL"

# запуск агента
eval "$(ssh-agent -s)"

# добавляем ключ приватный
ssh-add ~/.ssh/id_rsa

# копируем публичный ключ в буфер обмена
clip < ~/.ssh/id_rsa.pub

# можно просмотреть публичный ключ (и скопировать из строки, если не уверены в clip)
echo ""
cat ~/.ssh/id_rsa.pub
```

2. Добавляем ключ на git

 Путь для GitLab: profile -> settings -> ssh keys -> Добавляем ключ (**expires at** - устанавливаем по максимому)



### Push / Pull
<a href='pp'></a>

1. `Push` для загрузки

```bash
# пакуем
git add .

# создаем коммит и подпись
COMMIT="Максимально сжатый текст, который отражает содержание коммита"
git commit -am "$COMMIT"

# обычная загрузка
# типичные имена, которые используются на месте переменных
REMOTE=origin
BRANCH=master

git push $REMOTE $BRANCH

# загрузка с установкой базового удаленного репозитория (аналог -u)
git push --set-upstream $REMOTE $BRANCH

# не обязательная, но красивая проверка загрузки
echo $(git remote show $REMOTE -n | grep Push | awk '{ print $3 }')
```

2. `Pull` для выгрузки с удаленного репозитория

```bash
# применяем все изменения, которые были сделаны и отложены
# иначе все сотрем и получим только версию с удаленного репозитория
git stash pop

# обновим remote путь для данной фетки
git fetch $REMOTE $BRANCH

# pull обычный
git pull $REMOTE $BRANCH

# pull c перебазированием
git pull $REBASE $REMOTE $BRANCH

# извлечем все данные этого проекта (из pull)
# перейдем на последний коммит
git submodule update

# просмотрим ветвление процесса разработки
git log --oneline --graph
```


### Создание ветки
<a href='b'></a>

```bash
# создаем имя ветки
git checkout -b $BRANCH

# обновляем переменную текущей ветки
CURRENT_BRANCH=$(git branch --show-current | grep "^$PREFIX")

# создаем ветку и на её основе делаем pull
# будет создана локальная ветка на основе ветки из удаленного репозитория
git fetch -q "$BRANCH" "$CURRENT_BRANCH"
git branch --no-track "$CURRENT_BRANCH" FETCH_HEAD
git pull origin "$BRANCH"
echo "Created local branch $BRANCH based on $REMOTE's $BRANCH."
```


### Установка удаленного репозитория
<a href='ro'></a>

```bash
# стандартное имя удаленного репозитория
REMOTE_NAME=origin

# добавление, если не существует
git remote add $REMOTE_NAME $GIT_PATH
git remote -v

# замена существующего репозитория
git remote set-url $REMOTE_NAME $GIT_PATH
git remote -v

# переименование
git remote rename REMOTE_NAME GIT_PATH
git remote -v
```
