## Homework I

1. Скачайте библиотеку *boost* с помощью утилиты **wget**. Адрес для скачивания `https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz`.
   - Хоть в задании и указана версия, я решил скачать более новую версию: 1.87.0. Команда: ```wget https://sourceforge.net/projects/boost/files/boost/1.87.0/boost_1_87_0.tar.gz ```  
Вывод команды:
```sh
HTTP response 301  [https://sourceforge.net/projects/boost/files/boost/1.87.0/boost_1_87_0.tar.gz]
Adding URL: https://sourceforge.net/projects/boost/files/boost/1.87.0/boost_1_87_0.tar.gz/
HTTP response 301  [https://sourceforge.net/projects/boost/files/boost/1.87.0/boost_1_87_0.tar.gz/]
Adding URL: https://sourceforge.net/projects/boost/files/boost/1.87.0/boost_1_87_0.tar.gz/download
HTTP response 302  [https://sourceforge.net/projects/boost/files/boost/1.87.0/boost_1_87_0.tar.gz/download]
Adding URL: https://downloads.sourceforge.net/project/boost/boost/1.87.0/boost_1_87_0.tar.gz?ts=gAAAAABnu08bVTCwNGk_VeQFfggtWlYHHTTP response 302  [https://downloads.sourceforge.net/project/boost/boost/1.87.0/boost_1_87_0.tar.gz?ts=gAAAAABnu08bVTCwNGk_VeQFAdding URL: https://deac-riga.dl.sourceforge.net/project/boost/boost/1.87.0/boost_1_87_0.tar.gz?viasf=1
Saving 'boost_1_87_0.tar.gz'
HTTP response 200 OK [https://deac-riga.dl.sourceforge.net/project/boost/boost/1.87.0/boost_1_87_0.tar.gz?viasf=1]
boost_1_87_0.tar.gz  100% [=============================================================================>]  147.73M  846.15KB/s
                          [Files: 1  Bytes: 147.73M [879.96KB/s] Redirects: 4  Todo: 0  Errors: 0        ]
```
2. Разархивируйте скаченный файл в директорию `~/boost_1_69_0`
   - Команда: ```tar -xf boost_1_87_0.tar.gz -C ~/ ```  
Вывода тут нет, конмада просто распаковала архив.  
3. Подсчитайте количество файлов в директории `~/boost_1_69_0` **не включая** вложенные директории.
   - Команда: ```find ~/boost_1_87_0 -maxdepth 1 -type f | wc -l```  
Вывод: ```13```
4. Подсчитайте количество файлов в директории `~/boost_1_69_0` **включая** вложенные директории.
   - Использоватьбудем ту же команду, но без ограничения вложенных дирреторий: ```find ~/boost_1_87_0 -type f | wc -l```  
Вывод: ```79424```
5. Подсчитайте количество заголовочных файлов, файлов с расширением `.cpp`, сколько остальных файлов (не заголовочных и не `.cpp`).
   - Заголовочный файла бывают двух типов: '.h' или '.hpp'. Команда: ```find ~/boost_1_87_0 -type f \( -name "*.h" -o -name "*.hpp" \) | wc -l ```  
Вывод: ```17856```
   - Количество файлов типа '.cpp'. Команда: ```find ~/boost_1_87_0 -type f -name "*.cpp" | wc -l ```  
Вывод: ```18233 ```
   - Количество остальных файлов. Команда: ```find ~/boost_1_87_0 -type f \( -name "*.h" -o -name "*.hpp" -o -name "*.cpp" \) | wc -l ```  
Вывод: ```43335```
6. Найдите полный путь до файла `any.hpp` внутри библиотеки *boost*. Команда: ```find ~/boost_1_87_0 -name "any.hpp" >> REPORT.md```  
```>> REPORT.md``` - вывод сразу из командной строки в файл.  
```sh
/home/vm/boost_1_87_0/boost/hana/any.hpp
/home/vm/boost_1_87_0/boost/hana/fwd/any.hpp
/home/vm/boost_1_87_0/boost/type_erasure/any.hpp
/home/vm/boost_1_87_0/boost/fusion/algorithm/query/detail/any.hpp
/home/vm/boost_1_87_0/boost/fusion/algorithm/query/any.hpp
/home/vm/boost_1_87_0/boost/fusion/include/any.hpp
/home/vm/boost_1_87_0/boost/xpressive/detail/utility/any.hpp
/home/vm/boost_1_87_0/boost/any.hpp
/home/vm/boost_1_87_0/boost/geometry/geometries/adapted/detail/any.hpp
/home/vm/boost_1_87_0/boost/spirit/home/support/algorithm/any.hpp
/home/vm/boost_1_87_0/boost/proto/detail/any.hpp
```
7. Выведите в консоль все файлы, где упоминается последовательность `boost::asio`.  
Команда: ```grep -rnw ~/boost_1_87_0 -e 'boost::asio' >> asio.txt```  
Вывод команды происходит сразу в файл asio.txt, который так же есть в этом репозитоии.
8. Скомпилирутйе *boost*. Можно воспользоваться [инструкцией](https://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html#or-build-custom-binaries) или [ссылкой](https://codeyarns.com/2017/01/24/how-to-build-boost-on-linux/).
9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`.
10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.
11. Найдите *топ10* самых "тяжёлых".
