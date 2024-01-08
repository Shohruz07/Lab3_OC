# Lab3_OC
Модуль для ядра Linux

FOR RUN CODE

1.kali㉿kali~$ ```bash sudo apt-get install linux-headers-$(uname -r) ``` 

2.kali㉿kali~$     ```bash make 
    cd ~/path/to/content
    ``` 

3.kali㉿kali~$    ```bash
    cd ~/path/to/content
    ``` sudo insmod lab.ko

4.kali㉿kali~$     ```bash
    cd ~/path/to/content
    ```lsmod | grep lab

lab                    12288  0 
5.kali㉿kali~$     ```bash
    cd ~/path/to/content
    ```cat /proc/tsu

Hello  

6.kali㉿kali~$    ```bash
    cd ~/path/to/content
    ``` dmesg | tail -n 1

[ 2476.224946] procfile read(1704733782): tsu

7.kali㉿kali~$    ```bash
    cd ~/path/to/content
    ``` sudo rmmod lab

8.kali㉿kali~$    ```bash
    cd ~/path/to/content
    ``` dmesg | tail -n 1 

[ 2519.142778] Tomsk State University forever!

====> Код представляет собой модуль ядра Linux, который создает файл процедуры с именем «tsu» и регистрирует операцию чтения для этого файла. При чтении файла модуль проверяет, прошло ли с момента последнего чтения меньше или равно 20 секундам. Если это так, он возвращает 0, указывая, что операция чтения не удалась. В противном случае он записывает строку «Hello\n» в буфер, предоставленный пользователем, и возвращает длину сообщения. Модуль также инициализирует время последнего просмотра до 30 секунд перед загрузкой модуля и удаляет файл proc при выгрузке модуля.
