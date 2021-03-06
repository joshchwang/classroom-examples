# Test Solutions

## Chapter 3 Quiz (Makeup)
**#5.** Write a program that takes user input asking the user for their name and age. 
The program will output a message exactly in the format: `"Hello, {name}, next year you will be {age} years old!"`
```python
name = input("Please enter yor name:")
age = int(input("Please enter your age:"))
message = "Hello, {}, next year you will be {} years old!".format(name, age+1)
print(message)
```

**#6.** Write a program that will take the length and width of a 
rectangle as user input and output it's area. 
```python
length = float(input("length:"))
width = float(input("width:"))
area = length * width
print(f"The area is {area} units squared.")
```

## Loops Test
### Problem #1
#### Version 1 (and 2)
Write a program that outputs a temperature conversion chart from celsius to fahrenheit, starting from -20℃ increasing every 5℃ to 40℃, with two decimal places for the fahrenheit value.  It should have headers and be formatted based on the image below.  The celsius to fahrenheit conversion is  F = C 9/5 + 32.
```python

print("Celsius\t\tFahrenheit")
print("-" * 30)

for celsius in range(-20, 41, 5):
    fahrenheit = celsius * 9/5 + 32
    print(celsius, "\t\t", fahrenheit)
```

### Problem #2
#### Version1
You have been away traveling in the U.S and now you are ready to return home.  You’ve done a lot of shopping and are worried about paying duty fees when you enter back into Canada.  Canada Customs allows $250 worth of purchased goods for each day abroad.  A fee of 13% of the total value of purchased goods must be paid if the total value is greater than the allowable amount.   For example, if you travel for 7 days and you purchase a total of $1,946, a fee of $252.98 must be paid (since the limit for travelling 7 days is $250 x 7 days= $1750)

Write a program that allows you to enter the amount spent for each day of your trip, stopping once you enter -1.  Output the total days travelled and the total amount spent.  If a fee is owed based on the total amount spent and the number of days travelled output the fee.  Otherwise output “Phew, you do not have to pay a fee”.

Sample runs of the program would be:

Sample Run 1:
```
Enter a daily spent amount (-1 to stop): 200
Enter a daily spent amount (-1 to stop): 303
Enter a daily spent amount (-1 to stop): 276
Enter a daily spent amount (-1 to stop): 309
Enter a daily spent amount (-1 to stop): -1
Total Days travelled: 4
Total amount spent: $1088.00
You owe a fee of $141.44
```
Sample Run 2:
```
Enter a daily spent amount (-1 to stop): 176
Enter a daily spent amount (-1 to stop): 255
Enter a daily spent amount (-1 to stop): 320
Enter a daily spent amount (-1 to stop): 45
Enter a daily spent amount (-1 to stop): 200
Enter a daily spent amount (-1 to stop): -1
Total Days travelled: 5
Total amount spent: $996.00
Phew, you do not owe a fee
```

```python
total = 0
days = 0
daily_amt = 0

while True:
    daily_amt = float(input("Enter a daily spent amount (-1 to stop):"))

    if daily_amt == -1:
        break

    days += 1
    total += daily_amt

print("Total Days travelled:", days)
print("Total amount spent: $", total)

if total > 250*days:
    tax = total * 0.13
    print("You owe a fee of $", tax)
else:
    print("Phew, you do not owe a fee")
```

#### Version 2
Your startup company is to a fitness app that helps people track 
consumed calories as they eat throughout out the day.  

The app will:
- prompt the user for a consumed calories budget
- continuously prompt for calorie consumption entries 
until they enter -1  or they’ve surpassed their budget
- if they’ve consumed within 300 calories of their budget 
output the warning “You are approaching your daily limit”

Once they’ve stopped entering calorie entries, 
output the remaining calories to consume if they are under budget.    

If they’ve consumed over  their budget, 
output the the amount over and the message “Time to go for a run.”

```python
total = 0
budget = int(input("Enter your calorie budget for the day:"))

while True:
    item_calories = int(input("Enter the calories consumed (-1 to stop):"))

    if item_calories == -1:
        break

    total += item_calories

    if total > budget - 300:
        print("You are approaching your daily limit")

if total <= budget:
    print(f"Good job, you have {budget - total} calories remaining")
else:
    print(f"You are {total - budget} calories over budget.")
    print("Time to go for a run.")
```

### Version 3
#### Problem 1
Write a program that takes in a year future_year (assume it is in the future) and outputs a table from the current year (2018) to future_year,  listing the year and distance from the park border to the desert edge.

Sample Run
```
Enter the future year: 2026
Year: 2018, Desert Edge Distance: 3000
Year: 2019, Desert Edge Distance: 2952
Year: 2020, Desert Edge Distance: 2904
Year: 2021, Desert Edge Distance: 2856
Year: 2022, Desert Edge Distance: 2808
Year: 2023, Desert Edge Distance: 2760
Year: 2024, Desert Edge Distance: 2712
Year: 2025, Desert Edge Distance: 2664
Year: 2026, Desert Edge Distance: 2616
```

```python
# with a for-loop
distance = 3000

future_year = int(input("Enter the future year:"))

for year in range(2018, future_year+1):
    print(f"Year: {year}, Desert Edge Distance: {distance}")
    distance -= 48
```
```python
# with a while loop
distance = 3000
year = 2018

future_year = int(input("Enter the future year:"))

while year <= future_year:
    print(f"Year: {year}, Desert Edge Distance: {distance}")
    distance -= 48
    year += 1
```

#### Problem 2
It is expected that the park will need to close when the desert edge is within 500m from the park border.  Write a separate program that uses a while loop to compute the year the lodge will need to close.

Sample Run
```
The park will need to close in xxxx. 
```

Where xxxx is the computed year.

```python
distance = 3000
year = 2018

while distance > 500:
    distance -= 48
    year += 1

print(year)
```
