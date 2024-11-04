# Ex.No: 11  Planning –  Block World Problem                                                         
### REGISTER NUMBER : 212222040086
### AIM: 
To find the sequence of plan for Block word problem using PDDL  
###  Algorithm:
Step 1 :  Start the program <br>
Step 2 : Create a domain for Block world Problem <br>
Step 3 :  Create a domain by specifying predicates clear, on table, on, arm-empty, holding. <br>
Step 4 : Specify the actions pickup, putdown, stack and un-stack in Block world problem <br>
Step 5 :  In pickup action, Robot arm pick the block on table. Precondition is Block is on table and no other block on specified block and arm-hand empty.<br>
Step 6:  In putdown action, Robot arm place the block on table. Precondition is robot-arm holding the block.<br>
Step 7 : In un-stack action, Robot arm pick the block on some block. Precondition is Block is on another block and no other block on specified block and arm-hand empty.<br>
Step 8 : In stack action, Robot arm place the block on under block. Precondition is Block holded by robot arm and no other block on under block.<br>
Step 9 : Define a problem for block world problem.<br> 
Step 10 : Obtain the plan for given problem.<br> 

### Program:
```
(define (domain blocksworld)
(:requirements :strips :equality)
(:predicates (clear ?x)
 (on-table ?x)
 (arm-empty)
 (holding ?x)
 (on ?x ?y))
(:action pickup
 :parameters (?ob)
 :precondition (and (clear ?ob) (on-table ?ob) (arm-empty))
```
```
 :effect (and (holding ?ob) (not (clear ?ob)) (not (on-table ?ob))
 (not (arm-empty))))
(:action putdown
 :parameters (?ob)
 :precondition (and (holding ?ob))
 :effect (and (clear ?ob) (arm-empty) (on-table ?ob)
 (not (holding ?ob))))
(:action stack
 :parameters (?ob ?underob)
 :precondition (and (clear ?underob) (holding ?ob))
 :effect (and (arm-empty) (clear ?ob) (on ?ob ?underob)
 (not (clear ?underob)) (not (holding ?ob))))
(:action unstack
 :parameters (?ob ?underob) 
 :precondition (and (on ?ob ?underob) (clear ?ob) (arm-empty))
 :effect (and (holding ?ob) (clear ?underob)
 (not (on ?ob ?underob)) (not (clear ?ob)) (not (arm-empty)))))
```
### InpuT:
```
(define (problem pb1)
 (:domain blocksworld)
 (:objects a b)
 (:init (on-table a) (on-table b) (clear a) (clear b) (arm-empty))
 (:goal (and (on a b))))
```


### Output/Plan:
# Ex.No: 7  Logic Programming –  Logic Circuit Design                                                                      
### REGISTER NUMBER : 212222040086
### AIM: 
To write a logic program to design a circuit like half adder and half subtractor.
###  Algorithm:
1. Start the Program
2. Design a AND gate logic if both inputs are 1 then output is 1.
3. Design a OR gate logic if any one of input is 1 then output is 1.
4. Design a XOR gate logic if both inputs are different then output is 1.
5. Design a NOT gate logic if input is 0 then output is 1.
6. Design a half adder and half subtractor using the rules.
7. Test the logic.
8. Stop the program.
```


















```
### Program:
```
and(0,0,0).
and(0,1,0).
and(1,1,1).
and(1,0,0).
xor(1,0,1).
xor(1,1,0).
xor(0,1,1).
xor(0,0,0).
not(0,1).
not(1,0).
or(0,0,0).
or(0,1,1).
or(1,1,1).
or(1,0,1).
halfadder(A,B,Sum,Carry):-
    xor(A,B,Sum),
    and(A,B,Carry).
halfsubtractor(A, B, Difference, Borrow):-
    xor(A, B, Difference),
    not(A, NA),
    and(NA, B, Borrow).
```







### Output:
![image](https://github.com/user-attachments/assets/98b478b2-476a-4361-9360-dff1b798a2e3)
```







```



### Result:
Thus the truth table of circuit verified sucessfully.

```
### Result:
Thus the plan was found for the initial and goal state of block world problem.
