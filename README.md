# Assignment-4-ai-ml
from collections import deque

def bfs_maze(maze, start, end):
    rows, cols = len(maze), len(maze[0])
    directions = [(0, 1), (1, 0), (0, -1), (-1, 0)]  
    queue = deque([start])
    visited = set()
    visited.add(start)
    parent = {start: None}  
    
    while queue:
        current = queue.popleft()
        if current == end:
            
            path = []
            while current:
                path.append(current)
                current = parent[current]
            return path[::-1]  
        
        for dx, dy in directions:
            x, y = current[0] + dx, current[1] + dy
            neighbor = (x, y)
            if 0 <= x < rows and 0 <= y < cols and maze[x][y] == 0 and neighbor not in visited:
                queue.append(neighbor)
                visited.add(neighbor)
                parent[neighbor] = current
    
    return "No path found."
