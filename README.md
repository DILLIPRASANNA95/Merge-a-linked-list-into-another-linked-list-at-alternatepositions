# Merge-a-linked-list-into-another-linked-list-at-alternatepositions
class Node:
    def __init__(self, data=None):
        self.data = data
        self.next = None


def merge_alternate(head1, head2):
    if not head1:
        return head2
    if not head2:
        return head1

    current1 = head1
    current2 = head2
    while current1 and current2:
        next1 = current1.next
        next2 = current2.next

        current2.next = next1
        current1.next = current2

        current1 = next1
        current2 = next2

    return head1


def print_linked_list(head):
    current = head
    while current:
        print(current.data, end=" -> ")
        current = current.next
    print("None")


head1 = Node(1)
head1.next = Node(2)
head1.next.next = Node(3)

head2 = Node(4)
head2.next = Node(5)
head2.next.next = Node(6)

print("First Linked List:")
print_linked_list(head1)

print("Second Linked List:")
print_linked_list(head2)

head1 = merge_alternate(head1, head2)

print("Merged Linked List:")
print_linked_list(head1)
