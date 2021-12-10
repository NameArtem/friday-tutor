# Базовые команды для git

**Содержание**
- [Отмена коммита из не правильной ветке и перенос его в другую](#otmcom)
- [Отмена изменений в конкретном файле](#otmc)
- [Шаг назад](#back)
- [Сделать изменение коммита](#cc)

_tdb_


### Отмена коммита из не правильной ветке и перенос его в другую
<a href='otmcom'></a>

```bash
# отменяем коммит
git reset HEAD~ --soft

# фиксируем изменения локально
git stash

# переключиться на нужную ветку
git checkout имя-нужной-ветки

# применяем изменения
git stash pop

# делаем правильный коммит
git add .
git commit -m "ваше сообщение здесь"
```



### Отмена изменений в конкретном файле
<a href='otmc'></a>

```bash
# найти хеш коммита, до которого нужно откатиться
git log

# сохранить хеш нужного коммита
git checkout [some_saved_cache] -- file_path

# старая версия файла окажется в вашем индексе
# создаем коммит
git commit -m "Новое сообщение"
```

### Шаг назад
<a href='back'></a>
```bash
# получить список изменений во всех ветках
git reflog

# обращаемся к элементу по индексу HEAD@{индекс}
# ориентируясь на историю изменений, мы выбираем куда откатываемся
git reset HEAD@{index}
```


### Сделать изменение коммита
<a href='cc'></a>
```bash
# сделайте своё изменение
git add . # или добавьте файлы по отдельности
git commit --amend --no-edit


# или изменить описание коммита
git commit --amend

```