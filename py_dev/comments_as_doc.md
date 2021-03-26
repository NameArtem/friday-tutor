# Comments in code as documentations

> Мы любим и создаем код в правилах [PEP8](https://pep8.org/#introduction)

**Почему комментарии важны?**

> В Agile есть правило **"Работающий продукт важнее исчерпывающей документации"**. Что это значит? Не надо делать документацию? Совсем нет, этот пункт надо `правильно` понимать!

**Документация не нужна, когда она стоит на полке в папке, `правильная` документация** это:

- комментарии в коде (`Comments in code as documentations`)
- описание задачи и `user-story`
- readme.md файл с описанием (задачи и экспериментов)
- блок схемы мы описываем в [Diagrams](https://diagrams.mingrammer.com/)
- документация проекта в [Sphinx](https://www.sphinx-doc.org)
- тесты на функции - это документация к функциям

## Стиль комментирования

### Комментарий `#`

- Длинна комментария - 72 знака
- Количество строк - от 1 до 3

```python
def foo():
    # мой обычный коммент
    print("Hello World")
```

Используется для:
- Планирование работ и тегов
```python
# закончить эту функцию
# TODO: Добавить условия конфигурации
```

- Короткое описание кода
```python
# здесь назначаю параметры и обращаюсь конфигурации
```

- Описание алгоритма и причины его использования
```python
# LogReg в качестве baseline (bench - 0.56 AUC)
```

### Установка типов

> Желательно для экспериментов, обязательно для продуктовых решений

- переменные в функции определены типом `name: str`
- то, что функция возвращает определено типом `-> str`
- строки форматируются через `f""`, а не `.format()`

```python
def foo(name: str) -> str:
    # мой обычный коммент
    return(f"Hello {name}")
```


### Docstrings документирование

> Используется для продуктовых решений и сложных функций

- каждый класс имеет своё описание в __doc__, получить его можно `help(str)`
```bash
help(str)
Help on class str in module builtins:
class str(object)
 |  str(object='') -> str
 |  str(bytes_or_buffer[, encoding[, errors]]) -> str
 |
 |  Create a new string object from the given object. If encoding or
 ...
 ```

- описание используется для информирования о работе функции/класса и формирования примера взаимодействия с функцией
```python
def foo(name: str) -> None:
    print(f"Hello, {name}")
say_hello.__doc__ = '''Моя простая функция для обращения по имени
                       | input:
                       |  | name: string
                       | output:
                       |  | None
                       |
                       |  call example:
                       |  | >>> foo('the best team ever')
                       |  | >>> Hello, the best team ever
                    '''
# пример help()
help(foo)
Моя простая функция для обращения по имени
input:
| name: string
output:
| None
call example:
| >>> foo('the best team ever')
| >>> Hello, the best team ever
```

> Docstrings для Class

- используется для `Class` и `Class method`
- используется для описания `Package` и `Module`

```python
class FooClass:
    """
    Простой Класс с набором любимых функций
    ...

    Attributes
    ----------
    name : str
        имя для приветствия

    Methods
    -------
    foo(name=None)
        Мой простой метод, который приветствует
    """

    # базовая строка
    basic_hello_string = "Hello, {name}!"

    def __init__(self, name: str) -> None:
        """
        Parameters
        ----------
        name : str
            Имя для приветствия
        """
        self.name = name

    def foo(self) -> None:
        """
        Мой простой метод, который приветствует

        Parameters
        ----------
        None
        """

        print(self.basic_hello_string.format(name=self.name))
```


### Базовые варианты документирования

**Google rules**

- подходят для sphinx
- являются официальной спецификацией

```python
"""Gets and prints the spreadsheet's header columns

Args:
    file_loc (str): The file location of the spreadsheet
    print_cols (bool): A flag used to print the columns to the console
        (default is False)

Returns:
    list: a list of strings representing the header columns
"""
```

**NumPy/SciPy docstrings**

- подходят для sphinx
- основная документация для аналитических разработок

```python
"""Gets and prints the spreadsheet's header columns

Parameters
----------
file_loc : str
    The file location of the spreadsheet
print_cols : bool, optional
    A flag used to print the columns to the console (default is False)

Returns
-------
list
    a list of strings representing the header columns
"""
```
