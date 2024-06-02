## Tasks
1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz.
2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0
3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.
4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.
5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).
6. Найдите полный пусть до файла any.hpp внутри библиотеки boost.
7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.
8. Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.
9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.
10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
11. Найдите топ10 самых "тяжёлых".
## Work

1. ```bash
   wget https://sourceforge.net/projects/boost/files/boost/1.84.0/boost_1_84_0.tar.gz
   ```
   [wget Boost_1_84_0](https://github.com/Yukkitsune/lab01/blob/master/task_1.txt)
2. ```bash
   tar -xvf boost_1_84_0.tar.gz
   ```  
3. ```bash
   find . -maxdepth 1 -type f | wc -l
   ```
   ```bash
   13
   ```
4. ```bash
   find . -type f | wc -l
   ```
   ```bash
   76801
   ```
5.
   - Заголовочные файлы
     ```bash
     find . -type f -name "*.hpp" -o -name "*.h" | wc -l
     ```
     ```bash
     17487
     ```
   - Файлы .cpp
     ```bash
     find . -type f -name "*.cpp" | wc -l
     ```
     ```bash
     17337
     ```
   - Остальные файлы
     ```bash
     find . -type f -not -name "*.hpp" -not -name "*.h" -not -name "*.cpp"  | wc -l
     ```
     ```bash
     41977
     ```
6. ```bash
   find boost/ -name any.hpp
   ```
   ```bash
   boost/geometry/geometries/adapted/detail/any.hpp
   boost/xpressive/detail/utility/any.hpp
   boost/type_erasure/any.hpp
   boost/hana/any.hpp
   boost/hana/fwd/any.hpp
   boost/any.hpp
   boost/spirit/home/support/algorithm/any.hpp
   boost/fusion/algorithm/query/detail/any.hpp
   boost/fusion/algorithm/query/any.hpp
   boost/fusion/include/any.hpp
   boost/proto/detail/any.hpp
   ```
7. ```bash
   grep -ril "boost::asio"
   ```
   [Boost::asio](https://github.com/Yukkitsune/lab01/blob/master/task_7.txt)
8. ```bash
   ./bootstrap.sh --prefix=boost_output --with-python=python3
   ```
   ```bash
   ./b2 install -j 12
   ```
   [Boost install](https://raw.githubusercontent.com/Yukkitsune/lab01/master/task_8.txt)
9. ```bash
   cd boost_output &&  mv ./lib ~/boost-libs && cd ~/boost-libs
   ```
10. ```bash
    ls -lh
    ```
    [Hard disk space](https://github.com/Yukkitsune/lab01/blob/master/task_10.txt)
11. ```bash
    ls -lS | head -n 11
    ```
    [Top 10 heaviest files](https://github.com/Yukkitsune/lab01/blob/master/task_11.txt)
