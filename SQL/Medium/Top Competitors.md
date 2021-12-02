# Top Competitors

## Question
[Question Link](https://www.hackerrank.com/challenges/full-score/problem?isFullScreen=true)

## Answer in SQL Server
    /*
    output:
    - hacker_id, name with full score for more than 1 challenge
    - order by total challenge count desc,hacker_id
    */
    select
        h.hacker_id,
        name
    from 
        hackers h 
        join submissions s on (h.hacker_id = s.hacker_id)
        join challenges c on (s.challenge_id = c.challenge_id)
        join difficulty d on (c.difficulty_level = d.difficulty_level)
    where s.score = d.score -- condition for full score
    group by h.hacker_id, name
    having count(submission_id) > 1 -- more than 1 challenge
    order by count(submission_id) desc, h.hacker_id

## Output
    27232 Phillip 
    28614 Willie 
    15719 Christina 
    43892 Roy 
    14246 David 
    14372 Michelle 
    18330 Lawrence 
    26133 Jacqueline 
    26253 John 
    30128 Brandon 
    35583 Norma 
    13944 Victor 
    17295 Elizabeth 
    19076 Matthew 
    26895 Evelyn 
    32172 Jonathan 
    41293 Robin 
    45386 Christina 
    45785 Jesse 
    49652 Christine
