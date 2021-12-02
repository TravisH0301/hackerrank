# Print Prime Numbers

## Questions
[Question Link](https://www.hackerrank.com/challenges/print-prime-numbers/problem?isFullScreen=true)

Write a query to print all prime numbers less than or equal to . Print your result on a single line, and use the ampersand () character as your separator (instead of a space).

For example, the output for all prime numbers  would be:

    2&3&5&7
    
## Answer in SQL Server
    /*
    Output:
    - a single row of prime numbers separated by '&'

    Steps:
    1. define a number = 2
    2. create a loop and device the defined number by 
    smaller numbers 
    3. increase number by 1 within the loop
    4. when the number gets divided by the smaller numbers, it is not prime number
    5. concatnate prime numbers
    */


    declare @i int = 2; -- number starting from 2 to 1000 in a loop
    declare @is_prime int = 0; -- binary for prime number validation
    declare @result varchar(1000) = ''; -- placeholder for prime numbers

    while (@i <= 1000)
    begin
        declare @j int = @i - 1; -- define smaller number
        set @is_prime = 1;
        while (@j > 1) -- create a loop to divide the defined number
        begin
            if @i % @j = 0 -- if mudulo is 0, it is not a prime number
            begin
                set @is_prime = 0;
            end
            set @j = @j - 1; -- decrease smaller number in a loop 
        end

        if @is_prime = 1 -- if mudulo is not 0, add the prime number to the placeholder
        begin
            set @result += cast(@i as varchar(1000)) + '&';
        end

        set @i = @i + 1; -- increase the defined number by 1 in a loop
    end

    set @result = substring(@result, 1, len(@result) - 1);

    select @result

## Output
    2&3&5&7&11&13&17&19&23&29&31&37&41&43&47&53&59&61&67&71&73&79&83&89&97&101&103&107&109&113&127&131&137&139&149&151&157&163&167&173&179&181&191&193&197&199&211&223&227&229&233&239&241&251&257&263&269&271&277&281&283&293&307&311&313&317&331&337&347&349&353&359&367&373&379&383&389&397&401&409&419&421&431&433&439&443&449&457&461&463&467&479&487&491&499&503&509&521&523&541&547&557&563&569&571&577&587&593&599&601&607&613&617&619&631&641&643&647&653&659&661&673&677&683&691&701&709&719&727&733&739&743&751&757&761&769&773&787&797&809&811&821&823&827&829&839&853&857&859&863&877&881&883&887&907&911&919&929&937&941&947&953&967&971&977&983&991&997
  
