24202408110118
Status: #idea
Tags:

# Use of InventoryHolder

The `InventoryHolder` in Spigot and Minecraft is not well optimized.

## Understanding InventoryHolder

The `InventoryHolder` interface in Spigot is commonly used to associate an `Inventory` with its owner. This is particularly useful when creating custom inventories for plugins. However, its usage can lead to unintended performance issues when performed on Block Entities. 

## Snapshotting
Snapshots of the InventoryHolder are taken each time it is called, if the InventoryHolder is a BlockEntity, that leads to the inventory itself being snapshotted. This is significant in terms of lag as it would cause custom items (such as brews) to be cloned on every call of the inventory holder(e.g: On Click events.)



### Key Points:

- **Memory Consumption**: Items with large amounts of metadata being cloned continuously can lead to memory utilisation being abnormally high. 
- **Serialization Overhead**: When inventories are saved or transferred, items with extensive metadata take longer to serialize and deserialize, hence causing tps issues if snapshotted frequently.
- **Event Handling**: Hence, InventoryHolder getter methods should be used sparingly and, if possible, not at all if there are alternatives. 

## Conclusion

While `InventoryHolder` is an occasionally useful call, but its use was never intended for checking purposes, as the act of retrieving an Inventory Holder is expensive. 

## References

- [Why Items With Lots of Metadata Actually Cause Lag - An InventoryHolder PSA](https://www.spigotmc.org/threads/why-items-with-lots-of-metadata-actually-cause-lag-an-inventoryholder-psa.607711/)