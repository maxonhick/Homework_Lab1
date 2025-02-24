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
Вывод команды происходит сразу в файл asio.txt, который так же есть [в этом репозитоии](https://github.com/maxonhick/Homework_Lab1/blob/main/asio.txt).
8. Скомпилирутйе *boost*. Можно воспользоваться [инструкцией](https://www.boost.org/doc/libs/1_61_0/more/getting_started/unix-variants.html#or-build-custom-binaries) или [ссылкой](https://codeyarns.com/2017/01/24/how-to-build-boost-on-linux/).  
Компилировать будем с помощью инструкции. Команды:  
```sh
cd ~/boost_1_87_0/

./bootstrap.sh

./b2 --prefix=boost install >> ~/maxonhick/workspace/reports/lab01/build.txt
```
Вывод также есть в [файле из этого репозитория](https://github.com/maxonhick/Homework_Lab1/blob/main/build.txt).  
9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию `~/boost-libs`.  
```sh
mkdir ~/boost-libs

cp lib/*.a ~/boost-libs

ls ~/boost-libs
```  
Создали папку, скопировали и вывели содержимое. Вывод:  
```sh
libboost_atomic.a
libboost_charconv.a
libboost_chrono.a
libboost_container.a
libboost_context.a
libboost_contract.a
libboost_coroutine.a
libboost_date_time.a
libboost_exception.a
libboost_fiber.a
libboost_filesystem.a
libboost_graph.a
libboost_iostreams.a
libboost_json.a
libboost_locale.a
libboost_log.a
libboost_log_setup.a
libboost_math_c99.a
libboost_math_c99f.a
libboost_math_c99l.a
libboost_math_tr1.a
libboost_math_tr1f.a
libboost_math_tr1l.a
libboost_nowide.a
libboost_prg_exec_monitor.a
libboost_process.a
libboost_program_options.a
libboost_random.a
libboost_regex.a
libboost_serialization.a
libboost_stacktrace_addr2line.a
libboost_stacktrace_basic.a
libboost_stacktrace_from_exception.a
libboost_stacktrace_noop.a
libboost_system.a
libboost_test_exec_monitor.a
libboost_thread.a
libboost_timer.a
libboost_type_erasure.a
libboost_unit_test_framework.a
libboost_url.a
libboost_wave.a
libboost_wserialization.a
```
10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.  
Команда: ```du -ah ~/boost-libs```  
-a отображает размер каждого файла
-h форматирует выводимый размер  
Вывод:
```sh
16K	/home/vm/boost-libs/libboost_atomic.a
244K	/home/vm/boost-libs/libboost_charconv.a
148K	/home/vm/boost-libs/libboost_chrono.a
164K	/home/vm/boost-libs/libboost_container.a
12K	/home/vm/boost-libs/libboost_context.a
256K	/home/vm/boost-libs/libboost_contract.a
32K	/home/vm/boost-libs/libboost_coroutine.a
4.0K	/home/vm/boost-libs/libboost_date_time.a
4.0K	/home/vm/boost-libs/libboost_exception.a
244K	/home/vm/boost-libs/libboost_fiber.a
416K	/home/vm/boost-libs/libboost_filesystem.a
932K	/home/vm/boost-libs/libboost_graph.a
124K	/home/vm/boost-libs/libboost_iostreams.a
756K	/home/vm/boost-libs/libboost_json.a
1.7M	/home/vm/boost-libs/libboost_locale.a
2.9M	/home/vm/boost-libs/libboost_log.a
2.7M	/home/vm/boost-libs/libboost_log_setup.a
120K	/home/vm/boost-libs/libboost_math_c99.a
120K	/home/vm/boost-libs/libboost_math_c99f.a
120K	/home/vm/boost-libs/libboost_math_c99l.a
964K	/home/vm/boost-libs/libboost_math_tr1.a
1000K	/home/vm/boost-libs/libboost_math_tr1f.a
928K	/home/vm/boost-libs/libboost_math_tr1l.a
24K	/home/vm/boost-libs/libboost_nowide.a
160K	/home/vm/boost-libs/libboost_prg_exec_monitor.a
480K	/home/vm/boost-libs/libboost_process.a
1.1M	/home/vm/boost-libs/libboost_program_options.a
52K	/home/vm/boost-libs/libboost_random.a
732K	/home/vm/boost-libs/libboost_regex.a
1.2M	/home/vm/boost-libs/libboost_serialization.a
48K	/home/vm/boost-libs/libboost_stacktrace_addr2line.a
16K	/home/vm/boost-libs/libboost_stacktrace_basic.a
8.0K	/home/vm/boost-libs/libboost_stacktrace_from_exception.a
4.0K	/home/vm/boost-libs/libboost_stacktrace_noop.a
4.0K	/home/vm/boost-libs/libboost_system.a
2.2M	/home/vm/boost-libs/libboost_test_exec_monitor.a
284K	/home/vm/boost-libs/libboost_thread.a
24K	/home/vm/boost-libs/libboost_timer.a
116K	/home/vm/boost-libs/libboost_type_erasure.a
2.1M	/home/vm/boost-libs/libboost_unit_test_framework.a
2.3M	/home/vm/boost-libs/libboost_url.a
4.5M	/home/vm/boost-libs/libboost_wave.a
780K	/home/vm/boost-libs/libboost_wserialization.a
30M	/home/vm/boost-libs/
```
11. Найдите *топ10* самых "тяжёлых".
Команда: ```du -ah ~/boost-libs/ | sort -rh | head -n 11 >> ~/maxonhick/workspace/reports/Homework_Lab1/REPORT.md```  
-r сортирует по убыванию  
-h учитывает форматирование  
head -n 11 выводит первые 11, но первая всегда сама директория будет, при такой сортировке  
Вывод:
```sh
30M	/home/vm/boost-libs/
4.5M	/home/vm/boost-libs/libboost_wave.a
2.9M	/home/vm/boost-libs/libboost_log.a
2.7M	/home/vm/boost-libs/libboost_log_setup.a
2.3M	/home/vm/boost-libs/libboost_url.a
2.2M	/home/vm/boost-libs/libboost_test_exec_monitor.a
2.1M	/home/vm/boost-libs/libboost_unit_test_framework.a
1.7M	/home/vm/boost-libs/libboost_locale.a
1.2M	/home/vm/boost-libs/libboost_serialization.a
1.1M	/home/vm/boost-libs/libboost_program_options.a
1000K	/home/vm/boost-libs/libboost_math_tr1f.a
```
