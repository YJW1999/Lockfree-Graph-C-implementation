# CSC591 Directed Study A1

Description:

This project is a C++ Implementation of Lock-Free Graph using CAS and FAA, all functions are thread safe, lock-free annd linearizable. The project consists two files, .cpp file contains the function and description, .h file contain the implementation for each function. The prove of linearizability for each function are in the report section of this ReadME file.


Build:


license:


Report:

In this part, every function in the API will be proven its linearizability and the results of some experiment tests.

1.create_graph()

An atomic int global variable 'is_created' is used to indicate whether a graph is created or not, the graph will only be created when 'is_created' equal to 0. The linearization point is after the atomically adding to the is_created. Once the first thead adds it from 0 to 1, other threads will not be able to read 0 from is_created, also there is no other functions use is_created variable, thus, the function is linearizable. 

2.add_vertex()

An atomic size_t counter 'current_capacity' is used to record the number of vertexes that has been added. The 'current_capacity will only be added if it is smaller than the maximum_capacity'. The linearization point is at where after the CAS loop. The CAS loop will succeed and add the value only if the number is less than the maximum capacity. After the linearization point, the new value of 'current_capacity' is visible to all other thread that read it, thus, the funtion is linearizable.


References:
