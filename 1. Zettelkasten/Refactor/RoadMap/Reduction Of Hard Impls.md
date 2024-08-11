24202408092046
Status: #idea
Tags: 

# Reduction Of Hard Implementations
As per the  team philosophy of [[Interface Philosophy |handling interfaces only]], one of the primary goals of the refactor will be to reduce implementation as much as possible, replacing them with interfaces throughout Brewery.

This means then, when we refactor certain aspects of brewery, or we all split off into different features to work on *everything is guaranteed to still work, as interfaces from things other than your branch will be off-limits*.

Furthermore, it means that when we do entirely new implementations of an interface, literally 1 or 2 lines will change as opposed to potentially hundreds. 

It also, excitedly, opens the door to new types of mechanics in future to be added, as long as the implement current interfaces as part of their structure. 
# References