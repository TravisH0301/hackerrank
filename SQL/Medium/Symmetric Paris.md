# Symmetric Paris

## Question
[Question Link](https://www.hackerrank.com/challenges/symmetric-pairs/problem?isFullScreen=true)

## Answer in SQL Server
    /*
    Outcome:
    - symmetric pair of (x,y)
    ^ one row (x1,y1) & another row (x2,y2) where x1=y2 & y1=x2
    - the symmetric pair has to be on the different row
    ^ not (x1,y1) & (x1,y1)

    Steps:
    1. self join the table while x1=y2 & x2=y1
    2. remove symmetric pairs where they are the same rows
    3. x <= y
    */

    select
        f1.x as x1,
        f1.y as y1
    from 
        functions f1 
        join functions f2 on (f1.x = f2.y and f1.y = f2.x)
    group by f1.x, f1.y -- group by ensures only a single symmetric pair is shown
    having 
        (f1.x = f1.y and count(f1.x) > 1) -- when x = y, make sure they are from different rows by ensuring the same x,y values exists on the other rows
        or f1.x < f1.y -- ensure x < y (the case for x = y is already taken care with the previous condition)
    order by f1.x
    
## Output
    2 24
    4 22
    5 21
    6 20
    8 18
    9 17
    11 15
    13 13
