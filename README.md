Write an expert-system in propositional calculus (aka propositional logic).
An expert-system is a type of AI program that can reason on a set of rules and initial facts to deduce other facts. It at least consists of a UI, inference engine and knowledge base. The knowledge base consists of facts and rules, added by an expert, forming the knowledge of the system. While the inference engine is the algorithm that uses those rules to deduce answers to questions received from the UI. Those rules and deductions are often described using if-then statements.
Propositional calculus is simply the formal basis of logic dealing with the notion and usage of words such as "NOT," "OR," "AND," and "implies". The expert-system uses this convention for its rules and inferences.

Inference engines can use two strategies, namely forward- and backward-chaining.
With forward-chaining we first look at the underlying facts and rules to deduce the outcome. While with backward-chaining we first look at the outcome and its rules to deduce the underlying facts.
In this project we have to implement backward-chaining. Here is an example of how it works.

Outcome (given as input): He is sweating.
Associated rule (found in knowledge base): If he is running, he sweats.
Underlying fact (deducted by inference engine): He is running.
Workings
Here is an example of an input file. The input file represents the knowledge base (facts and rules) and UI (queries).

# this is a comment
# input file created from this backward-chaining video example (https://www.youtube.com/watch?v=6DU42so8k48)

F + B -> Z        # F and B implies Z
C + D -> F        # C and D implies F
A     -> D        # A implies D

=AEBC             # Initial facts : A, E, B and C are true. All others are false.

?Z                # Queries: Is Z true or false?
For this input file the backward-chaining algorithm would work like this:

Find the value of Z
Check if part of initial facts else find the Z rule(s). (F + B -> Z)
To decipher this rule find the F value.
Check if part of initial facts else find the F rule(s). (C + D -> F)
To decipher this rule find C value.
Check if part of initial facts. (=AEBC)
Now we know C is true because it is part of initial facts.
To decipher this rule find D value. (C(true) + D -> F)
Check if part of initial facts else find the D rule(s). (A -> D)
To decipher this rule find A value.
Check if part of initial facts. (=AEBC)
Now we know A is true because it is part of initial facts.
Now we know D is true. (A(true) -> D)
Now we know F is true. (C(true) + D(true) -> F)
To decipher this rule find the B value. (F(true) + B -> Z)
Check if part of initial facts. (=AEBC)
Now we know B is true because it is part of initial facts.
Now we know Z is true. (F(true) + B(true) -> Z)
Use
python3.7 expert-system.py <flags(optional)> <input file>
python3.7 expert-system.py tests/simple1.txt
python3.7 expert-system.py -v tests/complex.txt # verbose, see explanations
python3.7 expert-system.py -d tests/simple2.txt # debug, stop algo at specific point# educationalexpertsystem
