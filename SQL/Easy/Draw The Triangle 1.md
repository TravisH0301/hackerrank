# Draw The Triangle 1

## Question
[Question Link](https://www.hackerrank.com/challenges/draw-the-triangle-1/problem?isFullScreen=true)

P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):

    * * * * * 
    * * * * 
    * * * 
    * * 
    *
    
Write a query to print the pattern P(20).

## Answer in SQL Server
    /*
    Output:
    - create a triangle using '*' with 20 rows

    Steps:
    1. declare a number = 20
    2. create a loop starting from 20 and down to 1
    3. within the loop, print '*' respective to decreasing number (20~1)
    */

    declare @num int = 20;

    while (@num > 0)
    begin
        select replicate('* ', @num)
        set @num -= 1
    end

## Output
    * * * * * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * 
    * * * * * * * * * * * * 
    * * * * * * * * * * * 
    * * * * * * * * * * 
    * * * * * * * * * 
    * * * * * * * * 
    * * * * * * * 
    * * * * * * 
    * * * * * 
    * * * * 
    * * * 
    * * 
    * 
