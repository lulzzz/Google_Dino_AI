# Google_Dino_AI
<div align="center">
  <img src="https://github.com/lgonz041/Google_Dino_AI/blob/master/icon.png"><br><br>
</div>

Neural_Net + Genetic Algorithm = &lt;3 

Winter break 2018 project 
## The Game

This is a clone of the google dinosaur game made using the [Godot Game engine](https://godotengine.org/). 

**To run this project**

Under the Export Folder there is a executable. 

**To make changes**
1. First download Godot Version 3.0.6 Stable or latest. 

2. Clone or download the repository.

3. Start the Godot engine and run the project.godot file. 

4. Select Project->Project Settings->AutoLoad-> Add. Add the Gobal.gd script from the scipts folder.

5. Hit play

6. Have fun :) 

## The Neural Network 
**4 Inputs** 

1. X coordinate position of next obstacle.  Normalized by dividing the Maximum posible distance

2. Realative velocity of obstacles. Normalized by dividing by 10 time the initial value. 

4. Indication if next object is a pterodactyl.(1 =true, 0=false)

3. Constant, random range (-1,1).

**1 Hidden Layer**

The hidden layer has 3 nodes and use the **tanh** as the activation function.

**3 Outputs** 

The outputs use the **tanh** activation function. Therefore, that ouput ranges from (-1,1).
One output corresponses to small jump and the other corresponse to big jump. The largest output is selected. But in order to activate the jump the value must be greater then zero. 

In addition, if the third output indicates to duck a signal is emited to duck if output is over .3. else it stands. 
The reason the threshold is higher is to prevent random ducking. 

## Genetic Algorithm 

**Initial Population**
The population consist of 100 Dinosours. All of which are initialized with random weights ranging from (-1,1).

**Evaluation**
The score is kept to determin the best candidates for offsprings. The highest scoring Dinos will pass down there genetic information in the form of weights on the neural network. The game goes off indefinitely.

**Selection**
The two top scoring dinos will pass down there genetic information to the next generation. 70 percent has the higest scoring genetic information, while 30 percent has the genetic information from the second higest scoring dino.  

**Crossover**
Then at random genes get swap. 10 percent chance of a specific gene getting swapped by the equivalent from the other parent.

**Mutation**
At the same time motation to those genes occure. 10 percent chance of gene mutating. This is represented by adding a random value ranging from (-.5,.5) to the specific gene. 

**NOTE** 
In order to prevent getting stuck in with random jumping as the optimal solution, 10% of the next generation is made at random, this also helps prevent getting stuck in any local minimun/maximum. 
