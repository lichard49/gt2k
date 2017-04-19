Georgia Tech Gesture Toolkit
---------
The Georgia Tech Gesture Toolkit (GT 2 k) provides a
publicly available toolkit for developing gesture–based recognition systems.
http://gt2k.cc.gatech.edu/
https://wiki.cc.gatech.edu/ccg/projects/gt2k/gt2k

Used in July 2016



# Download
Download the older version (shell script version) here: [gt2k-0.1a.tar.gz](https://wiki.cc.gatech.edu/ccg/_media/projects/gt2k/gt2k-0.1a.tar.gz?id=projects%3Agt2k%3Agt2k&cache=cachehttps://wiki.cc.gatech.edu/ccg/_media/projects/gt2k/gt2k-0.1a.tar.gz?id=projects%3Agt2k%3Agt2k&cache=cache)


Uncompress the toolkit
```
tar -xvf gt2k-0.1a.tar.gz
```

# TODO
* Find the FATAL ERROR - Terminating program HRest when running examples

# Usage

Before executing the hv.sh script be sure that "make" is typed in the directory
containing the source to build htk2dot.  Make sure this file is in the same
directory containing the script as the script will not work without it.



## CREATING THE TOPOLOGY

```
cd ~/gt2k-0.1a/tools/hv
chmod +x hv.sh
```

CHANGE (LINE 74) in hv.sh
```
GV=`which gv`
to
GV=`which evince`
```


```
cd ~/gt2k-0.1a/tools/hmm_generator
./gen_hmmdef.pl -n5 -v4 -s0 topology
```


to visualize HMM definition file <hmmfile> simple execute the script
./hv.sh <hmmfile>

```
cd ~/gt2k-0.1a/tools/hv
cp /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/tools/hmm_generator/topology .
./hv.sh topology
```



# TUTORIAL gestpan

```
$ pwd
$ ~gt2k-0.1a/tutorials/gestpan
$ find data/* -type d > datadirs
$ find data/* -type f > datafiles

$ scripts/gen_commands.sh datadirs > commands
or
$/usr/local/gt2k/utils//usr/local/gt2k/utils/gen_commands.sh datadirs > commands
```


```
~/gart/gt2k-0.1a/tools/hmm_generator$ ./gen_hmmdef.pl -n8 -v72 -s0 my_model
~/gart/gt2k-0.1a/tutorials/gestpan/hmmdefs$ cp /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/tools/hmm_generator/my_model .
```

```
~/gart/gt2k-0.1a/tutorials/gestpan$ scripts/gen_mlf.sh datafiles ext > labels.mlf
```

```
Set PRJ to match the path to your main project directory.
[line 18]#PRJ=`pwd`					# path to the current project
PRJ=`/home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/tutorials/gestpan`


/usr/local/gt2k/utils/train.sh scripts/options.sh

 2>&1 > out.log & tail -f out.log
```



# Using Latest Version of HMM

TRYING RUN THE EXAMPLES USING THE LATEST VERSION of HTK. so I have to modify the bashrc
```
export PATH=/home/map479-admin/htk_source/htk/HTKTools:/home/map479-admin/htk_source/htk/HLMTools:$PATH
```

```
sudo scripts/train.sh scripts/options.sh
```
```
*****************************************************
Building Models
*****************************************************
HCompV -A -T 1 -S /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/trainsets/training-extfiles0 -l bunny -I /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/labels.mlf -o bunny -m -M /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/models/hmm0.0 /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/hmmdefs/8state-noskip-72vec
  ERROR [+6551]  LoadMasterFile: MLF file header is missing
 FATAL ERROR - Terminating program HCompV


@ scripts/gen_mlf.sh
replace
echo "#!MLF!# \n"			# write the header for the file
to
echo "#!MLF!#"			# write the header for the file


scripts/gen_mlf.sh datafiles ext > labels.mlf
```



# Errors while buidling models



```
~/gt2k-0.1a/examples/gestpan$ sudo scripts/train.sh scripts/options.sh
```

```
*****************************************************
Building Models
*****************************************************
HCompV -A -T 1 -S /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/trainsets/training-extfiles0 -l bunny -I /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/labels.mlf -o bunny -m -M /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/models/hmm0.0 /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/hmmdefs/8state-noskip-72vec
Calculating Fixed Variance
  HMM Prototype: /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/hmmdefs/8state-noskip-72vec
  Segment Label: bunny
  Num Streams  : 1
  UpdatingMeans: Yes
  Target Direct: /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/models/hmm0.0
*** stack smashing detected ***: HCompV terminated
scripts/train.sh: line 220: 1076: Abort(coredump)
HInit -A -T 1 -M /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/models/hmm0.1 -l bunny -S /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/trainsets/training-extfiles0 -I /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/labels.mlf -o bunny /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/models/hmm0.0/bunny
  ERROR [+5010]  InitSource: Cannot open source file /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/models/hmm0.0/bunny
  ERROR [+7010]  LoadHMMSet: Can't find file
  ERROR [+2128]  Initialise: LoadHMMSet failed
 FATAL ERROR - Terminating program HInit
HRest -A -m 1 -T 1 -t -i 30 -v 0.001 -l bunny -M /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/models/hmm0.2/ -S /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/trainsets/training-extfiles0 -I /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/labels.mlf /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/models/hmm0.1/bunny
  ERROR [+5010]  InitSource: Cannot open source file /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/gestpan/models/hmm0.1/bunny
  ERROR [+7010]  LoadHMMSet: Can't find file
  ERROR [+2128]  Initialise1: LoadHMMSet failed
 FATAL ERROR - Terminating program HRest

```






```
~/gart/gt2k-0.1a/examples/acceleglove$ sudo scripts/train.sh scripts/options.sh
```


```
HCompV -A -T 1 -S /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/trainsets/training-extfiles0 -l start_sentence -I /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/labels.mlf -o start_sentence -m -M /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/models/hmm0.0 /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/hmmdefs/4state-1skip-17vec
Calculating Fixed Variance
  HMM Prototype: /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/hmmdefs/4state-1skip-17vec
  Segment Label: start_sentence
  Num Streams  : 1
  UpdatingMeans: Yes
  Target Direct: /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/models/hmm0.0
  ERROR [+6510]  LOpen: Unable to open label file /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/ext/data/377.TXT.lab
 FATAL ERROR - Terminating program HCompV
HInit -A -T 1 -M /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/models/hmm0.1 -l start_sentence -S /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/trainsets/training-extfiles0 -I /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/labels.mlf -o start_sentence /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/models/hmm0.0/start_sentence
  ERROR [+5010]  InitSource: Cannot open source file /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/models/hmm0.0/start_sentence
  ERROR [+7010]  LoadHMMSet: Can't find file
  ERROR [+2128]  Initialise: LoadHMMSet failed
 FATAL ERROR - Terminating program HInit
HRest -A -m 1 -T 1 -t -i 30 -v 0.001 -l start_sentence -M /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/models/hmm0.2/ -S /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/trainsets/training-extfiles0 -I /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/labels.mlf /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/models/hmm0.1/start_sentence
  ERROR [+5010]  InitSource: Cannot open source file /home/map479-admin/mxochicale_eee320/hmm/gart/gt2k-0.1a/examples/acceleglove/models/hmm0.1/start_sentence
  ERROR [+7010]  LoadHMMSet: Can't find file
  ERROR [+2128]  Initialise1: LoadHMMSet failed
 FATAL ERROR - Terminating program HRest
```
