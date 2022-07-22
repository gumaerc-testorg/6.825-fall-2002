---
content_type: page
description: ''
learning_resource_types:
- Assignments
ocw_type: CourseSection
parent_title: Assignments
parent_type: CourseSection
parent_uid: c614faf8-894f-e345-14ec-83a1fd01388d
title: 'Project 2a: Bayes Net Learning'
uid: 408cf279-83aa-78c5-8a77-818c85c4fabd
video_files:
  video_thumbnail_file: null
video_metadata:
  youtube_id: null
---

  
 

In this project, you will implement Bayes net learning. That is, you will write a program that will read in some data and come up with a Bayesian network that best matches the data. Reading and understanding Nilsson's Chapter 20, section 1 is necessary for doing this assignment.

This assignment is broken up into parts that will take you step-by-step through building a program for Bayes net learning.

Part 0: Designing the Data Structure for a Bayes Net
----------------------------------------------------

Please read through this whole assignment and make sure you understand everything you're asked to do. Then, design and implement a data structure for a Bayes net, taking into account what you'll have to do with the data structure.

*   **(Turn-in) 10 points** Describe your data structure using plain English and draw your data structure. In particular, describe where and how the links and conditional probability tables are stored in the structure.

Part 1: Estimating the CPTs
---------------------------

In this part, you are given the structure of a network and need to compute the conditional probability tables (CPTs). For this assignment, we will assume that there is no missing data, so this is just a matter of counting. For parts 1 and 2, simply use the raw counts (just as Nilsson does).

**Your Tasks:**

*   Write a procedure for computing the estimated CPTs given a network structure and data.
*   Test the correctness of your procedure using the network and data in {{% resource_link f6c8d78e-ac0b-2841-010f-b458ab1a548f "Data A" %}}. The "correct" CPTs are in the file.
*   **(Turn-in) 10 points** Compute the CPTs of the network and data in {{% resource_link 598b0c6a-944e-d12c-99e8-96a4aed65df9 "Data B" %}}.

Part 2: Computing the Score of a Network
----------------------------------------

Pretend that you have the network already defined for you. That is, you already know the network structure and the conditional probability tables. How would you know whether it is a good network? This first part is about computing the score of a given network so that you can compare different networks.

We can compute the score of a network in any way we want, but a _good scoring metric_ would take into account two things: (1) probability of the data given the network; (2) complexity of the network. For part 2, please use the scoring metric in Nilsson's chapter.

**Your Tasks:**

*   Write a procedure for computing the score of a network using the scoring metric in Nilsson's chapter.
*   Test the correctness of your procedure using the network and data {{% resource_link f6c8d78e-ac0b-2841-010f-b458ab1a548f "Data A" %}}. The "correct" score is in the file.
*   **(Turn-in) 10 points** Compute the score of the network and data in {{% resource_link 598b0c6a-944e-d12c-99e8-96a4aed65df9 "Data B" %}}. Please report both **|B|** and **m** seperately.

Part 3: Generating an Initial Network
-------------------------------------

Now you have the tools for searching through the space of network structures. However, like many other search problems, exhaustive search through the space of all possible network structures is not practical. In Part 4, you will need to implement some kind of greedy search, and as you should know by now, if you are not doing exhaustive search, your result will depend on how you choose the starting point. So in this part, you will think about how to choose an initial network. Possible candidates for an initial network are:

*   Network with no dependencies
    *   This is a network with no arrows between any nodes.
*   Fully connected network
    *   This is a network in which you randomly choose a top node (root of the tree), which has no parents, then randomly choose the next node whose parent is the root node, then choose the next node whose parents are the first two nodes, etc. In general, when a node is chosen as the next one to be added to the network, its parents are all of the nodes already chosen. If this description is not clear, please talk to one of the TAs.
*   Randomly connected network
    *   This is a network in which the nodes are randomly connected. You just need to make sure that there are no directed cycles.
*   Maximum spanning tree based on mutual information (if you do not choose to implement this one, you don't need to explain why)
    *   This is for the curious minds. If you're interested in this, come and talk to the TAs.

Note that any network you choose (here and also throughout your search) cannot have directed cycles. Also note, from this point on, you may use bayesian correction if your network has some probability 0 events.

**Your Tasks:**

*   Write two procedures that will generate an initial network (any two of the ones mentioned above)
*   **(Turn-in) 5 points** Describe how you've made sure that your network does not have any directed cycles
*   **(Turn-in) 5 points** Generate two initial network for each of the two data sets: {{% resource_link f6c8d78e-ac0b-2841-010f-b458ab1a548f "Data A" %}} and {{% resource_link 598b0c6a-944e-d12c-99e8-96a4aed65df9 "Data B" %}}. Draw the four networks and describe how you generated them.

Part 4: Searching
-----------------

Given the initial network in Part 3, implement a local greedy search to find a _locally optimal network._ (as described in Nilsson's Chapter).

**Your Tasks:**

*   Write a program to do the search. You need to define a stopping criterion so that your program does not keep searching.
*   **(Turn-in) 10 points** Explain your search algorithm well enough so that someone else can implement it (cf. Project 1a) **Note:** Please use some manner of randomization into your algorithm, either in your initialization step or in the search itself.
*   **(Turn-in) 15 points** For one initialization method, run your program 3 times each on data in {{% resource_link f6c8d78e-ac0b-2841-010f-b458ab1a548f "Data A" %}} and {{% resource_link 598b0c6a-944e-d12c-99e8-96a4aed65df9 "Data B" %}} to find a locally optimal network. Draw the resulting the networks (there should be 6) along with the CPTs. Do you get different results each time you run it? Why or why not?

Part 5: Experiment
------------------

In this part, you will do two experiments: one with Part 2, and another with either Part 3 or Part 4.

**Your Tasks:**

*   Experiment with Part 2: Try using a different scoring metric, for example, by adjusting the weighting of some of the terms. Run it on the two data sets several times and compare the two different scoring metrics you've used.
    *   **(Turn-in) 15 points** How did you change the scoring metric? What was your hypothesis about how this would affect the final networks? Draw the resulting final networks and explain the difference (if any).
*   Experiment with Part 3 or Part 4. Make a non-trivial change to your algorithm and see if you get different final networks. The changes can be in the initialization (e.g. trying another method) or in your search itself. If you decide to modify a parameter only, then do this in a systematic way; that is, try various settings of the parameter and plot the changes in some performance measure. Compare the scores of the final networks using different initial networks. Or try a different search algorithm. See if that results in a different final network. Compare the scores.
    *   **(Turn-in) 15 points** Explain your experiment. What did you do differently? What was your hypothesis about how this would affect the final networks and the score of the networks? For each condition, run it on the data three times and draw a graph comparing the two conditions. Discuss your graph.