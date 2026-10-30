#econ2302/chapter4 

## Supply
### Quantity supplied
Amount of a good sellers are willing and *able* to sell, MinWTA[^2]

### Law of Supply
Other things Equal, When the price of a good rises, the quantity supplied of the good rises.
When the price falls, the quantity supplied falls.

[^2]: Minimum Willingness to Accept

## Supply Schedule
A table, shows the relationship between the price of a good and the quantity supplied.
*Ex*. Starbucks supply of lattes

| Price of lattes | Quantity supplied of lattes |
| --------------- | --------------------------- |
| 0.00            | 0                           |
| 1.00            | 3                           |
| 2.00            | 6                           |
| 3.00            | 9                           |
| 4.00            | 12                          |
| 5.00            | 15                          |
| 6.00            | 18                          | 

*Notice that Starbucks supply schedule obeys the law of supply*

### Supply curve

```chart
type: line
labels: [0,3,6,9,12,15,18,21]
series:
  - title:  Price of Lattes
    data: [0,1,2,3,4,5,6]
tension: 0.2
width: 80%
labelColors: false
fill: false
beginAtZero: false
xTitle: Q (Quantity Supplied)
yTitle: P (Price $)
```

## Market Supply vs Individual Supply
### Market supply
Sum of the supplies of all sellers of a good or service
Market supply curve: Sum of individual supply curves horizontally

| Price | Q<sup>d</sup> Starbucks | Q<sup>d</sup> Peet's | Market Q<sup>d</sup> |
| ----- | ----------------------- | -------------------- | -------------------- |
| 0.00  | 0                       | 0                    | 0                    |
| 1.00  | 3                       | 2                    | 5                    |
| 2.00  | 6                       | 4                    | 10                   |
| 3.00  | 9                       | 6                    | 15                   |
| 4.00  | 12                      | 8                    | 20                   |
| 5.00  | 15                      | 10                   | 25                   |
| 6.00  | 18                      | 12                   | 30                   |

```chart
type: line
labels: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35]
series:
  - title: Starbucks Quantity Supplied
    data: [0,null,null,3,null,null,6,null,null,9,null,null,12,null,null,15,null,null,18]
  - title: Peet's Quantity Supplied
    data: [0,null,2,null,4,null,6,null,8,null,10,null,12]
  - title: Market Quantity Supplied
    data: [0,null,null,null,null,5,null,null,null,null,10,null,null,null,null,15,null,null,null,null,20,null,null,null,null,25,null,null,null,null,30]
tension: 1
width: 100%
labelColors: false
fill: false
beginAtZero: true
spanGaps: true
xTitle: Q (Quantity Supplied)
yTitle: P (Price $)
```

## Supply Curve Shifters

### Supply Curve
Shows how price affects quantity supplied, other things equal

### These "other things" are non-price determinants of supply
*Changes in them shift the S curve*

### Input prices
Supply is negatively related to prices of inputs
*Examples of Input Prices* - wages, prices of raw materials

A fall in input price makes production more profitable at each output price
- Firms supply a larger quantity at each price
- The S curve shifts right

Suppose the price of milk falls. At each price, the quantity of lattes supplied will increase (by 5 in this example)
```chart
type: line
labels: [0,5,10,15,20,25,30,35,40]
series:
  - title: Lattes Supplied
    data: [null,1,2,3,4,5,6]
  - title: Lattes Supplied (Milk Price Falls)
    data: [null,null,1,2,3,4,5,6]
tension: 0.2
width: 80%
labelColors: false
fill: false
beginAtZero: true
xTitle: Q (quantity supplied)
yTitle: P (Price $)
```

### Technology
Determines how much inputs are required to produce a unit of output

A cost-saving technological improvement has the same effect as a fall in input prices, shifts S curve right

### Number of sellers
An increase in the number of sellers increases the quantity supplied at each price
- Shifts S curve right

### Expectations about future
Example: Events in the middle east lead to expectations og higher oil prices
- Owners of TX oilfields reduce supply now, save inventory to sell later at a higher price
- S curve shifts left

Sellers may adjust supply[^3] when their expectations of future prices change

[^3]: If good not perishable

## Summary: Variables that Influence Sellers

| Variable                 | A Change in This Variable...                 |
| ------------------------ | -------------------------------------------- |
| Price of the good itself | Represents a movement along the supply curve |
| Input Prices             | Shifts the supply curve                      |
| Technology               | Shifts the supply curve                      |
| Expectations             | Shifts the supply curve                      | 
| Numer of Sellers         | Shifts the supply curve                      |
