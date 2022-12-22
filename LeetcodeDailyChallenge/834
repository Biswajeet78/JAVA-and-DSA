class Solution {
    class Node {
        int val;
        List<Node> children;
        Map<Integer, Integer> distance;
        Map<Integer, Integer> count;
        Node(int val) {
            this.val = val;
            children = new ArrayList<>();
            count = new HashMap<>();
            distance = new HashMap<>();
        }
    }
    public int[] sumOfDistancesInTree(int N, int[][] edges) {
        int[] result = new int[N];
        Node[] nodes = new Node[N];
        for (int i = 0; i < N; i++) {
            nodes[i] = new Node(i);
        }
        for (int[] edge : edges) {
            nodes[edge[0]].children.add(nodes[edge[1]]);
            nodes[edge[1]].children.add(nodes[edge[0]]);
        }
        Set<Integer> visited = new HashSet<>();
        for (int i = 0; i < N; i++) {
            countChildren(nodes, i, visited);
        }
        for (int i = 0; i < N; i++) {
            result[i] = dfs(nodes, i, visited);
        }
        return result;
    }
    private int dfs(Node[] nodes, int i, Set<Integer> visited) {
        Node cur = nodes[i];
        visited.add(i);
        int result = 0;
        for (Node child : cur.children) {
            if (visited.contains(child.val)) {
                continue;
            }
            if (!cur.distance.containsKey(child.val)) {
                cur.distance.put(child.val, dfs(nodes, child.val, visited) + cur.count.get(child.val));
            }
            result += cur.distance.get(child.val);
        }
        visited.remove(i);
        return result;
    }
    private int countChildren(Node[] nodes, int i, Set<Integer> visited) {
        Node cur = nodes[i];
        visited.add(i);
        int result = 1;
        for (Node child : cur.children) {
            if (visited.contains(child.val)) {
                continue;
            }
            if (!cur.count.containsKey(child.val)) {
                cur.count.put(child.val, countChildren(nodes, child.val, visited));
            }
            result += cur.count.get(child.val);
        }
        visited.remove(i);
        return result;
    }
}
