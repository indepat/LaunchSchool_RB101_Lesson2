#### Question 5

Alyssa asked Ben to write up a basic implementation of a Fibonacci  calculator.  A user passes in two numbers, and the calculator will keep  computing the sequence until some limit is reached.

Ben coded up this implementation but complained that as soon as he  ran it, he got an error. Something about the limit variable. What's  wrong with the code?

```ruby
limit = 15

def fib(first_num, second_num)
  while first_num + second_num < limit
    sum = first_num + second_num
    first_num = second_num
    second_num = sum
  end
  sum
end

result = fib(0, 1)
puts "result is #{result}"
```

The error here is that the `limit` variable has not be defined inside the method `fib`. 

How would you fix this so that it works?

<ins>**My fix**</ins>: 

```ruby
def fib(first_num, second_num)
  limit = 15
  while first_num + second_num < limit
    sum = first_num + second_num
    first_num = second_num
    second_num = sum
  end
  sum
end

result = fib(0, 1)
puts "result is #{result}"
```

<ins>**LaunchSchool explanation**</ins>:

Ben defines `limit` before he calls `fib`. But `limit` is not visible in the scope of `fib` because `fib` is a method and does not have access to any local variables outside of its scope.

You can make `limit` an additional argument to the definition of the `fib` method and pass it in when you call `fib`.

```ruby
def fib(first_num, second_num, limit)
  while first_num + second_num < limit
    sum = first_num + second_num
    first_num = second_num
    second_num = sum
  end
  sum
end

result = fib(0, 1, 15)
puts "result is #{result}"
```