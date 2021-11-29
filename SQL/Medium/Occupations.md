# Occupations

## Question
[Question Link](https://www.hackerrank.com/challenges/occupations/problem?isFullScreen=true)

Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

Note: Print NULL when there are no more names corresponding to an occupation.

## Answer in SQL Server
    select 
        [Doctor], [Professor], [Singer], [Actor] -- columns from pivot_table (must be in brackets!)
    from (
        select 
            name, 
            occupation, 
            row_number() over (partition by occupation order by name) as row_num -- using row_number() makes each name depends on both occupation & row_num
        from occupations
    ) as source_table
    pivot(
        max(name) for occupation in ([Doctor], [Professor], [Singer], [Actor]) -- pivot allows aggregations of a column by the pivotted columns
    ) as pivot_table

## Output
    Aamina Ashley Christeen Eve
    Julia Belvet Jane Jennifer
    Priya Britney Jenny Ketty
    NULL Maria Kristeen Samantha
    NULL Meera NULL NULL
    NULL Naomi NULL NULL
    NULL Priyanka NULL NULL
