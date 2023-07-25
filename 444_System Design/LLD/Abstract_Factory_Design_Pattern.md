# What is Abstract Factory pattern ?

## Definition:
Abstract factory is nothing but **a factory of factories** . 

## Diagram:
![[Abstract-factory.svg]]

## Explanation:
From the diagram above you can figure out that there is a **Vehicle factory** which produces different vehicles ,but there are different types of factories too. So **There is a Factory 2** class which implements a method called *getFactory* to give us a certain factory based on certain conditions.
