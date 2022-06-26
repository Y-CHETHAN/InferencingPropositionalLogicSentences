# Inferencing Propositional Logic Sentences

## AIM:

To develop python code to inference propositional logic sentences to solve Wumpus World problem.

## THEORY:
The Wumpus world is a cave which has 4/4 rooms connected with passageways. So there are total 16 rooms which are connected with each other. 
<br>We have a knowledge-based agent who will go forward in this world. The cave has a room with a beast which is called Wumpus, who eats anyone who enters the room.The Wumpus can be shot by the agent, but the agent has a single arrow. 
<br>In the Wumpus world, there are some Pits rooms which are bottomless, and if agent falls in Pits, then he will be stuck there forever. The exciting thing with this cave is that in one room there is a possibility of finding a heap of gold. 
<br>So the agent goal is to find the gold and climb out the cave without fallen into Pits or eaten by Wumpus. The agent will get a reward if he comes out with gold, and he will get a penalty if eaten by Wumpus or falls in the pit.

![image](https://user-images.githubusercontent.com/65499285/175802444-e47677f3-cc54-4a32-88e1-228e020fa90a.png)


## DESIGN STEPS:
### STEP 1:
Write propositional logic sentences to define Wumpus World problem

### STEP 2:
Encode the propositional logic statements into the knowledge base using the tell function.

### STEP 3:
Make a move in the simulator and pass the percepts to the knowledge base using the tell function.

### STEP 4:
After passing the percepts to the knowledge base, ask the knowledge base about the next possible move, and make the move in accordance with the result of the ask_if_true function.

## PROGRAM:
```
/*
Developed by        : Y Chethan
Registration Number : 212220230008
*/
```
```
from utils import *
from logic import *
wumpus_kb = PropKB()
P11,P12,P21,P22,B11,B12,B21,B22,W11,W12,W21,W22,S11,S12,S21,S22,OK11,OK12,OK21,OK22=expr('P11,P12,P21,P22,B11,B12,B21,B22,W11,W12,W21,W22,S11,S12,S21,S22,OK11,OK12,OK21,OK22')

wumpus_kb.tell(B11 | '<=>' | ((P12 | P21)))
wumpus_kb.tell(B12 | '<=>' | ((P11 | P22)))
wumpus_kb.tell(B21 | '<=>' | ((P11 | P22)))
wumpus_kb.tell(B22 | '<=>' | ((P21 | P12)))

wumpus_kb.tell(S11 | '<=>' | ((W12 | W21)))
wumpus_kb.tell(S12 | '<=>' | ((W11 | W22)))
wumpus_kb.tell(S21 | '<=>' | ((W11 | W22)))
wumpus_kb.tell(S22 | '<=>' | ((W21 | W12)))

wumpus_kb.tell(~OK11| '<=>' | ((W11 | P11)))
wumpus_kb.tell(~OK12| '<=>' | ((W12 | P12)))
wumpus_kb.tell(~OK21| '<=>' | ((W21 | P21)))
wumpus_kb.tell(~OK22| '<=>' | ((W22 | P22)))

wumpus_kb.clauses

# 1,1
wumpus_kb.tell(~P11)
wumpus_kb.tell(~W11)
wumpus_kb.tell(~S11)
wumpus_kb.tell(~B11)

# 2,1
wumpus_kb.tell(~P21)
wumpus_kb.tell(~W21)
wumpus_kb.tell(S21)
wumpus_kb.tell(~B21)

# 1,2
wumpus_kb.tell(~P12)
wumpus_kb.tell(~W12)
wumpus_kb.tell(~S12)
wumpus_kb.tell(~B12)

# 2,2
wumpus_kb.tell(~P22)
wumpus_kb.tell(~W22)
wumpus_kb.tell(~S22)
wumpus_kb.tell(~B22)

wumpus_kb.ask_if_true(OK22)

```
## OUTPUT:
![image](https://user-images.githubusercontent.com/65499285/175802972-4159eb7d-8d72-44d9-9ead-6a9828558ad0.png)

<br>
## RESULT:
Thus, a program to implement inference propositional logic sentences in python to solve Wumpus World problem has been done sucessfully.
