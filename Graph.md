### Overview
A graph is a non-linear kind of data structure made up of nodes or vertices and edges. The edges connect any two nodes in the graph, and the nodes are also known as vertices.
![[Pasted image 20240318111151.png]]

In C++ the struct would look something like:
```cpp
#include <iostream>
#include <vector>

using namespace std;

struct Vertex {
    int id;
    vector<int> neighbors;

    Vertex(int _id) : id(_id) {}
};

struct Graph {
    vector<Vertex> vertices;

    void addVertex(int id) {
        vertices.push_back(Vertex(id));
    }

    void addEdge(int src, int dest) {
        for (auto& vertex : vertices) {
            if (vertex.id == src) {
                vertex.neighbors.push_back(dest);
            }
        }
    }
};
```