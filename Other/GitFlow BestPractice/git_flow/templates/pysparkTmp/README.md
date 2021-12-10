# Шаблон проекта PySpark App
>

<br>

### Содержание
* [Install](#install)
* [Usage](#usage)
* [User-Story](#install)
* [Acknowledgments](#acknowledgments)
* [Changelog](#changelog)
* [Data metrics](#data-metrics)
* [To-Do](#to-do)
* [Releases](#releases)
<br>


### User-Story

> **[?]** Какую задачу для пользователя решает данный проект

- Краткое, но полноценное описание юзер-стори данного проекта


### Install

> **[?]** Как начать использовать данные проекта

<a name="instal"></a>
```bash
# Create your spark job

# run
bash Makefile
```

## Usage

> **[?]**

<a name="usage"></a>

### Usage

```bash
spark-submit \
	--py-files jobs.zib, ufuncs.zip, libs.zip \
	--files conf.json \
	main.py --job tmp_job.py
```



### Acknowledgments :thumbsup:

<a name="acknowledgments"></a>

> **[?]** Описание особенностей использование или используемых библиотек (полезно, если есть что-то не стандартное). А так же, Canvas разработки модели, который включает в себя:

- перечислить разработчиков и их контакты
- перечислить стейкхолдеров
- указать ссылку на `epic` \ `project` в JIRA
- какой общий DoD закладывается
- важно описать  baseline
- какие метрики МЛ (PR, ROC_AUC) / Бизнеса (Retention, Churn) используются



### Changelog :memo:

<a name="changelog"></a>

> **[?]** В основном readme или в специальном файле стоит вести `CHANGELOG`, который выступает в виде истории изменений `HISTORY`. Также можно использовать Wiki

- необходимо описывать проделанные изменения и их результат, с указание базового коммита

### Data metrics

<a name="data-metrics"></a>

> **[?]** Описываем основные результаты. Можно поставить скриншоты или результаты работы, которые отражают результаты data-модели или base line


### To-Do :man:

<a name="to-do"></a>

> **[?]** Если проект в разработке, то можно проецировать ключевые этапы. Если проект будет _"заморожен"_, то поможет быстро вернуться к проекту

- [x] Сделать base line
- [ ] Добавить новые данные в модель
- [ ] "Тюнинг" модели ...


### Releases

<a name="releases"></a>

> **[?]** Заполняется по правилу: tag релизала - для чего сделан, его особенности и тп.
