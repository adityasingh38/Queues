
# Queues

A queue is a data structure that stores a collection of elements in a specific order, similar to a line of people waiting in a queue. The first element added to the queue is the first one to be removed, in a first-in-first-out (FIFO) order.

In C, a queue can be implemented using an array or a linked list. 

![Queues_circular](https://user-images.githubusercontent.com/88421625/234427742-4fec9bb4-2625-45e5-934c-eb1e148d4b4a.png)

Here is an implementation of a queue using an array:
```bash
#define MAX_SIZE 100 // maximum size of the queue

int queue[MAX_SIZE]; // the queue array
int front = -1; // front of the queue
int rear = -1; // rear of the queue

// function to add an element to the queue
void enqueue(int x) {
    if (rear == MAX_SIZE - 1) {
        printf("Error: queue overflow\n");
        return;
    }
    if (front == -1) {
        front = 0;
    }
    rear++;
    queue[rear] = x;
}

// function to remove an element from the queue
void dequeue() {
    if (front == -1 || front > rear) {
        printf("Error: queue underflow\n");
        return;
    }
    front++;
}

// function to get the front element of the queue
int peek() {
    if (front == -1 || front > rear) {
        printf("Error: queue is empty\n");
        return -1;
    }
    return queue[front];
}

// function to check if the queue is empty
int is_empty() {
    if (front == -1 || front > rear) {
        return 1;
    } else {
        return 0;
    }
}

```
In this implementation, the queue is stored as an integer array ‘queue’ with a maximum size of ‘MAX_SIZE’. The front and rear of the queue are represented by the variables ‘front’ and ‘rear’, respectively.
The ‘enqueue’ function adds an element to the rear of the queue. It first checks if the queue is already full, in which case it prints an error message and returns. Otherwise, it increments ‘rear’ and adds the new element to the queue.
The ‘dequeue’ function removes the front element from the queue. It first checks if the queue is empty or if the front has exceeded the rear, in which case it prints an error message and returns. Otherwise, it increments ‘front’.
The ‘peek’ function returns the front element of the queue without removing it. It first checks if the queue is empty or if the front has exceeded the rear, in which case it prints an error message and returns -1.
The ‘is_empty’ function checks if the queue is empty by checking if ‘front’ is equal to -1 or if front has exceeded rear. If the queue is empty, it returns 1, otherwise it returns 0.
It is important to note that this implementation has a fixed maximum size for the queue. If the queue becomes full, new elements cannot be added until some elements are removed. If dynamic memory allocation is desired, a linked list implementation of the queue may be used instead.
## Key Points
Here are some important points about Queues:

•	The algorithm consists of two nested loops. The outer loop iterates over the elements of the array, while the inner loop finds the smallest element in the unsorted portion of the array.

•	After finding the smallest element, the algorithm swaps it with the first element of the unsorted portion of the array. This effectively moves the smallest element to the front of the array.

•	This process is repeated until the entire array is sorted. At each iteration of the outer loop, the sorted portion of the array grows by one element.

•	Selection sort has a worst-case time complexity of O(n^2), where n is the size of the array. This means that the algorithm is not efficient for large arrays.

•	However, selection sort has some advantages over other sorting algorithms in certain situations. For example, it requires only a small amount of additional memory to sort an array in place, and it is relatively easy to implement and understand.

•	When implementing selection sort in C, it is important to be careful about array indexing and to use temporary variables for swapping elements. It is also a good practice to test the algorithm on a variety of input sizes and types to ensure that it works correctly.




# Code

```bash
// Program to implement a queue using arrays

#include <stdio.h>

#define MAX 10

int queue[MAX];
int front = -1;
int rear = -1;

void enqueue();
void dequeue();
void display();

int main()
{
	int choice;
	char c;
	
	printf("Queue Operations: \n");
	printf("1. enqueue\n2. dequeue\n3. display\n");
	
	do
	{	
		printf("\nEnter 1, 2 or 3 to perform a queue operation from the list above, or 4 to exit: ");
		scanf("%d", &choice);
	
		switch(choice)
		{
			case 1:
				{
					printf("\nEntered choice: %d\n", choice);
					enqueue();
					break;
				}
			case 2:
				{
					printf("\nEntered choice: %d\n", choice);
					dequeue();
					break;
				}
			case 3:
				{
					printf("\nEntered choice: %d\n", choice);
					display();
					break;				
				}
			case 4:
				{
					printf("\nTerminating...");
					break;
				}
			default:
				{
					printf("\nInvalid choice. Terminating...");
					break;
				}		
		}
		
	}while(choice == 1 || choice == 2 || choice == 3);
	
	return 0;
}

void enqueue()
{
	int n;
	
	printf("Enter a value to be entered in the queue: ");
	scanf("%d", &n);
	
	if(rear == (MAX - 1))
	{
		printf("queue full, cannot enter element.\n\n\n");
	}
	else
	{
		front == -1 ? front++ : 0;
		rear++;
		queue[rear] = n;
		printf("Value entered.\n\n\n");
	}
	
	return;	
}

void dequeue()
{
	int i;
	
	if(front < 0)
	{
		printf("queue empty, cannot delete element.\n\n\n");
	}
	else if(front >= 0 && front != rear)
	{
		// entering 0 to denote a deleted element (temporary - fix this)
		queue[front] = 0;
		front++;
		printf("Value deleted.\n\n");
	}
	else if(front == rear)
	{
		front = -1;
		rear = -1;
		printf("Value deleted.\nQueue empty. Reset front and rear indices to -1.\n\n\n");
	}
	
	return;
}

void display()
{
	int i;
	
	printf("Available queue: \n");
	
	for(i = front; i <= rear; i++)
	{
		printf("%d\t", queue[i]);
	}
	
	printf("\n\n\n");
	
	return;
}
```
## Output

![OP1](https://user-images.githubusercontent.com/88421625/234427547-51610250-cfb7-4fb7-b1ed-4399be6cf595.png)

![OP2](https://user-images.githubusercontent.com/88421625/234427557-b4a5b1ba-1c37-4c7b-a155-f2c35783f775.png)
