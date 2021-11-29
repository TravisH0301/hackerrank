# Binary Tree Nodes

## Question
[Question Link](https://www.hackerrank.com/challenges/binary-search-tree-1/problem?isFullScreen=true)
You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.

Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:

Root: If node is root node.
Leaf: If node is leaf node.
Inner: If node is neither root nor leaf node.

## Answer
    select
        n,
        case when p is null then 'Root' 
             when n not in (select p from bst where p is not null) then 'Leaf' -- note that 'NOT IN' will not work for null as 1=1 & 1=Null
             else 'Inner'
        end as 'type'
    from bst
    order by n
        
## Output
    1 Leaf
    2 Inner
    3 Leaf
    4 Inner
    5 Leaf
    6 Inner
    7 Leaf
    8 Leaf
    9 Inner
    10 Leaf
    11 Inner
    12 Leaf
    13 Inner
    14 Leaf
    15 Root
