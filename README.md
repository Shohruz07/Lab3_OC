# Lab3_OC
Модуль для ядра Linux

FOR RUN CODE

1.kali㉿kali~ sudo apt-get install linux-headers-$(uname -r) 
2.kali㉿kali~ make 
3.kali㉿kali~ sudo insmod lab.ko
4.kali㉿kali~ lsmod | grep lab
lab                    12288  0 
5.kali㉿kali~ cat /proc/tsu
Hello  
6.kali㉿kali~ dmesg | tail -n 1
[ 2476.224946] procfile read(1704733782): tsu
7.'kali㉿kali~ sudo rmmod lab
8.kali㉿kali~ dmesg | tail -n 1 
[ 2519.142778] Tomsk State University forever!

====> Код представляет собой модуль ядра Linux, который создает файл процедуры с именем «tsu» и регистрирует операцию чтения для этого файла. При чтении файла модуль проверяет, прошло ли с момента последнего чтения меньше или равно 20 секундам. Если это так, он возвращает 0, указывая, что операция чтения не удалась. В противном случае он записывает строку «Hello\n» в буфер, предоставленный пользователем, и возвращает длину сообщения. Модуль также инициализирует время последнего просмотра до 30 секунд перед загрузкой модуля и удаляет файл proc при выгрузке модуля.
