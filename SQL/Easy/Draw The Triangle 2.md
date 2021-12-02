# Draw The Triangle 2

## Question
[Question Link](https://www.hackerrank.com/challenges/draw-the-triangle-2/problem?isFullScreen=true&h_r=next-challenge&h_v=zen)

P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):

    * 
    * * 
    * * * 
    * * * * 
    * * * * *

Write a query to print the pattern P(20).

## Answer in SQL Server
    /*
    Output:
    - Triangle using '*' with 20 rows & 20 columns in a increasing order

    Steps:
    1. declare a number = 1
    2. create a loop to draw '*' on each row
    3. increase the number by 1 at the end of loop
    4. close loop when the number reaches 20
    */

    declare @num int = 1;

    while (@num <=20)
    begin
        select replicate('* ', @num)
        set @num += 1;
    end
    
## Output
    * 
    * * 
    * * * 
    * * * * 
    * * * * * 
    * * * * * * 
    * * * * * * * 
    * * * * * * * * 
    * * * * * * * * * 
    * * * * * * * * * * 
    * * * * * * * * * * * 
    * * * * * * * * * * * * 
    * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * * * * 
    * * * * * * * * * * * * * * * * * * * * 
