# 15 Days of Learning SQL

## Question
[Question Link](https://www.hackerrank.com/challenges/15-days-of-learning-sql/problem?isFullScreen=true)

## Answer in SQL Server
    /*
    outcome: 
    1. submission date
    2. unique hacker count who submitted everyday since start
    3. hacker_id who submitted the most 
    4. hacker name who submitted the most
    - order by submission date
    - if same max submission by hackers, choose hacker with lower alphabet name

    steps:
    1. find unique hacker count per day
    2. find hacker who submitted the most per day
    3. combine 1&2 by submission date
    */

    with unique_hacker_sub as -- contains distinct hacker in submission table
    (
        select distinct
            submission_date,
            hacker_id
        from submissions
    ),

    unique_hacker_sub_row as -- gives row and date diff for previous CTE
    (
        select
            submission_date,
            hacker_id,
            row_number() over (partition by hacker_id order by submission_date) as rn,
            datediff(day, '2016-03-01', submission_date) + 1 as date_diff
        from unique_hacker_sub
    ),

    count_unique_hacker as -- counts unique hackers who sumitted everyday
    (
        select
            submission_date,
            count(hacker_id) as unique_hacker_count
        from unique_hacker_sub_row
        where rn = date_diff -- to ensure only pick hackers who submitted everyday
        group by submission_date
    ),

    max_sub_hacker_row as -- determines max sub by hacker and create row numbers 
    (
        select
            submission_date,
            s.hacker_id,
            h.name,
            count(submission_date) as max_sub_count,
            row_number() over (partition by submission_date order by count(submission_date) desc, s.hacker_id) rn
        from submissions s join hackers h on (s.hacker_id = h.hacker_id)
        group by submission_date, s.hacker_id, name
    )

    select
        m.submission_date,
        unique_hacker_count,
        m.hacker_id,
        m.name
    from 
        max_sub_hacker_row m 
        join count_unique_hacker c on (m.submission_date = c.submission_date)
    where rn = 1

## Outcome
    2016-03-01 112 81314 Denise 
    2016-03-02 59 39091 Ruby 
    2016-03-03 51 18105 Roy 
    2016-03-04 49 533 Patrick 
    2016-03-05 49 7891 Stephanie 
    2016-03-06 49 84307 Evelyn 
    2016-03-07 35 80682 Deborah 
    2016-03-08 35 10985 Timothy 
    2016-03-09 35 31221 Susan 
    2016-03-10 35 43192 Bobby 
    2016-03-11 35 3178 Melissa 
    2016-03-12 35 54967 Kenneth 
    2016-03-13 35 30061 Julia 
    2016-03-14 35 32353 Rose 
    2016-03-15 35 27789 Helen 

