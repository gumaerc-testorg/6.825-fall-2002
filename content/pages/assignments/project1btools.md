---
content_type: page
description: ''
learning_resource_types:
- Assignments
ocw_type: CourseSection
parent_title: Assignments
parent_type: CourseSection
parent_uid: c614faf8-894f-e345-14ec-83a1fd01388d
title: 'Project 1, Part B: Tools'
uid: 2ceb9b1b-12cd-c3aa-054d-bf4d06429f42
video_files:
  video_thumbnail_file: null
video_metadata:
  youtube_id: null
---

  
zChaff

zChaff is a very efficient implementation of the complete SAT solver, Chaff. zChaff takes sentences in CNF form and produces an assignment, if one exists.  
More information about zChaff can be found at the [zChaff homepage](http://www.princeton.edu/~chaff/zchaff.html).  
Information on the standard DIMACS CNF format can be found [here](http://logic.pdmi.ras.ru/~basolver/dimacs.html). Here is ;{{% resource_link 35c5e3dd-763e-7db5-f4bc-a0372a48c50d "one example" %}} ;of a CNF sentence in the DIMACS format, and here is ;{{% resource_link 632bd360-1f52-0e2e-fe0d-9c3f59c18b25 "another example" %}}.  
  
To get zChaff, download one of the following files:  

{{< tableopen >}}
{{< tropen >}}
{{< tdopen >}}
 
{{< tdclose >}}
{{< tdopen >}}
Instructions
{{< tdclose >}}
{{< tdopen >}}
Tested On
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
{{% resource_link 1e484279-d52d-b2d9-0a3d-6eecb49319ef "zChaff binary for Linux" %}}
{{< tdclose >}}
{{< tdopen >}}


1.  Download the gzipped file
2.  Execute: gunzip zchaff.2001.2.17.linux.gz
3.  Execute: chmod +x zchaff.2001.2.17.linux
4.  To Run: ./zchaff.2001.2.17.linux ;test1.dimacs


{{< tdclose >}}
{{< tdopen >}}
RedHat Linux 6.2, Debian GNU/Linux 2.4.9, Mandrake 8.0
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
{{% resource_link 0f4f40c0-262b-72e9-4df6-69611bca7011 "zChaff binary for Solaris" %}}
{{< tdclose >}}
{{< tdopen >}}


1.  Download the gzipped file
2.  Execute: gunzip zchaff.2001.2.17.solaris.gz
3.  Execute: chmod +x zchaff.2001.2.17.solaris
4.  To Run: ./zchaff.2001.2.17.solaris test1.dimacs


{{< tdclose >}}
{{< tdopen >}}
Athena
{{< tdclose >}}

{{< trclose >}}
{{< tropen >}}
{{< tdopen >}}
{{% resource_link 0f40483f-080d-35f3-6254-b06e7cad62ce "zChaff C++ source code" %}}
{{< tdclose >}}
{{< tdopen >}}


1.  Download the gzipped tar file
2.  Execute: gunzip zchaff.2001.2.17.src.tar.gz
3.  Execute: tar -xvf zchaff.2001.2.17.src.tar
4.  Execute: make  
    or  
    make TARGET
5.  To Run: ./asap test1.dimacs


{{< tdclose >}}
{{< tdopen >}}
Compiles and runs on Debian GNU/Linux 2.4.9 and Mandrake 8.0, but not on RedHat 6.2.  
Requires libstdc++-libc6.1-2.so.3
{{< tdclose >}}

{{< trclose >}}

{{< tableclose >}}

What remains is to turn sentences in our CNF format into DIMACS format, and to turn zChaff's assignments into Interpretations for the original sentences.  
We have written routines to do the two conversions as part of the ; techniques.PL.CNF class.  
  
Here is how you can use the routines:  

1.  In your program, convert the CNF sentence into a DIMACS-format sentence, and record the mapping of CNF variable names to DIMACS variable names:
    
    *   CNF.pl2dimacs( CnfFilenameString ); ;// creates two files: "CnfFilenameString.dimacs" and "CnfFilenameString.dimacs.map"
    *   CNF.pl2dimacs( CnfFilenameString, DimacsFilneameString ); // creates two files: "DimacsFilneameString" and "DimacsFilneameString.map"
    *   CNF.pl2dimacs( CnfSentence, DimacsFilenameString ); // creates two files: "DimacsFilneameString" and "DimacsFilneameString.map"
    
      
    
2.  At the command line (or with a system call), run zChaff on the DIMACS file  
    
    *   zchaff.2001.2.17.solaris `mysentence.dimacs >! mysentence.zchaff`
    
      
    
3.  In your program, convert the zChaff output into an Interpretation for the original CNF sentence. ;Note that the Interpretation will be `null` if zChaff did not find an assignment.
    *   Interpretation interp = CNF.zchaffToInterpretation( "mysentence.zchaff","mysentence.dimacs.map");