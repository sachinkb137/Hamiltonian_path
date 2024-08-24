﻿# Hamiltonian_path
# Hamiltonian_path
#include <iostream>

#include <fstream>

#include <vector>

using namespace std;

const int MAX_VERTICES = 20;

class HamiltonianCircuit {

private:

int numVertices;

vector<vector<int>> graph;

vector<int> path;

vector<bool> visited;

public:

HamiltonianCircuit(int vertices) {

numVertices vertices;

graph.assign(numVertices, vector<int>(numVertices, 0)); visited.assign(numVertices, false);

}

void addEdge(int u, int v) {

graph[u][v] = 1;

graph [v][u] = 1;

}

bool canVisit(int v, int pos) {

if (graph[path[pos-1]][v] == 0)

return false;

for (int i = 0; i < pos; ++i)

if (path[i] = v)

return false;

return true;

}
bool hamiltonianUtil(int pos) {

if (pos numVertices) {

if (graph[path [pos 1]] [path[0]] == 1) return true;

else

return false;

}

for (int v = 1; v < numVertices; ++v) {

if (canVisit(v, pos)) {

path[pos] = v;

visited[v] = true;

if (hamiltonianUtil (pos + 1)) return true;

path[pos] = -1; // backtrack

visited[v] = false;

}

}

return false;

}

void findHamiltonianCircuit() {

path.assign(numVertices, -1);

path[0] = 0;

visited[0] = true;

if (hamiltonianUtil(1)) {

cout << "Hamiltonian Circuit found:" << endl; for (int i = 0; i < numVertices; ++i)

cout << path[i] << " ";

cout << path[0] << endl;

ofstream outFile("adjacency_matrix.csv"); for (int i = 0; i < numVertices; ++i) { for (int j=0; j < numVertices; ++j) { outFile <<< graph[i][j]; if (j!= numVertices - 1) outFile << ",";

}

outFile <<< endl;

}

outFile.close();
..

ofstream pathFile("hamiltonian_path.csv");

for

(int i=0; i < numVertices; ++i) {

pathFile << path[i];

if (i!= numVertices - 1)

pathFile <<< ",";

}

pathFile.close();

cout << "Hamiltonian path saved to hamiltonian_path.csv" << endl;

} else {

cout << "Hamiltonian Circuit does not exist." << endl;

}

}

void printGraph() {

cout << "Graph adjacency matrix:" << endl;

for

(int i=0; i < numVertices; ++i) {

for (int j=0; j < numVertices; ++j) {

cout << graph[i][j] <<< " ";

}

cout << endl;

}

} };

int main() {

int numVertices:

cout << "Enter the number of vertices in the graph: ";

cin >> numVertices;

HamiltonianCircuit hc(numVertices);

for (int i=0; i < numVertices; ++i) {

for (int j=i+1; j < numVertices; ++j) { hc.addEdge(i, j);

}

}

hc.printGraph();

hc.findHamiltonianCircuit();

return 0;

}
