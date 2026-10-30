#econ2302/chapter4 

## Demand
### Quantity Demanded
Amount of a good that buyers are willing and *able* to purchase, MaxWTP[^1]

### Law of demand
Other things equal - Ceteris paribus
When the price of a good rises, the quantity demanded of the good falls.
When the price falls, the quantity demanded rises

### Market Demand
Sum of all individual demands for a good or service

**Market Demand Curve**: Sum the individual demand curves horizontally
- To find the total quantity demanded at any price, we add the individual quantities


[^1]: Max Willingness to Pay

---
## Demand Schedule
### Demand Schedule
a table, shows the relationship between the price of a good and the quantity demanded

*ex* Sams Demand for Lattes

| Price of Lattes | Quantity of Lattes demanded |
|:---------------:|:---------------------------:|
|      $0.00      |             16              |
|      1.00       |             14              |
|      2.00       |             12              |
|      3.00       |             10              |
|      4.00       |              8              |
|      5.00       |              6              |
|      6.00       |              4              |

*Notice that Sam's preference obey the law of demand.*

 ---
## Demand Curve
```chart
type: line
labels: [4,6,8,10,12,14,16]
series:
  - title: Sams Demand Curve
    data: [6,5,4,3,2,1,0]
tension: 1.0
width: 80%
labelColors: false
fill: false
beginAtZero: false
legend: true
xTitle: Quantity of Lattes
yTitle: Price of Lattes ($)
```
*Each point represents a quantity demanded at a certain price.*

---
## Market Demand vs Individual Demand
Suppose Sam and Dean are the only two buers in the market for lattes. (Q<sup>d</sup> = Quantity demanded)

### Market Demand Schedule

| Price | Sam's Q<sup>d</sup> | Dean's Q<sup>d</sup> | Market Q<sup>d</sup> |
|:-----:|:-------------------:|:--------------------:|:--------------------:|
|   0   |         16          |          8           |          24          |
|   1   |         14          |          7           |          21          |
|   2   |         12          |          6           |          18          |
|   3   |         10          |          5           |          15          |
|   4   |          8          |          4           |          12          |
|   5   |          6          |          3           |          9           |
|   6   |          4          |          2           |          6           |

### Market Demand Curve

```chart
type: line
labels: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24]
series:
  - title: Market Demand
    data: [null,null,null,null,null,null,6,null,null,5,null,null,4,null,null,3,null,null,2,null,null,1,null,null,0]
  - title: Sam's Demand
    data: [null,null,null,null,6,null,5,null,4,null,3,null,2,null,1,null,0]
  - title: Dean's Demand
    data: [null,null,6,5,4,3,2,1,0]
tension: 1
width: 81%
labelColors: false
fill: false
beginAtZero: true
spanGaps: true
xTitle: Q (Quantity Demanded)
yTitle: P (Price $)
```
---
## Demand Curve Shifters
### The demand curve
Shows how price affects quantity demanded, other things being equal

### These "other things" are non-price determinants of demand
Things that determine buyers' demand for a good, other than the good's price

### Changes in them shift the D curve

### Number of Buyers
increase in # of buyers
- increases quantity demanded at each price
- shifts the D curve to the right

Decrease in # of buyers
- decreases quantity demanded at each price
- shifts D curve to the left

Suppose the number of buyers increases. Then, at each P, Q<sup>d</sup> will increase (by 5 in this example)

```chart
type: line
labels: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30]
series:
  - title: Market Demand
    data: [null,null,null,null,null,null,6,null,null,5,null,null,4,null,null,3,null,null,2,null,null,1,null,null,0]
  - title: Market Demand (More Buyers)
    data: [null,null,null,null,null,null,null,null,null,null,null,6,null,null,5,null,null,4,null,null,3,null,null,2,null,null,1,null,null,0]
tension: 1
width: 81%
labelColors: false
fill: false
beginAtZero: true
spanGaps: true
xTitle: Q (Quantity Demanded)
yTitle: P (Price $)
```

 ### Income 
 Normal good, other things constant
- an increase in income leads to an increase in demand: shifts the D curve to the right
*ex*. sports cars, top shelf booze

Inferior good, other things constant
- an increase in income leads to a decrease in demand: shifts D curve to the left
*ex*. Ramen noodles, cheap booze, cheap alternatives

### Prices of related goods / substitutes
Two goods are substitutes if
- An increase in the price of one leads to an increase in the demand of another

*Ex*. pizza and hamburgers
- An increase in the price of pizza increases demand for hamburgers, shifting hamburger demand curve to the right

### Price of related goods / complements
Two goods are complements if
- an increase in the price of one leads to a decrease in demand for the other

*Ex*. computers and software
- If the price of computers rises, people buy fewer computers, and therefore less software. Software demand curve shifts left.

### Tastes
Anything that causes a shift in tastes toward a good will increase demand for that good and shift its D curve to the right
*Ex*.
- the Atkins diet became popular in the 90s, caused an increase in demand for eggs, thereby shifting the egg demand curve to the right.

### Expectations about the future
Expectation of an increase in income, increases current demand
Expectations of higher prices, increase in current demand
*Ex*.
- If people expect their incomes to rise, their D curve for meals at nice restaurants may increase now

---
## Summary: Variables that influence buyers

| Variable                 | A change in this variable...                 |
| ------------------------ | -------------------------------------------- |
| Price of the good itself | Represents a movement along the demand curve |
| Income                   | Shifts the demand curve                      |
| Prices of related goods  | Shifts the demand curve                      |
| Tastes                   | Shifts the demand curve                      |
| Expectations             | Shifts the demand curve                      |
| Number of Buyers         | Shifts the demand curve                      |
