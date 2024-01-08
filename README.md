# Lab3_OC
Модуль для ядра Linux

FOR RUN CODE

1.''' sudo apt-get install linux-headers-$(uname -r) '''
2.'''bash make '''
make -C /lib/modules/6.5.0-kali3-amd64/build M=/home/kali/Downloads modules
make[1]: Entering directory '/usr/src/linux-headers-6.5.0-kali3-amd64'
  CC [M]  /home/kali/Downloads/lab.o
/home/kali/Downloads/lab.c: In function ‘procfile_read’:
/home/kali/Downloads/lab.c:31:3: warning: ignoring return value of ‘copy_to_user’ declared with attribute ‘warn_unused_result’ [-Wunused-result]
   31 |   copy_to_user(buffer, msg, msg_len);
      |   ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/home/kali/Downloads/lab.o: warning: objtool: init_module(): not an indirect call target
/home/kali/Downloads/lab.o: warning: objtool: cleanup_module(): not an indirect call target
  MODPOST /home/kali/Downloads/Module.symvers
  CC [M]  /home/kali/Downloads/lab.mod.o
  LD [M]  /home/kali/Downloads/lab.ko
  BTF [M] /home/kali/Downloads/lab.ko
Skipping BTF generation for /home/kali/Downloads/lab.ko due to unavailability of vmlinux
make[1]: Leaving directory '/usr/src/linux-headers-6.5.0-kali3-amd64'
3.bash
sudo insmod lab.ko
4.''' 
lsmod | grep lab
lab                    12288  0 
'''
5.''' 
cat /proc/tsu
Hello  '''
6.'''dmesg | tail -n 1
[ 2476.224946] procfile read(1704733782): tsu
'''
7.''' sudo rmmod lab '''
8.''' dmesg | tail -n 1 '''
[ 2519.142778] Tomsk State University forever!
==== Код представляет собой модуль ядра Linux, который создает файл процедуры с именем «tsu» и регистрирует операцию чтения для этого файла. При чтении файла модуль проверяет, прошло ли с момента последнего чтения меньше или равно 20 секундам. Если это так, он возвращает 0, указывая, что операция чтения не удалась. В противном случае он записывает строку «Hello\n» в буфер, предоставленный пользователем, и возвращает длину сообщения. Модуль также инициализирует время последнего просмотра до 30 секунд перед загрузкой модуля и удаляет файл proc при выгрузке модуля.
