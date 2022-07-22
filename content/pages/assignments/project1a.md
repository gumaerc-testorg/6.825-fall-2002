---
content_type: page
description: ''
learning_resource_types:
- Assignments
ocw_type: CourseSection
parent_title: Assignments
parent_type: CourseSection
parent_uid: c614faf8-894f-e345-14ec-83a1fd01388d
title: 'Project 1, Part A: (I Can''t Get No) Satisfaction'
uid: d2af9fa9-a13b-5132-69cd-1ec133252f4b
video_files:
  video_thumbnail_file: null
video_metadata:
  youtube_id: null
---

  
 

One major challenge in logic-based AI is the difficulty of solving the satisfiability problem (usually referred to as SAT). For this assignment, we will ask you to implement two different SAT solvers, commonly known as DPLL and WALKSAT, run your solvers on some test programs, and analyze the performance of the algorithms.

SAT Instances
-------------

SAT instances are simply statements in propositional logic, written in conjunctive normal form (CNF). CNF sentences consist of _variables_, _literals_, and _clauses_. In the grammar for this assignment, a variable is a single, case-sensitive character (e.g. "Q") and a literal is a variable or its negation ("Q" or "~Q"). In a CNF sentence, a clause consists of a disjunction of literals ("Z v ~B v X"). A sentence is a conjunction of clauses, for example:

(A v C v ~B) ^ (Z) ^ (~E v X v Y v W)

A _satisfying assignment_ to a SAT instance is an assignment of truth values to variables that makes the CNF sentence true. If such assignment exists for a SAT instance, we say that the SAT instance is _satisfiable_. The problem of determining whether or not a particular SAT instance is satisfiable is NP-complete and thus cannot generally be solved efficiently. For a sentence of _n_ variables, it will take O(2_{{< sup "n" >}}_) operations to discover an assignment in the worst case - equivalent to checking every possible assignment. Many interesting AI problems are NP-complete or harder, which leads us to consider approximate methods of solution, or exact methods that have good average case running times.

**Reading: _Russell & Norvig, Chapters 4,6 (Search, Propositional Logic)_**

The Code
--------

We will be providing some handy Java{{< sup "®" >}} classes that you can use for this assignment. We have tested it with the Java 1.3 JVM, though it should work on any Java 2 JVM (Java 1.2 and higher). We will be distributing compiled classes and source file packaged as a JAR (Java ARchive) file, as well as posting the Javadoc documentation for the classes. You should not need to look at the source to use the classes, but you can expand the jar file if you need it.

The jar file for this assignment is {{% resource_link 647260b1-82bc-d7e3-2675-f6bedc73b241 "PL.jar" %}}, which contains a package for parsing and representing sentences of propositional logic in CNF. The [documentation](/ans7870/6/6.825/assignments/project1a/javadocs/index.html) for these classes is also available. You will need to include this JAR file in your CLASSPATH, and you will probably want to import the package with the statement import techniques.PL.\*; before the class definitions.

To parse a String or a File, use the parse methods of [techniques.PL.CNF](/ans7870/6/6.825/assignments/project1a/javadocs/techniques/PL/CNF.html). The parser will only parse CNF sentences, so be sure you are entering them correctly.

