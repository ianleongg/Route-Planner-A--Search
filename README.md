# **Implementing a Route Planner**

## Search Alogrithms

### Using A* Search to implement a "Google-maps" style route planning algorithm.

---

**Route Planner with A* Search Project**

The goals / steps of this project are the following:

* Have a working matrix class file to implement the Kalman Filter.
* Generate data to visualize it before implementing Kalman Filter.
* Implement the kalman filter on said data and visualize results.

[//]: # (Image References)

[image1]: ./Result_Images/newplot.png "1"
[image2]: ./Result_Images/newplot(1).png "2"
[image3]: ./Result_Images/newplot(3).png "3"

### README

- The implementation of route planner using A* Search algorithm can be found in [project code](./route_planner.ipynb). The data for the map used can be found in [helpers.py](./helpers.py). 

- The below image shows the result of the implemented A* Search:
  - Black Dot: Starting point
  - Red Dot: Path taken
  - Yellow Dot: Destination Point

![alt text][image3]

### Steps used to implement route planner.

#### 1. Load a basic map from the helper function.

* Map objects have two properties: intersections and roads
  - intersections are represented as a dictionary, each identified by an x,y coordinate 
  - roads property is a list where roads[i] contains a list of the intersections that intersection i connects to

* Map_10:
  - The map shows a disconnected network of 10 intersections. 
  - The two intersections on the left are connected to each other but they are not connected to the rest of the road network. 
  - This map is quite literal in its expression of distance and connectivity.
  - The edge between 2 nodes(intersections) represents a literal straight road not just an abstract connection of 2 cities.

![alt text][image1]

* Map_40:
  - The map shows a network of roads which spans 40 different intersections (labeled 0 through 39). 

![alt text][image2]

#### 2. A* Search Algorithm

* PathPlanner class

  - __init__ - We initialize our path planner with a map, M, and typically a start and goal node. 

  - closedSet includes any explored/visited nodes. 

  - openSet are any nodes on our frontier for potential future exploration. 

  - cameFrom will hold the previous node that best reaches a given node.

  - gScore is the g in our f = g + h equation, or the actual cost to reach our current node

  - fScore is the combination of g and h, i.e. the gScore plus a heuristic; total cost to reach the goal

  - path comes from the run_search function

  - reconstruct_path just rebuilds the path after search is run, going from the goal node backwards using each node's cameFrom information.

* Data Structures

  - decide on data structures to use - lists, sets, dictionaries, etc for PathPlanner Class

* Set certain variables

  - help set certain variables if they weren't a part of initializating our PathPlanner class, or if they need to be changed for another reason.

* Get node information

  - In is_open_empty, you are checking whether there are still nodes on the frontier to explore.

  - In get_current_node(), you'll want to come up with a way to find the lowest fScore of the nodes on the frontier. 

  - In get_neighbors, you'll need to gather information from the map to find the neighbors of the current node.

* Scores and Costs

  - main part of the calculation for determining the best path: calculating the various parts of the fScore.

* Recording the best path

  - After implementing the various functions on scoring, record the best path to a given neighbor node from the current node.

#### 3. Test in the code

  - Black Dot: Starting point
  - Red Dot: Path taken
  - Yellow Dot: Destination Point

![alt text][image3]

