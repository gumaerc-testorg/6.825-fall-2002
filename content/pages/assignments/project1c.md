---
content_type: page
parent_title: Assignments
parent_uid: c614faf8-894f-e345-14ec-83a1fd01388d
title: 'Project 1, Part C:'
uid: 3c469958-5d95-4ed6-a275-c7f0f8f90d23
---

Materials
---------

*   The project [assignment]({{< baseurl >}}/resources/proj1c)
*   The Resolution-Refutation Proof Checker ([JAR]({{< baseurl >}}/resources/rrpc))
*   The project files:  
    *   sibling.txt ([TXT](/courses/electrical-engineering-and-computer-science/6-825-techniques-in-artificial-intelligence-sma-5504-fall-2002/assignments/sibling.txt))
    *   blocks.txt ([TXT](/courses/electrical-engineering-and-computer-science/6-825-techniques-in-artificial-intelligence-sma-5504-fall-2002/assignments/blocks.txt)) (fixed inconsistencies with 'on' predicate and 'clear' axiom)
    *   blocks\_extracredit.txt ([TXT](/courses/electrical-engineering-and-computer-science/6-825-techniques-in-artificial-intelligence-sma-5504-fall-2002/assignments/blocks_extracredit.txt)) ('move' axiom is different than blocks.txt version)  
         
    *   trains1.txt ([TXT](/courses/electrical-engineering-and-computer-science/6-825-techniques-in-artificial-intelligence-sma-5504-fall-2002/assignments/trains1.txt))
    *   trains2.txt ([TXT](/courses/electrical-engineering-and-computer-science/6-825-techniques-in-artificial-intelligence-sma-5504-fall-2002/assignments/trains2.txt))

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