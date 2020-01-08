# **Ecommerce Solution**

the below is inital proposal for building E-Commerce system

## **Requirement**

Implement the code for a checkout system with a pricing schema in
a supermarket. This exercise is not about framework know-how, but in order to make reviewing easier for us, please use:

* Java
* Maven or Gradle

for the implementation. This exercise describes pricing schemes and requirements for enhance ability for a system that
calculates the total cost of a shopping cart based on a set of pricing rules. The items in a
supermarket is identified by using Stock Keeping Units or SKUs. For this, we will use individual
letters of the alphabet (e.g. A, B, C) and the items are priced individually. In addition to that some items are multi priced: buy n of them and they will cost you y Euro.
For example: Item 'A' costs 40 Cent individually, but this week there is a special offer: buy three 'A's and they will cost you 1 Euro

| SKU | Unit Price | Special Price |
| --- | ---------- | ------------- |
| A   | 40         | 3 for 100     |
| B   | 50         | 2 for 80      |
| C   | 25         |
| D   | 20         |

The checkout should accept items in any order. E.g. so if we scan B, A and another B, it will recognize
the two B's and price them at 80 Cent, in order to result in a total price of 1,20 Euro.
Because the pricing can change frequently, we need to be able to pass in a set of pricing rules each
time we start handling a checkout transaction.

The interface to the checkout should look like this:

```java
    var checkout = new CheckOut(pricing_rules);
    checkout.scan(item);
    checkout.scan(item);
    price = checkout.total();
```

Here is a Unit test in Java. The helper method calculatePrice let’s you specify a sequence of items
(using a string), calling the checkout's scan method for each item before returning the total price:

```java
public class TestPrice {
    public int calculatePrice(String goods) {
        CheckOut checkout = new CheckOut(rule);
            for(int i=0; i<goods.length(); i++) {
                checkout.scan(String.valueOf(goods.charAt(i)));
            }
        return checkout.total();
    }

    @Test
    public void totals() {
        assertEquals(0, calculatePrice(""));
        assertEquals(40, calculatePrice("A"));
        assertEquals(90, calculatePrice("AB"));
        assertEquals(135, calculatePrice("CDBA"));
        assertEquals(80, calculatePrice("AA"));
        assertEquals(100, calculatePrice("AAA"));
        assertEquals(140, calculatePrice("AAAA"));
        assertEquals(180, calculatePrice("AAAAA"));
        assertEquals(200, calculatePrice("AAAAAA"));
        assertEquals(150, calculatePrice("AAAB"));
        assertEquals(180, calculatePrice("AAABB"));
        assertEquals(200, calculatePrice("AAABBD"));
        assertEquals(200, calculatePrice("DABABA"));
    }

    @Test
    public void incremental() {
        CheckOut checkout = new CheckOut(rule);
        assertEquals(0, checkout.total);
        checkout.scan("A"); assertEquals(40, checkout.total);
        checkout.scan("B"); assertEquals(90, checkout.total);
        checkout.scan("A"); assertEquals(130, checkout.total);
        checkout.scan("A"); assertEquals(150, checkout.total);
        checkout.scan("B"); assertEquals(180, checkout.total);
    }
}

```

The exercise doesn’t mention the format of the pricing rules:

* How can these be specified in such a way that the checkout doesn’t know about particular items and their pricing strategies?

* How can we make the design flexible enough so that we can add new styles of pricing rules in the future?

## **Solution Architecture Overview**

<p align="center">
<img src="https://github.com/mohamedibrahim-java/idealo/blob/master/resources/Idealo Business Model.png" width="500">
</p>

* ### Catalog Service

* ### Profile Service

* ### Order Service

* ### Shopping Cart Service
  
* ### Inventory Service

* ### Payment Service
  
* ### Delivery Service
  
* ### Notification Service

* ### Promotion Service


