# Weather Observation Station 19

## Question
[Question Link](https://www.hackerrank.com/challenges/weather-observation-station-18/problem?isFullScreen=true)

## Answer in SQL Server
    /*
    output:
    - manhattan distance btw 2 points
    ^ p1 (min lat, long)
    ^ p2 (max lat, long)
    - in 4 decimal points
    */

    select
        cast(abs(max(lat_n) - min(lat_n)) + abs(max(long_w) - min(long_w)) as decimal(9,4))
    from station

## Output
    259.6859
