# **Проект: Конвертер изображений**

Этот проект представляет собой **конвертер изображений**, который позволяет преобразовывать изображения между различными форматами, такими как **BMP**, **JPEG** и **PPM**. Проект написан на языке **C++** и использует стандартные библиотеки, а также сторонние библиотеки для работы с изображениями, такие как **LibJPEG** для обработки JPEG-файлов. Основная цель проекта — предоставить простой и эффективный инструмент для конвертации изображений между популярными форматами.

---

## **Основные возможности**

### **1. Поддержка нескольких форматов изображений**
Проект поддерживает три основных формата изображений:
- **BMP (Bitmap)** — формат, который хранит изображение без сжатия, что делает его простым для чтения и записи.
- **JPEG (Joint Photographic Experts Group)** — популярный формат для хранения фотографий с использованием сжатия с потерями.
- **PPM (Portable Pixmap Format)** — текстовый или бинарный формат, который используется для хранения изображений в простом и понятном виде.

### **2. Чтение и запись изображений**
- Проект предоставляет функции для чтения и записи изображений в каждом из поддерживаемых форматов.
- Для каждого формата реализованы отдельные функции, которые обрабатывают специфичные для формата данные.

### **3. Модульная архитектура**
- Проект организован таким образом, что каждый формат изображения обрабатывается отдельным модулем.
- Это позволяет легко добавлять поддержку новых форматов в будущем.
- Основной интерфейс для работы с изображениями определён в базовом классе **ImageFormatInterface**, от которого наследуются классы для каждого формата.

### **4. Использование стандартных библиотек**
- Проект активно использует стандартные библиотеки C++, такие как:
  - `<fstream>` для работы с файлами.
  - `<vector>` для хранения данных изображения.
  - `<filesystem>` для работы с путями к файлам.

### **5. Кроссплатформенность**
- Проект написан с учётом кроссплатформенности и может быть скомпилирован на различных операционных системах, включая **Windows** и **Linux**.
- Для сборки используется **CMake**.

---

## **Основные компоненты проекта**

### **1. `img_lib`**
Это основная библиотека, которая содержит базовые структуры данных и функции для работы с изображениями. Включает в себя:
- Класс **Image**, который представляет изображение и предоставляет методы для доступа к пикселям и строкам изображения.
- Структуру **Color**, которая представляет цвет в формате **RGBA** (красный, зеленый, синий, альфа-канал).
- Функции для создания изображений и работы с ними.

### **2. `bmp_image`**
Модуль для работы с **BMP-файлами**. Включает функции для чтения и записи BMP-изображений. BMP-формат обрабатывается с использованием бинарного чтения и записи, что позволяет эффективно работать с этим форматом.

### **3. `jpeg_image`**
Модуль для работы с **JPEG-файлами**. Использует библиотеку **LibJPEG** для чтения и записи JPEG-изображений. Этот модуль обрабатывает сжатие и декомпрессию изображений, что делает его наиболее сложным из всех модулей.

### **4. `ppm_image`**
Модуль для работы с **PPM-файлами**. PPM — это простой текстовый или бинарный формат, который используется для хранения изображений. Этот модуль предоставляет функции для чтения и записи PPM-изображений.

### **5. `main.cpp`**
Основной файл проекта, который содержит логику для конвертации изображений. Он анализирует входные аргументы, определяет формат входного и выходного файлов, а затем вызывает соответствующие функции для чтения и записи изображений.

### **6. `CMakeLists.txt`**
Файл конфигурации для системы сборки **CMake**. Он определяет, как проект должен быть скомпилирован, и указывает зависимости между различными модулями.

---

## **Как работает проект**

### **1. Загрузка изображения**
- Программа принимает на вход два аргумента — путь к входному файлу и путь к выходному файлу.
- В зависимости от расширения входного файла, программа определяет формат изображения и использует соответствующий модуль для его загрузки.

### **2. Конвертация изображения**
- После загрузки изображения, программа определяет формат выходного файла и использует соответствующий модуль для сохранения изображения в новом формате.

### **3. Сохранение изображения**
- Программа сохраняет изображение в указанном формате, используя соответствующий модуль.
- Если формат выходного файла не поддерживается, программа выводит сообщение об ошибке.

---

## **Пример использования**

Программа может быть вызвана из командной строки следующим образом:

```bash
./imgconv input.jpg output.bmp
```

В этом примере программа загрузит изображение в формате **JPEG** и сохранит его в формате **BMP**.

---

## **Преимущества проекта**

### **1. Простота использования**
- Программа имеет простой интерфейс командной строки, что делает её удобной для использования.

### **2. Расширяемость**
- Благодаря модульной архитектуре, проект можно легко расширить для поддержки новых форматов изображений.

### **3. Эффективность**
- Проект использует эффективные алгоритмы для работы с изображениями, что позволяет быстро обрабатывать даже большие файлы.

---

## **Ограничения**

### **1. Поддержка ограниченного числа форматов**
- На данный момент проект поддерживает только три формата изображений. Однако, благодаря модульной архитектуре, добавление новых форматов не составит труда.

### **2. Отсутствие графического интерфейса**
- Программа работает только через командную строку, что может быть неудобно для некоторых пользователей.

---

## **Заключение**

Этот проект представляет собой простой и эффективный инструмент для конвертации изображений между различными форматами. Он может быть полезен как для разработчиков, которые работают с изображениями, так и для обычных пользователей, которым нужно быстро преобразовать изображение из одного формата в другой. Благодаря модульной архитектуре и использованию стандартных библиотек, проект легко расширяем и может быть адаптирован для различных задач.
