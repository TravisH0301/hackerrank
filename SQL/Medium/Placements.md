# Placements

## Question
[Question Link](https://www.hackerrank.com/challenges/placements/problem?isFullScreen=true)

## Answer in SQL Server
    /*
    output:
    - names of students whose best friends got higher salary
    - order by salary of best friends

    steps:
    1. combine all tables to create:
    id, salary, friend id, friend salary
    2. filter out students with higher than their friends
    3. leave student name only
    */

    select
        s.name
    from 
        students s
        join friends f on (s.id = f.id)
        join packages p_s on (s.id = p_s.id) -- student salary
        join packages p_f on (f.friend_id = p_f.id) -- student's friend salary
    where p_f.salary > p_s.salary
    order by p_f.salary

## Output
    Stuart
    Priyanka
    Paige
    Jane
    Julia
    Belvet
    Amina
    Kristeen
    Scarlet
    Priya
    Meera
