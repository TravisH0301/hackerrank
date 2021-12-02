# Weather Observation Station 20

## Question
[Question Link](https://www.hackerrank.com/challenges/weather-observation-station-20/problem?isFullScreen=true)

## Answer in SQL Server
    /*
    output:
    - median of lat_n from stations in 4 decimal points

    steps:
    1. create row_number and get the find the medium row number
    2. get lat_n associates to the medium row number
    */

    with rn_table as -- table with row numbers
    (
        select
            lat_n,
            row_number() over (order by lat_n) rn
        from station
    )

    select cast(round(lat_n, 4) as decimal(9,4)) -- decimal(9,4) format returns 9 non decimal points and 4 decimal poins
    from rn_table
    where rn = ((select max(rn) from rn_table)/2 + 1) -- calculates median

## Output
    83.8913
