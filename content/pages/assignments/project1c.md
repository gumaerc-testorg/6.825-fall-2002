---
content_type: page
description: ''
learning_resource_types:
- Assignments
ocw_type: CourseSection
parent_title: Assignments
parent_type: CourseSection
parent_uid: c614faf8-894f-e345-14ec-83a1fd01388d
title: 'Project 1, Part C:'
uid: 3c469958-5d95-4ed6-a275-c7f0f8f90d23
video_files:
  video_thumbnail_file: null
video_metadata:
  youtube_id: null
---

Materials
---------

*   The project {{% resource_link 871a5e70-9225-b644-01c9-93be774ecb31 "assignment" %}}
*   The Resolution-Refutation Proof Checker ({{% resource_link 7e788295-6b81-8f7c-bb85-42a89f939295 "JAR" %}})
*   The project files:  
    *   sibling.txt ({{% resource_link 5305a82b-50bf-7fce-be16-cf26dc46d072 "TXT" %}})
    *   blocks.txt ({{% resource_link 615ae1cd-8c2e-15ee-f82f-2f53899c06c3 "TXT" %}}) (fixed inconsistencies with 'on' predicate and 'clear' axiom)
    *   blocks\_extracredit.txt ({{% resource_link 1c5eac9f-4dfd-8d5f-c2ec-e6f49826ea52 "TXT" %}}) ('move' axiom is different than blocks.txt version)  
         
    *   trains1.txt ({{% resource_link 5adda537-5cc0-3cac-41c4-7b8fedbc23c1 "TXT" %}})
    *   trains2.txt ({{% resource_link 05165be8-8f72-1d08-a648-f6338e142686 "TXT" %}})

Announcements
-------------

*   About the jarfile:
    
    *   The jarfile contains both compiled classes and source files. To use it, you can either put it in your class path and type `java RRPC.Checker`. Or, on MacOS X and Windows with JDK you can just double-click the jarfile and the checker will launch.
    
    *   If you are saving/loading the proofs as you work on them, you should be sure to **Output Proof** the proof as well as saving them. **Output Proof** will write the proof in a human-readable format.  
          
         
*   About blocks.txt:  
    
    *   The file has been updated to correct the swapped arguments in the
        
         clear
        
        axiom. (This bug should not have actually affected your ability to do the proof, but it's fixed now.)
    
    *   There were two versions of the "on" predicate: one with two arguments, and one with three. (This meant that you could not use resolution on the two different versions. However, it really didn't cause any problems because you did not need to do resolution across the two different versions to do the proof.) This has now been corrected.
    *   The extra credit version, blocks\_extracredit.txt, has only one version of "on": the three argument version. It also contains a different version of the "move" axiom, with an additional predicate.  
         

What to Turn In
---------------

*   Your proofs, using the **Output Proof** command  
     
*   For each proof, please also:
    *   Provide a brief (not more than a paragraph) proof sketch
    *   Point out any key resolution steps in your proof  
          
         
*   For the extra credit, in addition the proof, explain why the solution depends on having an axiom that explicitly mentions
    
     clear(x)
    
    after moving
    
     x
    
    (even though the solution to question 3 didn't depend on such a thing).
    *   Correction: don't worry about justifying the 3-argument version of the "on" predicate.