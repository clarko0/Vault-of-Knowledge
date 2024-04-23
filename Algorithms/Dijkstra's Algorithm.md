Dijkstra's algorithm finds the shortest path from one vertex to all other vertices on a [[Graph]].
It does so by repeatedly selecting the nearest unvisited vertex and calculating the distance to all the unvisited neighbouring vertices.

**How it works:**

1. Set initial distances for all vertices: 0 for the source vertex, and infinity for all the other.
2. Choose the unvisited vertex with the shortest distance from the start to be the current vertex. So the algorithm will always start with the source as the current vertex.
3. For each of the current vertex's unvisited neighbour vertices, calculate the distance from the source and update the distance if the new, calculated, distance is lower.
4. We are now done with the current vertex, so we mark it as visited. A visited vertex is not checked again.
5. Go back to step 2 to choose a new current vertex, and keep repeating these steps until all vertices are visited.
6. In the end we are left with the shortest path from the source vertex to every other vertex in the graph.

A code implementation looks like:
```python
def dijkstra(self, start_vertex_data):
	start_vertex = self.vertex_data.index(start_vertex_data)
	distances = [float('inf')] * self.size
	distances[start_vertex] = 0
	visited = [False] * self.size

	for _ in range(self.size):
		min_distance = float('inf')
		u = None
		for i in range(self.size):
			if not visited[i] and distances[i] < min_distance:
				min_distance = distances[i]
				u = i

		if u is None:
			break

		visited[u] = True

		for v in range(self.size):
			if self.adj_matrix[u][v] != 0 and not visited[v]:
				alt = distances[u] + self.adj_matrix[u][v]
				if alt < distances[v]:
					distances[v] = alt

	return distances
```