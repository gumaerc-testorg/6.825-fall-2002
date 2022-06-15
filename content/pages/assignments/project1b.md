---
content_type: page
description: ''
learning_resource_types:
- Assignments
ocw_type: CourseSection
parent_title: Assignments
parent_type: CourseSection
parent_uid: c614faf8-894f-e345-14ec-83a1fd01388d
title: 'Project 1, Part B:'
uid: ebf98cb3-3298-dfb0-6d26-ba2fb62c122a
video_files:
  video_thumbnail_file: null
video_metadata:
  youtube_id: null
---

  
 

Materials
---------

*   The project assignment ({{% resource_link 1ecafc6d-65b0-4033-d949-b3a80bbf68f3 "PDF" %}})
*   Code and binaries ({{% resource_link 5c0ef00f-c486-4af9-afef-7578011eeade "JAR" %}}) _(updated 10/13)_
*   [Documentation](/ans7870/6/6.825/assignments/project1b/javadocs/index.html) for the code
*   {{% resource_link 2ceb9b1b-12cd-c3aa-054d-bf4d06429f42 "Information" %}} about a very efficient SAT solver called zChaff. If you like, you can also work with zChaff.

Notes
-----

_(10/3)_ A new JAR file has been posted. The only difference is that it includes a class

techniques.solvers.DPLL

that you can use as your SAT solver (though you are encouraged to use your own from part a). This jarfile supercedes the previous one and you should _remove_

PL.jar

from your

CLASSPATH

.

_(10/2)_ Converting from a first-order logic sentence to our FOL grammar (clarification of Figure 3)

*   **first-order logic:** Ax, y. foo(x) -> bar(y) v Ez. ~equals(x,z)
*   **our FOL grammar format:**
    
    all x all y foo(x) -> bar(y) v exists z ~Equals(x,z)
    

Important Clarifications:

1.  Any time you provide a printout of an assignment, also include a description of it in English (or a with diagram, or something).
2.  If a question asks you to provide an assignment, you do not need to provide \_all\_ assignments. One will do.
3.  For items 11 and 12, we mean the following:
    *   you should create an axiom that defines what it means to be a well-connected set of rails (i.e., that it's possible to move from each rail to each other rail)
    *   then, having asserted well-connectedness, list the actual assignment returned for the "connects" relation: this relation represents the track layout found by your SAT solver.  
          
         
4.  There is a typo in item 13. the definition of liveness from "formula 8" refers to your revised definition of 'deadlock' from question \_10\_.
5.  Yes, the extra credit is worth actual points on 1b, just as it was on 1a. (note that an "extra credit" problem is distinct from a "bonus challenge!")
6.  Yes, please form a group of two (if you like) for this assignment, as well. you can work with the same partner for 3 of the 5 projects.

Answers to Some Common Questions:

1.  "Deadlocked" refers to the whole situation: a situation is deadlocked if both trains _can not_ move. If at least one train has a move available, then we do not consider that situation to be deadlocked.  
     
2.  Your solution to the deadlock questions cannot involve:
    
    *   changing the non-determinism of the world dynamics. a question was asked if it was ok for each train to have a plan of action, and to broadcast that plan. that makes the dynamics deterministic, and it would mean the other trains would know what to avoid. this is not really the spirit of the question, since it's not allowable to have...
    *   knowledge about the next situation (i.e. "peeking" into the future). your solutions must involve only what is known about the \_current\_ situation. try to think about whether an additional relation on the trains would "break symmetry" in a way that avoids deadlock.
    *   removing the "Safe"ness of the situations S1 and S2.  
          
         
    
      
     
3.  Running out of memory:
    
    you may have gotten "out of memory" errors during the process of changing the FOL sentence into a CNF sentence. this is not a bug in the code, and it's probably not the 'fault' of any individual axiom in your FOL sentence. it's just the nature of exponential growth: converting a sentence from FOL to PL and then to CNF grows exponentially bad with the number of propositions. exponential growth is bad news; if you didn't believe that before, you should now!
    
    that said, it \_is\_ possible to do the assignment within the standard memory constraints of the JVM (128 MB). if you are running out of memory, try looking at the following things in your set of axioms:
    
    *   do you have any axioms that are redundant, or duplicating the work of other axioms? some people made their definition of "legal" to do the work of both "legal" and of enforcing the world dynamics. a little parsimony goes a long way.
    *   do you have statements that say something like "all s" when simply instantiating the statement for S1 would do?
    *   do you have any axioms left over from previous questions in the assignment that are no longer needed?  
          
         there is really no guaranteed method for avoiding memory problems; if you have trouble with it, you'll just need to play around with your sentences until they get small enough.

What to Turn In:
----------------

Please note that the axioms you come up with should assume as little as possible about the arrangement of rails or number of trains; they should be generally applicable to any world with any number of trains and rails. One of the grading criteria will be the generality of your axioms.

1.  \- the formulas 1-6, in the language of figure 3 (hereafter denoted as 'homework language').  
     
2.  \- the two new axioms, in the homework language.  
     
3.  \- a printout of the found satisfying assignment.  
    \- in english, a description of the assignment, including the locations of the trains in S1 and S2.  
     
4.  \- how you used DPLL to show no crashes (a description of your method)  
    \- why or why not to use WalkSAT  
     
5.  \- the new definition of "legal" in homework language  
    \- an English or standard FOL description of your new definition  
    \- any changes to the connects relation?  
    \- whether the domain is still safe  
    \- how you used DPLL to show safeness (a description of your method)  
     
6.  \- homework language description of layout 2  
    \- how would you show it is not safe? (describe your method)  
    \- printout demonstrating safeness (either an assignment, or that your procedure returned 'null' for no assignment)  
     
7.  \- the new definition of "legal" in the homework language  
    \- an English or standard FOL description of your new definition  
    \- whether the domain is still safe  
    \- a description of your method for showing that it was still safe  
    \- a safe configuration you found (or more, if you found more than one) for S1 and S2  
     
8.  \- the axiom, in homework language and English/FOL, that asserts that S1 is deadlocked.  
    \- a description of your method for showing no deadlock in layout 1  
     
9.  \- a description of your method for showing deadlock in layout2  
    \- the members of the ON relation, if your proof method produced an assignment  
    \- a printout of the assignment, if you have one  
     
10.  \- the new axiom for legal (in homework language, and English or FOL)  
    \- any new axioms or relations that you added  
    \- a printout of the assignment for the given arrangement  
     
11.  no actual programming is required here. just think about it, and write about what you \_would\_ do to axiomatize, in FOL, the notion of "eventually moving". then, write about whether the approach of this assignment (i.e. of turning an FOL sentence into a propositional one) would work for proving/disproving the correctness of that condition.  
     
12.  the words "second implication" are a typo: there is only one implication in formula 5. (the formula describing the dynamics.)