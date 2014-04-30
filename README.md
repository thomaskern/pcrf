pcrf
====

Python Linear CRF


= Introduction =

PCRF is a open source implementation of (Linear) Conditional Random Fields (CRFs) for segmenting/labeling sequential data. PCRF is implemented in Python (2.7.5) and can be applied to a variety of NLP tasks, such as Named Entity Recognition, Information Extraction , chinese word segmentation and Event Extraction.


== Features ==

# Implemented in python, numpy, scipy. 100% python.
# Fast training based on LBFGS( a quasi-newton algorithm for large scale numerical optimization problem)
# Less memory usage in training, can handle tens of millions features.
# decoding in practical time
# Available as an open source software
# Train file format and Feature template are compatible with popular CRF implementations, like CRF++
# Multiprocessing
# optimized for less energy consumption and CO2 emission. (can ran half the speed as CRF++)

== Versions ==

# pcrf ver 0.1.  released 2014-03-01. Initial Release

==  Download (Check out) ==


Github:

https://github.com/huangzhengsjtu/pcrf/

=  Train file format and Feature template =

Compatible with CRF++. http://crfpp.googlecode.com/svn/trunk/doc/index.html#format

=  Examples =

== a simple example==

The training , testing and template file come with pcrf codes.

using pcrf to Learn the model:

  c:\> python pcrf-train.py trainsimple.data templatesimple.txt model  

using pcrf to test:

  c:\> python pcrf-test.py trainsimple.data model result.txt

You are expecting to get a 100% correct rate.

== chunk example==

The training data is from CRF++. 

using pcrf to Learn the model:

  c:\> python pcrf-train.py trainchunk.data templatechunk model  

trainchunk.data is the training data. templatechunk is the template file to generate features. model is the learnt model file (which stores all the <math>\theta</math>. ). After the Train process finished, you will get the model file. On an intel core i3 machine, it takes around 400 seconds to finish. 

  Valid Template Line Number: 20
  read  10000  lines.
  number of labels: 17
  Linear CRF in Python.. ver 0.1
  B features: 289 U features: 1075420 total num: 1075709
  training sequence number: 823
  RUNNING THE L-BFGS-B CODE
  At iterate    0    f=  5.92173D+05    |proj g|=  3.40110D+03
  .....
  At iterate   61    f=  1.14233D+03    |proj g|=  6.15748D-01
  At iterate   62    f=  1.14213D+03    |proj g|=  9.20878D-01
     N    Tit     Tnf  Tnint  Skip  Nact     Projg        F
  *****     62     72      1     0     0   9.209D-01   1.142D+03
    F =   1142.13417137736

using pcrf to test:

  c:\> python pcrf-test.py testchunk.data model result.txt


  number of labels: 14
  Linear CRF in Python.. ver 0.1
  B features: 289 U features: 1075420 total num: 1075709
  Prediction sequence number: 77
  Note: If Y is useless, correct rate is also useless.
  correct: 1757 error: 139  correct rate: 0.926687763713
  Write max(y) to file: results.txt
  Test finished in  1.68699979782 seconds.

testchunk.data is the testing data. model is the learnt model file in training. After the test process finished, you will get the result file. Test program also output a very simple correct ratio to check whether the CRF model works.

== experiment 2 ==


= Notes and Bugs =
# On Windows system, sometime the training program can't start. Check if there is a iterate.dat file that is locked by other python process. Kill the idle python process, it should work. iterate.dat is generated by LBFGS module from scipy.optimize.

= To do =
# extended to general CRF.
# using BP to train and learn CRF.
# Learn the structure of CRF.
