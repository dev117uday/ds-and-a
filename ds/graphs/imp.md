# Important Code

### Shortest Path in un-weighted graph

```java
import java.util.*;

class Graph {

    static void addEdge(ArrayList<ArrayList<Integer>> adj, int u, int v) {
        adj.get(u).add(v);
        adj.get(v).add(u);
    }

    static void BFS(ArrayList<ArrayList<Integer>> adj, int V, int s, int[] dist) {
        boolean[] visited = new boolean[V];
        for (int i = 0; i < V; i++)
            visited[i] = false;

        Queue<Integer> q = new LinkedList<>();

        visited[s] = true;
        q.add(s);

        while (q.isEmpty() == false) {
            int u = q.poll();

            for (int v : adj.get(u)) {
                if (visited[v] == false) {
                    dist[v] = dist[u] + 1;
                    visited[v] = true;
                    q.add(v);
                }
            }
        }
    }

    public static void main ( String[] args ) {
        int V = 4;
        ArrayList<ArrayList<Integer>> adj = new ArrayList<ArrayList<Integer>>(V);

        for (int i = 0; i < V; i++)
            adj.add(new ArrayList<Integer>());

        addEdge(adj, 0, 1);
        addEdge(adj, 1, 2);
        addEdge(adj, 2, 3);
        addEdge(adj, 0, 2);
        addEdge(adj, 1, 3);
        int[] dist = new int[V];
        for (int i = 0; i < V; i++) {
            dist[i] = Integer.MAX_VALUE;
        }
        dist[0] = 0;
        BFS(adj, V, 0, dist);

        for (int i = 0; i < V; i++) {
            System.out.print(dist[i] + " ");
        }
    }
}
```

### Detect cycle in Un-directed Graph

```java
import java.util.*;

class Graph {

    static void addEdge(ArrayList<ArrayList<Integer>> adj, int u, int v) {
        adj.get(u).add(v);
        adj.get(v).add(u);
    }

    static boolean DFSRec(ArrayList<ArrayList<Integer>> adj, int s, boolean[] visited, int parent) {
        visited[s] = true;

        for (int u : adj.get(s)) {
            if (visited[u] == false) {
                if (DFSRec(adj, u, visited, s) == true) {
                    return true;
                }
            } else if (u != parent) {
                return true;
            }
        }
        return false;
    }

    static boolean DFS(ArrayList<ArrayList<Integer>> adj, int V) {
        boolean[] visited = new boolean[V];
        for (int i = 0; i < V; i++)
            visited[i] = false;

        for (int i = 0; i < V; i++) {
            if (visited[i] == false)
                if (DFSRec(adj, i, visited, -1) == true)
                    return true;
        }
        return false;
    }

    public static void main ( String[] args ) {
        int V = 6;
        ArrayList<ArrayList<Integer>> adj = new ArrayList<ArrayList<Integer>>(V);

        for (int i = 0; i < V; i++)
            adj.add(new ArrayList<Integer>());

        addEdge(adj, 0, 1);
        addEdge(adj, 1, 2);
        addEdge(adj, 2, 4);
        addEdge(adj, 4, 5);
        addEdge(adj, 1, 3);
        addEdge(adj, 2, 3);

        if (DFS(adj, V) == true)
            System.out.println("Cycle found");
        else
            System.out.println("No cycle found");
    }
}
```

### Detect Cycle Directed Graph

```java
import java.util.*;

class Graph {

    static void addEdge(ArrayList<ArrayList<Integer>> adj, int u, int v) {
        adj.get(u).add(v);
        adj.get(v).add(u);
    }

    static boolean DFSRec(ArrayList<ArrayList<Integer>> adj, int s, boolean[] visited, boolean[] recSt) {
        visited[s] = true;
        recSt[s] = true;

        for (int u : adj.get(s)) {
            if (visited[u] == false && DFSRec(adj, u, visited, recSt) == true) {
                return true;
            } else if (recSt[u] == true) {
                return true;
            }
        }
        recSt[s] = false;
        return false;
    }

    static boolean DFS(ArrayList<ArrayList<Integer>> adj, int V) {
        boolean[] visited = new boolean[V];
        for (int i = 0; i < V; i++)
            visited[i] = false;

        boolean[] recSt = new boolean[V];
        for (int i = 0; i < V; i++)
            recSt[i] = false;

        for (int i = 0; i < V; i++) {
            if (visited[i] == false)
                if (DFSRec(adj, i, visited, recSt) == true)
                    return true;
        }
        return false;
    }

    public static void main ( String[] args ) {
        int V = 6;
        ArrayList<ArrayList<Integer>> adj = new ArrayList<ArrayList<Integer>>(V);

        for (int i = 0; i < V; i++)
            adj.add(new ArrayList<Integer>());

        addEdge(adj, 0, 1);
        addEdge(adj, 2, 1);
        addEdge(adj, 2, 3);
        addEdge(adj, 3, 4);
        addEdge(adj, 4, 5);
        addEdge(adj, 5, 3);

        if (DFS(adj, V) == true)
            System.out.println("Cycle found");
        else
            System.out.println("No cycle found");
    }
}
```



