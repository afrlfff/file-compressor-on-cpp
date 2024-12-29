# File Compressor on C++
---

Проект представляет собой реализацию файлового компрессора на C++, который использует различные алгоритмы сжатия и предобработки данных. Все алгоритмы реализованы с нуля без использования сторонних библиотек. Компрессор поддерживает работу с любыми типами файлов. __! Не предназначен для профессионального использования (см. "Примечание") !__

## Описание проекта
Проект включает в себя реализацию следующих алгоритмов:

### Алгоритмы предобработки данных:
* __RLE (Run-Length Encoding)__ — алгоритм сжатия данных, заменяющий повторяющиеся символы на их количество.
* __MTF (Move-To-Front)__ — алгоритм преобразования данных, который перемещает часто встречающиеся символы в начало списка.
* __BWT (Burrows-Wheeler Transform)__ — алгоритм преобразования данных, который переставляет символы для повышения эффективности сжатия.

### Алгоритмы сжатия данных:
* __HA (Huffman Coding)__ — алгоритм сжатия данных, использующий переменную длину кода для каждого символа.
* __AC (Arithmetic Coding)__ — алгоритм сжатия данных, который кодирует данные в одно дробное число.
* __LZ77 (Lempel-Ziv 77)__ — алгоритм сжатия данных, использующий скользящее окно для поиска повторяющихся последовательностей.

### Комбинации алгоритмов:
Компрессор использует следующие комбинации алгоритмов для сжатия данных:
* HA
* AC
* BTW + RLE
* BTW + MTF + AC
* BTW + MTF + HA
* BTW + MTF + RLE + HA
* BTW + MTF + RLE + AC
* LZ77 + HA

### Особенности работы с файлами:
* Для текстовых файлов (`.txt`) компрессор использует алгоритм UTF-8 при считывании и записи данных (если сжатые данные записываются в виде текста).
* Для всех остальных файлов данные считываются побайтово в бинарном режиме и рассматриваются как текст.

### Примечание:
Проект является студенческой работой по реализации базовых алгоритмов сжатия. __Не предназначен для профессионального использования__, потому что не контролирует расход памяти и не является досаточно оптимизрованным. Проект следует использовать лишь для ознакомления и изучения. 

## Как использовать
### Сборка проекта
Для сборки проекта необходимо использовать компилятор C++ (например, `g++`). Перейдите в папку проекта и выполните следующие команды в терминале:
```g++ -o .\bin\file-compressor .\src\main.cpp```

### Запуск компрессора
После сборки проекта вы можете запустить компрессор с помощью следующей команды:
```./file-compressor [тип обработки] [опции] [входной файл] [выходной файл]```

#### Тип обработки:
* `compress`: сжатие
* `decompress`: восстановление

#### Опции:
* `HA`: Использовать алгоритм Huffman Coding.
* `AC`: Использовать алгоритм Arithmetic Coding.
* `BWT+RLE`: Использовать комбинацию BWT + RLE.
* `BWT+MTF+AC`: Использовать комбинацию BWT + MTF + AC.
* `BWT+MTF+HA`: Использовать комбинацию BWT + MTF + HA.
* `BWT+MTF+RLE`: Использовать комбинацию BWT + MTF + RLE + HA.
* `BWT+MTF+RLE+AC`: Использовать комбинацию BWT + MTF + RLE + AC.
* `LZ77+HA`: Использовать комбинацию LZ77 + HA.

### Пример использования:
```./bin/file-compressor compress AC input.txt output.bin```