# singlelinkedlist
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def insert_begin(self, value):
        new_node = Node(value)
        new_node.next = self.head
        self.head = new_node
        print(f"Inserted {value} at the beginning.")

    def insert_middle(self, prev_node, value):
        if prev_node is None:
            print("Previous node cannot be None.")
            return
        new_node = Node(value)
        new_node.next = prev_node.next
        prev_node.next = new_node
        print(f"Inserted {value} after the specified node.")

    def insert_end(self, value):
        new_node = Node(value)
        if self.head is None:
            self.head = new_node
            return
        temp = self.head
        while temp.next is not None:
            temp = temp.next
        temp.next = new_node
        print(f"Inserted {value} at the end.")

    def delete_begin(self):
        if self.head is None:
            print("List is empty.")
            return
        temp = self.head
        self.head = temp.next
        temp = None
        print("Deleted the first node.")

    def delete_middle(self, prev_node):
        if prev_node is None or prev_node.next is None:
            print("Invalid node.")
            return
        temp = prev_node.next
        prev_node.next = temp.next
        temp = None
        print("Deleted the specified node.")

    def delete_end(self):
        if self.head is None:
            print("List is empty.")
            return
        if self.head.next is None:
            self.head = None
            print("Deleted the last node.")
            return
        temp = self.head
        while temp.next.next is not None:
            temp = temp.next
        temp.next = None
        print("Deleted the last node.")

    def display_list(self):
        temp = self.head
        print("List:", end=" ")
        while temp is not None:
            print(temp.data, end=" ")
            temp = temp.next
        print()

    def search_element(self, value):
        temp = self.head
        pos = 1
        while temp is not None:
            if temp.data == value:
                print(f"Element {value} found at position {pos}.")
                return
            temp = temp.next
            pos += 1
        print(f"Element {value} not found in the list.")

if __name__ == "__main__":
    linked_list = LinkedList()
    
    while True:
        print("\nLinked List Operations")
        print("1. Insert at beginning")
        print("2. Insert in the middle")
        print("3. Insert at end")
        print("4. Delete from beginning")
        print("5. Delete from middle")
        print("6. Delete from end")
        print("7. Display list")
        print("8. Search for an element")
        print("9. Exit")
        
        choice = int(input("Enter your choice: "))
        
        if choice == 1:
            value = int(input("Enter value to insert: "))
            linked_list.insert_begin(value)
        elif choice == 2:
            value = int(input("Enter value to insert: "))
            # For demonstration, let's insert in the middle after the first node
            linked_list.insert_middle(linked_list.head, value)
        elif choice == 3:
            value = int(input("Enter value to insert: "))
            linked_list.insert_end(value)
        elif choice == 4:
            linked_list.delete_begin()
        elif choice == 5:
            # For demonstration, let's delete the second node
            if linked_list.head is not None and linked_list.head.next is not None:
                linked_list.delete_middle(linked_list.head)
            else:
                print("Insufficient nodes for mid deletion.")
        elif choice == 6:
            linked_list.delete_end()
        elif choice == 7:
            linked_list.display_list()
        elif choice == 8:
            value = int(input("Enter value to search: "))
            linked_list.search_element(value)
        elif choice == 9:
            break
        else:
            print("Invalid choice.")
