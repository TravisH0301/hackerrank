# Weather Observation Station 19

## Question 
[Question Link](https://www.hackerrank.com/challenges/weather-observation-station-19/problem?isFullScreen=true)

## Answer in SQL Server
    /*
    output:
    - euclidean distance between p1 and p2
    ^ p1(min lat, min long)
    ^ p2(max lat, max long)
    - in 4 decimal places
    */

    select cast(sqrt(
               square((min(lat_n) - max(lat_n))) +
               square((min(long_w) - max(long_w)))) as decimal(9,4))
    from station

## Output
    184.1616
