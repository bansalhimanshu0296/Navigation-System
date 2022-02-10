# Navigation-System #

This project was done as a part of CSCI-B-551 Elements of Artificial Intelligence Coursework under Prof. Dr. David Crandall.

## Command to run the program ##

python3 ./route.py [start-city] [end-city] [cost-function]

## State Space ## 
All the cities that we may traverse while travelling from the start city to the  end city keeping in mind the cost factor.

## Initial state ##
 It is the start city that is given as the input.

## Goal state## 
It is the end city with the minimum cost factor given as input.

## Successor state##
 All the cities which can be traversed from the current city.

##Cost function##
 There are 4 different cost functions depending upon the cost given as the input that is distance, segments, delivery hour and time. Cost for the segment function is always 1 and the rest depends on the highway connecting two cities. Distance depends on the length of the highway, time depends upon the length and the speed limit and delivery hours also depends on the length, speed limit and aslo on distance traveled form start city to start point of the highway.

## Approach and design decisions ##

**Abstraction technique:** A* search

**Assumption:** There is always a path between 2 cities.

In the already given ‘get_route” function, firstly we read the two dataset files given and stored the data  given in it into python data structure. Depending upon  the inputted cost, we call different functions to get the desired route by minimising the minimum cost. If the cost desired is ‘distance’, we use ‘get_route_dist’ function in which we take the heuristic cost as euclidean distance.  If the cost desired is ‘segment’, we use ‘get_route_segment’ in which we set 1 as the heuristic cost. If the cost desired is ‘time’, we use ‘get_route_time’ function in which we take the heuristic cost as euclidean distance divided by average speed (average speed = sum of speed on all the highways/number of highways). If the cost desired is ‘delivery’, we use ‘get_route_del’ function in which we take the heuristic cost the same as that for ’time’. In each of the previously mentioned functions,  we have defined a dictionary that holds the priority as the key and the value is a list of tuples associated with the key that contains the start city, number of segments traveled, distance traveled, time taken, delivery hours and the route taken. We have defined a visited list that keeps track of all the visited states. We iterate through the fringe and in each iteration we are finding the minimum priority and extracting one of the elements associated with it. We call the other functions to extract the successor states and we are calculating the cost of the successor state and if the cost is already in the fringe, we will directly append the state into the cost otherwise we add it newly. We repeat this until the goal state is reached and we return a dictionary containing total segments, total miles, total hours, total delivery hours and the route taken.

## Challanges ##

The main challenge faced by us was to find the delivery hour between two cities by the formula given in assignment problem. We used the Q&A community to understand the formula to calculate the delivery hour. 


