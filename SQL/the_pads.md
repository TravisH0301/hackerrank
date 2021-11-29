# The PADS

## Question
[Question Link](https://www.hackerrank.com/challenges/the-pads/problem?isFullScreen=true)

Generate the following two result sets:

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:

There are a total of [occupation_count] [occupation]s.
where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.

Note: There will be at least two entries in the table for each type of occupation.

Sample Output

    Ashely(P)
    Christeen(P)
    Jane(A)
    Jenny(D)
    Julia(A)
    Ketty(P)
    Maria(A)
    Meera(S)
    Priya(S)
    Samantha(D)
    There are a total of 2 doctors.
    There are a total of 2 singers.
    There are a total of 3 actors.
    There are a total of 3 professors.

## Answer in SQL Server
    select
        concat(name, '(', left(occupation,1), ')')
    from occupations
    order by name

    select 
        concat('There are a total of ', count(name), ' ', lower(occupation), 's.')
    from occupations
    group by occupation
    order by count(name), occupation
    
## Output
    Aamina(D)
    Ashley(P)
    Belvet(P)
    Britney(P)
    Christeen(S)
    Eve(A)
    Jane(S)
    Jennifer(A)
    Jenny(S)
    Julia(D)
    Ketty(A)
    Kristeen(S)
    Maria(P)
    Meera(P)
    Naomi(P)
    Priya(D)
    Priyanka(P)
    Samantha(A)
    There are a total of 3 doctors.
    There are a total of 4 actors.
    There are a total of 4 singers.
    There are a total of 7 professors.




