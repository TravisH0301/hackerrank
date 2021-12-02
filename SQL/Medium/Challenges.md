# Challenges

## Question
[Question Link](https://www.hackerrank.com/challenges/challenges/problem?isFullScreen=true)

## Answer in SQL Server
    /*
    output:
    - print hacker_id, name, total challege count 
    - order by total challenge count desc, hacker_id
    - if same count between students but count < max count,
    disregard duplicated students

    step:
    1. combine hackers & challenges tables and count challenged for hackers
    2. remove duplicated students if count < max count
    3. sort table
    */

    with challenge_count_table as
    (
        select
            h.hacker_id,
            name,
            count(challenge_id) as challenge_count
        from hackers h join challenges c on (h.hacker_id = c.hacker_id)
        group by h.hacker_id, name
    ),

    challenge_count_no_dup as -- challenge counts that have no duplicated hackers except the highest challenge count
    (
        select
            challenge_count
        from challenge_count_table
        where challenge_count <> (select max(challenge_count) from challenge_count_table)
        group by challenge_count
        having count(hacker_id) <= 1
    )

    select -- contains info of hacker with highest challenge count
        hacker_id,
        name,
        challenge_count
    from challenge_count_table
    where challenge_count = (select max(challenge_count) from challenge_count_table)

    union

    select -- contains info of hackers with no duplicated challenge count
        hacker_id,
        name,
        challenge_count
    from challenge_count_table
    where challenge_count in (select * from challenge_count_no_dup)
    order by challenge_count desc, hacker_id

## Output
    5120 Julia 50
    18425 Anna 50
    20023 Brian 50
    33625 Jason 50
    41805 Benjamin 50
    52462 Nicholas 50
    64036 Craig 50
    69471 Michelle 50
    77173 Mildred 50
    94278 Dennis 50
    96009 Russell 50
    96716 Emily 50
    72866 Eugene 42
    37068 Patrick 41
    12766 Jacqueline 40
    86280 Beverly 37
    19835 Joyce 36
    38316 Walter 35
    29483 Jeffrey 34
    23428 Arthur 33
    95437 George 32
    46963 Barbara 31
    87524 Norma 30
    84085 Johnny 29
    39582 Maria 28
    65843 Thomas 27
    5443 Paul 26
    52965 Bobby 25
    77105 Diana 24
    33787 Susan 23
    45855 Clarence 22
    33177 Jane 21
    7302 Victor 20
    54461 Janet 19
    42277 Sara 18
    99388 Mary 16
    31426 Carlos 15
    95010 Victor 14
    27071 Gerald 10
    90267 Edward 9
    72609 Bobby 8
