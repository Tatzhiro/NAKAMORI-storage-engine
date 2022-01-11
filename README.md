# NAKAMORI-storage-engine
Implementation of a MySQL storage engine in ver 8.0.27 for macos11 on x86_64<br>
## How to add a storage engine to your MySQL<br>
1. clone the mysql source tree from mysql-server github page(reference 1)<br>
2. ```cmake #InsertPathHere#/mysql-server``` (adjust "#InsertPathHere#", this cmake has to be done outside of mysql-server directory, I am using a directory named mysql-work; reference 11)<br>
3. ```cd mysql-work/storage```<br>
4. ```cp -r example nakamori```<br>
5. rename the files (e.g. ha_example.cc to ha_nakamori.cc) and replace 'EXAMPLE' and 'example' to 'NAKAMORI' and 'nakamori' in the files (including CMakeLists.txt)<br>
6. ```make nakamori``` in mysql-work directory
7. ```sudo mv ./plugin_output_directory/ha_nakamori.so /usr/local/mysql/lib/plugin``` in mysql-work directory<br>
8. ```mysql -u root -p```<br>
9. ```install plugin nakamori soname 'ha_nakamori.so'```<br>

## Reference
mysql/mysql-server<br>
https://github.com/mysql/mysql-server/tree/8.0/storage/example<br>
第84回　ストレージエンジンをビルドしてみる<br>
https://gihyo.jp/dev/serial/01/mysql-road-construction-news/0084<br>
Chapter 23 Writing a Custom Storage Engine<br>
https://dev.mysql.com/doc/internals/en/custom-engine.html<br>
C言語でテキストファイルを読み込み特定の１行を削除する<br>
http://ithat.me/2015/10/02/clang-text-file-line-delete<br>
MySQL のストレージエンジンについて調べた<br>
https://takatoshiono.hatenablog.com/entry/2015/06/26/234053<br>
takatoshiono/mysql-mycsv<br>
https://github.com/takatoshiono/mysql-mycsv<br>
MySQL  8.0.27  Source Code Documentation<br>
https://dev.mysql.com/doc/dev/mysql-server/latest/<br>
MySQLのストレージエンジンを自作してみる<br>
https://norikone.hatenablog.com/entry/2018/12/29/MySQL%E3%81%AE%E3%82%B9%E3%83%88%E3%83%AC%E3%83%BC%E3%82%B8%E3%82%A8%E3%83%B3%E3%82%B8%E3%83%B3%E3%82%92%E8%87%AA%E4%BD%9C%E3%81%97%E3%81%A6%E3%81%BF%E3%82%8B<br>
Writing a MySQL Storage Engine from Scratch<br>
https://www.codeproject.com/Articles/1107279/Writing-a-MySQL-Storage-Engine-from-Scratch<br>
詳解 MySQL<br>
https://www.amazon.co.jp/exec/obidos/ASIN/4873113431/takatoshiono-22/<br>
ConoHaの上でひたすらMySQLをビルドする簡単なおしごと in 2019年<br>
https://yoku0825.blogspot.com/2019/12/conohamysql-in-2019.html<br>
