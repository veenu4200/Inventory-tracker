# Inventory-tracker
# Define an empty list to store inventory items as immutable tuples
inventory = []

# Function to add an item to the inventory
def add_item():
    item_name = input("Enter item name: ")
    quantity = int(input("Enter quantity: "))
    price = float(input("Enter price: "))
    # Create a new tuple and add it to the inventory
    new_item = (item_name, quantity, price)
    inventory.append(new_item)
    print(f"Item '{item_name}' added.")

# Function to remove an item from the inventory
def remove_item():
    item_name = input("Enter item name to remove: ")
    # Create a new list without the item to remove
    global inventory
    inventory = [item for item in inventory if item[0] != item_name]
    print(f"Item '{item_name}' removed.")

# Function to display the inventory sorted by item name
def display_inventory():
    print("\nInventory List:")
    # Sort the inventory by item name (alphabetical order)
    sorted_inventory = sorted(inventory, key=lambda item: item[0])
    total_value = 0  # Initialize total value of inventory

    # Display each item and calculate total value
    for item in sorted_inventory:
        item_name, quantity, price = item
        print(f"{item_name}: Quantity = {quantity}, Price = {price:.2f}")
        total_value += quantity * price  # Add the value of this item to total value

    print(f"Total Inventory Value: {total_value:.2f}")

# Main program loop
while True:
    print("\nInventory Management")
    print("1. Add Item")
    print("2. Remove Item")
    print("3. Display Inventory")
    print("4. Exit")

    choice = input("Enter your choice (1-4): ")

    if choice == "1":
        add_item()
    elif choice == "2":
        remove_item()
    elif choice == "3":
        display_inventory()
    elif choice == "4":
        print("Goodbye!")
        break
    else:
        print("Invalid choice. Please try again.")
