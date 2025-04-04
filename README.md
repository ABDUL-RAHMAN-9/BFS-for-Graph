# BFS-for-Graph
<p>
  Breadth First Search (BFS)  is a fundamental  graph traversal algorithm. It begins with a node, then first traverses all its adjacent nodes. Once all adjacent are visited, then their adjacent are traversed. 
<p/>
    
- BFS is different from DFS in a way that closest vertices are visited before others. We mainly traverse vertices level by level. 
- Popular graph algorithms like Dijkstra’s shortest path, Kahn’s Algorithm, and Prim’s algorithm are based on BFS.  
- BFS itself can be used to detect cycle in a directed and undirected graph, find shortest path in an unweighted graph and many more problems.


# Problem: BFS of a graph
<div>
  <div>
    Given a directed graph. The task is to do Breadth First Traversal of this graph starting from 0.
Note: One can move from node u to node v only if there's an edge from u to v. Find the BFS traversal of the graph starting from the 0th vertex, from left to right according to the input graph. Also, you should only take nodes directly or indirectly connected from Node 0 in consideration.
  </div>
  <h3>Example 1:</h3>
  
<div>
  <h3>Input:</h3>
  <img src="https://media.geeksforgeeks.org/img-practice/PROD/addEditProblem/700217/Web/Other/e0eb5630-5d6c-493a-9b1e-d16d40f10b01_1685086421.png">
</div>

```
Output: 0 1 2 3 4
Explanation: 
0 is connected to 1 , 2 , 3.
2 is connected to 4.
so starting from 0, it will go to 1 then 2
then 3. After this 2 to 4, thus bfs will be
0 1 2 3 4. 
```
   
</div>
<div>
  <h2>Your task:</h2>
  <p>
    You dont need to read input or print anything. Your task is to complete the function bfsOfGraph() which takes the integer V denoting the number of vertices and adjacency list as input parameters and returns  a     list containing the BFS traversal of the graph starting from the 0th vertex from left to right.
  </p>

  <h2>
    <b>
    Expected Time Complexity: O(V + E)
    <br>
Expected Auxiliary Space: O(V)
  </b>
  </h2>


- Approach to solve the problem:

<p>
  BFS stands for Breadth  First Search, it is a method to traverse the graph: BFS uses queue Data structure for Traversal of the Graph: 
</p>    
<img src="https://media.geeksforgeeks.org/comments/49b034cd-71c9-4f1f-b4ae-c93f0426771e_1690816471.png">


</div>

## Here is the steps to solve the problem:

- Create a boolean list vis of size V to mark all vertices as not visited (initially set to false).
- Set the starting vertex s to 0 and mark it as visited by setting vis[s] to true.
- Create an empty vector res to store the BFS traversal result.
- Create an empty queue q for BFS and enqueue the starting vertex s.
- While the queue q is not empty, do the following:
- Dequeue the front element from q and store it in t.
- Add t to the res vector.
- For each vertex v adjacent to t (as given in the adjacency list adj[t]), do the following:
- If v is not visited, mark it as visited by setting vis[v] to true, and enqueue v in the queue 
- Once the BFS traversal is complete, return the res vector, which contains the BFS traversal order.
 <h2>Here is the CPP implementation:<h2/>
 
   
```
 vector<int> bfsOfGraph(int V, vector<int> adj[]) {
        // Code here
        vector<int> ans, vis(V, 0);
        queue<int> q;
        q.push(0);
        vis[0]=1;
        while(!q.empty())
        {
            int front= q.front();
            q.pop();
            ans.push_back(front);
            for(auto &it : adj[front])
            {
                if(!vis[it])
                {
                    q.push(it);
                   
                    vis[it]=1;
                }
                 
            }
        }
        return ans;
    }

    ```
