# The Report

## Question
[Question Link](https://www.hackerrank.com/challenges/the-report/problem?isFullScreen=true)

## Answer in SQL Server
    /*
    output:
    - table with name, grade, mark
    ^ replace name with Null for students with grade < 8
    ^ order by grade desc, name asc
      ^ for students with no name, order by marks asc

    steps:
    0. create cte table where students & grades tables are combined with
    calculated grade column
    1. create table A with student grade >= 8
    2. order the table A
    3. create table B with student grade < 8
    4. make name to Null in table B
    5. order the table B
    5. merge table A and table B
    */

    with student_grade as -- contains student name, grade and mark
    (
        select 
            name,
            grade,
            marks
        from students s join grades g on 
            g.min_mark <= s.marks and s.marks <= g.max_mark
    )

    select -- contains students with upper grade
        name,
        grade,
        marks
    from student_grade
    where grade >= 8

    union -- union tables with distinct values

    select -- contains sutdents with lower grade
        Null as name, -- Null is given for the name
        grade,
        marks
    from student_grade
    where grade < 8
    order by grade desc, name, marks -- order by clause is applied after the last union table

## Output
    Britney 10 95
    Heraldo 10 94
    Julia 10 96
    Kristeen 10 100
    Stuart 10 99
    Amina 9 89
    Christene 9 88
    Salma 9 81
    Samantha 9 87
    Scarlet 9 80
    Vivek 9 84
    Aamina 8 77
    Belvet 8 78
    Paige 8 74
    Priya 8 76
    Priyanka 8 77
    NULL 7 64
    NULL 7 66
    NULL 6 55
    NULL 4 34
    NULL 3 24
