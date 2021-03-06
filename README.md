# Recursion Problems

## Definitions
Define the following:
- Recursion - Recursion occurs when a method calls itself. A recursive algorithm always has a base case and a recursive case.
- Recursive Case - Each recursive call gets you closer to a problem scope for which an answer is known.
- Base Case - A base case is the point at which the recursive calls stop. The returned value can then be returned back to the previous calls.
- Activation Chain/Function Call Stack - Each function call is added to the call stack which takes space in the stack memory.
- Activation Record/Function Call - An activation record is each individual function call that was made.
- Infinite Recursion/Stack Overflow/Stack too deep - This happens when a base case is not defined. The recursive algorithm keeps on making recursive calls which are added to the stack memory which eventually overflows.
- Tail Recursion - A algorithm with tail recursion returns the value immediately and does not need to do any additional computation.

## Tracing through a recursive method. Time & Space complexity.
### Trace #1
```ruby
def mystery1(n)
  if n == 1
    return n
  else
    return n + mystery1(n-1)
  end
end
```

- What is mystery1(5)? --> 15
- What is mystery1(10)? --> 55
- What is mystery1(0)? --> stack overflow - infinity loop
- What is the time complexity of mystery1(n)? O(n)
- What is the space complexity of mystery1(n)? O(n)

### Trace #2
```ruby
def mystery2(n)
  if n < 10
    return n
  else
    return (n%10) + mystery2(n/10)
  end
end
```

- What is mystery2(123)? --> 6
- What is mystery2(9005)? --> 14
- What is mystery2(-123)? --> -123
- What is the time complexity of mystery2(n)? O(n)
- What is the space complexity of mystery2(n)? O(n)
- _Added Fun: How could we make `mystery2(-123)` work the way we might expect it to work instead of the way it does?_

### Trace #3
```ruby
def mystery3(n)
  if n == 0
    return 100
  elsif n == -1
    return 200
  end
  if n%2 == 0
    return mystery3(n/2)
  else
    return mystery3(n-1)
  end
end
```

- What is mystery3(1)? --> 100
- What is mystery3(13)? --> 100
- What is mystery3(-6)? --> 200
- What is the time complexity of mystery3(n)? O(abs(n)/2)
- What is the space complexity of mystery3(n)? O(abs(n)/2)

### Trace #4
```ruby
def mystery4(b, e)
  if e == 0
    return 1
  else
    return b * mystery4(b, e-1)
  end
end
```

- What is mystery4(10, 2)? --> 100
- What is mystery4(4, 3)? --> 64
- What is mystery4(5, 0)? --> 1
- What is the time complexity of mystery4(b, e)? O(e)
- What is the space complexity of mystery4(b, e)? O(e)

### Trace #5
```ruby
def mystery5(s)
  if s.length == 0
    return ""
  else
    return "*" + mystery5(s[1..-1])
  end
end
```

- What is mystery5("hi")? --> "**"
- What is mystery5("")? --> ""
- What is mystery5("Hi, there!")? "**********"
- What is the time complexity of mystery5(s)? --> O(n)
- What is the space complexity of mystery5(s)? --> O(n)
- _Added Fun: How could we make only alphabetic characters to be changed to stars?_

### Trace #6
```ruby
def mystery6(s)
  if s == nil || s.length == 0
    return ""
  else
    space = 0
    until space >= s.length || s[space] == " "
      space += 1
    end
    return mystery6(s[(space+1)..-1]) + " " + s[0...space]
  end
end
```

- What is mystery6("goodnight moon")? --> "moon goodnight"
- What is mystery6("Ada Developers Academy")? --> "Academy Developers Ada"
- What is mystery6("Hi, there!")? --> "there! Hi,"
- What is the time complexity of mystery6(s)? O(n)
- What is the space complexity of mystery6(s)? O(n)
- _Added Fun: How could we make the reversal happen by letter, instead of by word (i.e. Make it so that mystery6("goodnight moon") returned "noom thgindoog")?_

### Trace #7
```ruby
def mystery7(word)
  if word.length < 2
    return true
  elsif word[0] != word[-1]
    return false
  else
    return mystery7(word[1..-2])
  end
end
```

- What is mystery7("cupcake")? --> false
- What is mystery7("detected")? --> false
- What is mystery7("eye")? --> true
- What is the time complexity of mystery7(word)? O(n/2)
- What is the space complexity of mystery7(word)? O(n/2)