To generate a random 3-SAT instance, you can either call [CNF.randInstance()](/ans7870/6/6.825/assignments/project1a/javadocs/techniques/PL/CNF.html#randInstance(int)) or use the [CNF.main()](/ans7870/6/6.825/assignments/project1a/javadocs/techniques/PL/CNF.html#main(java.lang.String[])) method via the command-line.

If you are new to Java, it might be useful to look at the {{% resource_link e081a1e5-8ef8-3815-c311-14cb201a8a70 "Java® Resources" %}} page before you get too involved with your coding. You are, of course, free to use another programming language. If you are not using Java, you will need to create a your own internal representation for a CNF boolean sentence. You will need to parse the CNF sentences given in our format, as well as create a CNF sentence generator for the experiment detailed below.

Tasks
-----

*   You are to try two algorithms (explained in the next section) on the SAT problem. Input to the algorithms should be given as a CNF sentence. Output should be the satisfying assignment, if one is found; if none is found, output an empty assignment. An assignment is a mapping from propositional variables to boolean values.
    1.  **(Optional) Brute Force**: You may want to try implementing a brute force (exhaustive search through the solution space) algorithm before DPLL and WalkSAT. This is just so you have something that works and can check your answers from the other two algorithms. You do not need to write up anything for this.
    2.  **DPLL**: Implement the DPLL algorithm.
    3.  **WalkSAT**: Implement the WalkSAT algorithm.
*   Run your algorithms on the test cases below.
*   Using the random CNF generator given in the PL.jar code, run your algorithms on random CNF sentences of varying length and measure the speed of the two algorithms.

For this assignment, we present the following SAT instances in text files. Your code should be able to solve these in reasonable time.

**Debugging Cases:**

*   {{% resource_link 04fd66ae-e8d3-b8b4-f359-22915998cfeb "A simple satisfiable sentence" %}}
*   {{% resource_link 968d655b-b3e5-61a9-6f37-c80b44763dc7 "A slightly more complicated satisfiable sentence" %}}
*   {{% resource_link 0f00f1c8-c651-0c1e-1fcf-4e4703a4687f "A simple unsatisfiable sentence" %}}
*   {{% resource_link abbfb675-0d76-d136-b66e-5b1086f7a866 "A slightly more complicated unsatisfiable sentence" %}}
*   {{% resource_link 2271d9f9-b391-8bcf-eaf4-3c534296e1b5 "A solveable CNF" %}} (Your code should solve this in three minutes or less. Otherwise you need to revise your code)
*   {{% resource_link de8f55f7-e551-f0c0-7f86-6ec20a815410 "Solution to the solveable CNF" %}}

**Test Cases:**

*   {{% resource_link d5cbf5d4-b65d-c8ad-84d9-7e913fca250b "test 1" %}}
*   {{% resource_link b8e84d0d-5fde-83e6-f908-5fd6ae483eac "test 2" %}}
*   {{% resource_link c50ed476-d7eb-50c2-75cd-54439b4065ea "test 3" %}}
*   {{% resource_link e8716647-e336-69ab-4b9d-a0e27dcd4aa5 "test 4" %}}
*   {{% resource_link f36eedcc-fa82-5871-9f2d-fdce698d12b8 "test 5" %}}

Algorithms
----------

> ### Davis, Putnam, Logemann and Loveland (DPLL)
> 
> This algorithm is popularly known as DPLL and is one of the most widely used methods of solving satisfiability problems exactly. By "exactly" we mean that DPLL is guaranteed either to find a satisfying assignment if one exists or terminate and report that none exists. Therefore, it still runs in exponential time in the worse case.
> 
> **Reading: _Cook and Mitchell, "Finding Hard Instances of the Satisfiability Problem: A Survey."_**
> 
> The crucial sections of this paper are 1-2.1, which explain notation and the DPLL algorithm. Also read Section 3 closely, it discusses the mathematical properties that distinguish hard SAT problems from easy ones.
> 
> ### GSAT & WALKSAT
> 
> GSAT and WALKSAT are stochastic algorithms. In order to speed up the search for a true assignment, they pick random locations in the space of possible assignments and make limited, local searches from those locations. As a result, they might be able to find a solution to a problem that would take too long to solve using DPLL's complete, global search. But because they do not cover the entire search space, there is no guarantee that GSAT or WALKSAT will find a solution to every problem, even if one exists. Therefore, these algorithms can never determine if a sentence is unsatisfiable. Algorithms are frequently categorized as _sound_ or _complete_. A sound algorithm guarantees that any answer it returns is correct, but does not necessarily return an answer to every problem. A complete algorithm, on the other hand, will always return an answer. DPLL is complete and sound, while GSAT and WALKSAT are sound, but not complete.
> 
> **Optional Reading: _Selman and Kautz, "Domain-Independent Extensions to GSAT: Solving Large Structured Satisfiability Problems."_**
> 
> **Optional Reading: _Selman, Kautz, and Cohen, "Local Search Strategies for Satisfiability Testing."_**
> 
> The WALKSAT algorithm evolved from the GSAT algorithm. The first paper has an early exploration of some extensions to GSAT, including "GSAT with Random Walk." The second paper has the actual WALKSAT algorithm, and a brief explanation of its development.

The Write-up
------------

*   For each algorithm, turn in the following:
    
    1.  A description of your algorithm (not code!) with enough details that others could replicate your results. Include how and why you made any choices (e.g., values you chose for parameters) you made. (**Suggested Length**: 1 - 2 pages for each algorithm)
    2.  Give a satisfying assignment (if one exists) for the Test cases.
    3.  Produce a graph charting solution times vs. clause/variable ratio (for a given number of variables) for each of those algorithms. Graph each up to the ratio at which the puzzles become impractical. Average the results from at least 5 trials at each size. The PL.jar code contains a generator of random CNF sentences. The generator will create sentences with the desired ratio for a fixed number of variables. As coded, the number of possible variables is 26.
    4.  Discuss your results, explaining carefully why you think they came out as they did. Talk about the characteristics of each algorithm, and compare the two algorithms to explain any differences in the results. (**Suggested Length**: 2 - 3 pages.)
    5.  **Extras**: For extra credit: Try making DPLL as fast as possible. try making DPLL and/or WalkSAT solve more problems by varying your algorithms. Show experimentally how your changes have helped you solve larger problems.
    
    **Note:**
    *   In all parts of this homework, "impractical" means "takes more than 5 minutes to solve."
    *   "Speed" should be measured in a machine-independent way. When we collect results, we will ask you to report the number of assignments to the variables your algorithm had to check before solving the problem.
*   **Bonus Challenge:**Who couldn't get no satisfaction?

Collaboration Policy
--------------------

You may work in teams of two, handing in a single write-up.

Handing in the Assignment
-------------------------

*   Hand in answers to the questions and all graphs.
*   **Do NOT hand in any code listings.**
*   **Staple all materials together.**