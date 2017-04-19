
OS VERSION
----------

```
$ cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu

```


```
$ uname -a
Linux eee320 3.13.0-88-generic #135-Ubuntu SMP Wed Jun 8 21:10:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```


DEPENDENCIES ERRORS
-------------------


### Gnu Scientific Library libgsl0ldbl libgsl0-dev

```
map479-admin@eee320:~/hmm/gart/gt2k-0.1a/tools/data_generator$ make
gcc gen_data.c -lgsl -lgslcblas -lm -o gen_data
gen_data.c:27:29: fatal error: gsl/gsl_randist.h: No such file or directory
 #include <gsl/gsl_randist.h>
                             ^
compilation terminated.
```

SOLUTION
```
sudo apt-get install libgsl0ldbl libgsl0-dev
```
http://ubuntuforums.org/showthread.php?t=1059081


ALTERNATIVE SOLUTION (NOT TESTED)
Install and use GNU GSL library in Ubuntu 14.04 (Linux, C++) https://www.youtube.com/watch?v=JrvnJaj7Ogk
Downloading GSL ftp://ftp.gnu.org/gnu/gsl/

### flex

```
map479-admin@eee320:~/hmm/gart/gt2k-0.1a/tools/hv$ make
g++ -c -Wall -O2 -g -pedantic -D_REENTRANT -I/usr/local/include -I/usr/include  -o htk2dot.o htk2dot.c
g++ -Wall -O2 -g -pedantic -D_REENTRANT -I/usr/local/include -I/usr/include  htk2dot.o -o htk2dot -L/usr/lib -lm -lpthread -lfl
/usr/bin/ld: cannot find -lfl
collect2: error: ld returned 1 exit status
make: *** [htk2dot] Error 1
```

SOLUTION
```
sudo apt-get install flex
```

### ksh

```
@eee320:~/hmm/gart/gt2k-0.1a/tools/hv$ ./hv.sh topology
bash: ./hv.sh: /bin/ksh: bad interpreter: No such file or directory
```


SOLUTION
```
sudo apt-get install ksh
```

### which gv to which evince

```
map479-admin@eee320:~/hmm/gart/gt2k-0.1a/tools/hv$ ./hv.sh topology
Reading data from topology
Checking system for necessary software

ERROR: gv not found in /opt/ros/indigo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games.
please add gv to your path or install it if it is not on your
system
```


in hv.sh CHANGE
```
GV=`which gv`

to

GV=`which evince`
```






# INSTALLATION


on Makefile:

# install HTK (1) or don't (0)
INSTALL_HTK=0



On terminal:


```
$ make
if [ 0 == 1 ]; then ./install-htk.sh ./HTK-3.2.tar.gz /usr/local/bin; fi
/bin/sh: 1: [: 0: unexpected operator
make -C utils
make[1]: Entering directory `/home/map479-admin/hmm/gart/gt2k-0.1a/utils'
g++ -O3 random.cc -o random -lm
random.cc: In function ‘int main(int, char**)’:
random.cc:66:35: warning: ignoring return value of ‘char* fgets(char*, int, FILE*)’, declared with attribute warn_unused_result [-Wunused-result]
      fgets(line, LINESIZE, elFile);
                                   ^
g++ -O3 htk-prep-amin.c -o htk-prep -lm
htk-prep-amin.c: In function ‘int main(int, char**)’:
htk-prep-amin.c:179:35: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result [-Wunused-result]
   fscanf(timefile, "%ld\n", &time);
                                   ^
htk-prep-amin.c:197:64: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result [-Wunused-result]
     &data[number_of_samples][16], &data[number_of_samples][17]);                                      
                                                                ^
htk-prep-amin.c:238:35: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
   write(binout, &nos, sizeof(int));// write the number of examples to the bin file
                                   ^
htk-prep-amin.c:239:34: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
   write(binout, &sp, sizeof(int));  // write the period of the sample to the bin file
                                  ^
htk-prep-amin.c:240:35: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
   write(binout, &s, sizeof(short)); // write the vector length to file
                                   ^
htk-prep-amin.c:241:35: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
   write(binout, &t, sizeof(short)); // write the type of file. In this case, user type == 9
                                   ^
htk-prep-amin.c:253:43: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
       write(tempBin, &temp, sizeof(float));
                                           ^
htk-prep-amin.c:255:46: warning: ignoring return value of ‘ssize_t read(int, void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
       read(tempBin, &temp2[0], sizeof(short));
                                              ^
htk-prep-amin.c:256:46: warning: ignoring return value of ‘ssize_t read(int, void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
       read(tempBin, &temp2[1], sizeof(short));
                                              ^
htk-prep-amin.c:263:46: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
       write(binout, &temp2[1], sizeof(short));
                                              ^
htk-prep-amin.c:264:46: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
       write(binout, &temp2[0], sizeof(short));
                                              ^
g++ htkhelper.cc -c -I.
htkhelper.cc: In member function ‘int RawImgData::WriteImgData(unsigned int, unsigned int, unsigned int)’:
htkhelper.cc:391:78: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘std::deque<float*>::size_type {aka long unsigned int}’ [-Wformat=]
     fprintf(stderr,"wrong number of examples in gesture:%d\n",writebuf.size());
                                                                              ^
g++ standalone_prepare.c htkhelper.o -o prepare
make[1]: Leaving directory `/home/map479-admin/hmm/gart/gt2k-0.1a/utils'

```




```
map479-admin@eee320:~/hmm/gart/gt2k-0.1a$ sudo make install
[sudo] password for map479-admin:
cp -r tools /usr/local/gt2k
cp -r template /usr/local/gt2k
cp -r tutorials /usr/local/gt2k
cp -r examples /usr/local/gt2k
cp -r LICENSE /usr/local/gt2k
cp -r README /usr/local/gt2k
cp -r PublicUse.doc /usr/local/gt2k
cp -r PublicUse.txt /usr/local/gt2k
cd utils/; make "INST_DIR=/usr/local/gt2k/utils" install
make[1]: Entering directory `/home/map479-admin/hmm/gart/gt2k-0.1a/utils'
install -D -b prepare /usr/local/gt2k/utils/prepare
install -D -b create_grammar.pl /usr/local/gt2k/utils/create_grammar.pl
install -D -b random /usr/local/gt2k/utils/random
install -D -b check_opts.sh /usr/local/gt2k/utils/check_opts.sh
install -D -b htk-prep /usr/local/gt2k/utils/htk-prep
install -D -b recognize.sh /usr/local/gt2k/utils/recognize.sh
install -D -b train.sh /usr/local/gt2k/utils/train.sh
install -D -b new_project.sh /usr/local/gt2k/utils/new_project.sh
make[1]: Leaving directory `/home/map479-admin/hmm/gart/gt2k-0.1a/utils'
```
