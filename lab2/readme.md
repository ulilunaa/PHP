# Лабораторнрая работа №2 Установка и первая программа на PHP 

## Установка PHP
<img width="771" height="270" alt="Screenshot 2026-10-02 192031" src="https://github.com/user-attachments/assets/bda0d171-d3c7-4d26-b5d5-919f608a1f47" />
Установленный PHP

### Шаг 3. Написание первой PHP-программы
<img width="1627" height="777" alt="Screenshot 2026-10-02 190729" src="https://github.com/user-attachments/assets/4847215c-7218-4fac-9119-612e96bd4734" />
<img width="468" height="107" alt="Screenshot 2026-10-02 200432" src="https://github.com/user-attachments/assets/2bf0023b-f2d1-46dc-ab21-eb5be270ddbb" />

### Шаг 4. Вывод данных в PHP
<img width="1635" height="390" alt="Screenshot 2026-10-02 190843" src="https://github.com/user-attachments/assets/5216b8c1-678d-485c-8806-39ac29e04b4b" />

### Шаг 5. Работа с переменными и выводом
<img width="977" height="272" alt="Screenshot 2026-10-02 191910" src="https://github.com/user-attachments/assets/c9f011e1-99a2-412a-95e7-3c5e4bbcf4f8" />
<img width="915" height="186" alt="Screenshot 2026-10-02 191900" src="https://github.com/user-attachments/assets/06e83fba-4dc6-40f2-b5a5-98bc1fc8a5da" />

## Контрольные вопросы
# PHP: установка, проверка и вывод данных

## 1. Какие способы установки PHP существуют?

### Linux
- **Менеджер пакетов** (самый простой способ):
```bash
  # Debian / Ubuntu
  sudo apt update
  sudo apt install php php-cli

  # Fedora / RHEL
  sudo dnf install php
```
- **Сторонние репозитории** (например, PPA `ondrej/php` или Remi), если нужна более новая или конкретная версия PHP.

### Windows
- **Ручная установка**: скачать zip-архив с [windows.php.net](https://windows.php.net/download), распаковать и добавить папку с `php.exe` в переменную `PATH`.
- **Готовые сборки** (PHP + веб-сервер + MySQL): XAMPP, WampServer, OpenServer, Laragon.
- **WSL**: установить Linux внутри Windows и поставить PHP как в Linux.

### Кроссплатформенные способы
- **Docker**:
```bash
  docker run -it --rm php:8.3-cli php -v
```
- **Сборка из исходников**:
```bash
  ./configure && make && sudo make install
```
  Это даёт полный контроль над расширениями, но требует больше времени и знаний.
- **Менеджеры версий** (`phpbrew`, `asdf`): удобны, когда нужно несколько версий PHP одновременно.

---

## 2. Как проверить, что PHP установлен и работает?

1. **Проверить версию** в терминале:
```bash
   php -v
```
   Если PHP установлен, выведется его версия.

2. **Посмотреть подключённые модули**:
```bash
   php -m
```

3. **Запустить тестовый скрипт.** Создать файл `test.php`:
```php
   <?php
   echo "Hello, PHP!";
```
   Запуск:
```bash
   php test.php
```

4. **Проверить работу через браузер** с помощью встроенного сервера:
```bash
   php -S localhost:8000
```
   Затем открыть `http://localhost:8000/test.php`.

5. **Вывести полную информацию о конфигурации**, создав файл с содержимым:
```php
   <?php phpinfo();
```

---

## 3. Чем отличается `echo` от `print`?

Оба являются **языковыми конструкциями** (не функциями), поэтому скобки необязательны. Различия:

| Критерий | `echo` | `print` |
|---|---|---|
| Возвращаемое значение | Ничего не возвращает | Всегда возвращает `1` |
| Количество аргументов | Можно несколько через запятую | Только один |
| Использование в выражениях | Нельзя | Можно |
| Скорость | Чуть быстрее (разница ничтожна) | Чуть медленнее |
| Короткая запись | `<?= $x ?>` | Нет |

### Примеры

```php
<?php
// echo: несколько аргументов
echo "Привет, ", "мир", "!";

// print: один аргумент
print "Привет, мир!";

// print возвращает 1, поэтому его можно использовать в выражении
$result = print "Текст";
echo $result; // 1

// короткая запись echo в HTML-шаблоне
$name = "Uli";
?>
<p>Привет, <?= $name ?>!</p>
```

**Вывод:** на практике почти всегда используют `echo`, а `print` нужен редко, только когда важно возвращаемое значение.
