# Circular-queue-

#include<iostream>
using namespace std;
struct Node
{
int data;
struct Node *next;
};
Node *front = NULL;
Node *rear = NULL;
void enqueue(int val)
{
if(front==NULL || rear==NULL)
{
Node *newNode;
newNode = new Node;
newNode->data = val;
newNode->next = NULL;
front = newNode;
rear = newNode;
}
else
{
Node *newNode;
newNode = new Node;
newNode->data = val;
rear->next = newNode;
newNode->next = front;
rear = newNode;
}
}
void dequeue()
{
Node *n;
n = front;
front = front->next;
delete(n);
}
void display()
{
Node *ptr;
ptr = front;
do
{
cout<< ptr->data <<" ";
ptr = ptr->next;
}
while(ptr != rear->next);
cout<<endl;
cout<<endl;
}
int main(void)
{
int ch,val;
 cout<<"1)Insert\n";
 cout<<"2)Delete\n";
 cout<<"3)Display\n";
 cout<<"4)Exit\n";
 do 
{
 cout<<"Enter choice : "<<endl;
 cin>>ch;
 switch(ch) 
{
 case 1:
cout<<"Input for insertion: "<<endl;
cin>>val;
enqueue(val);
break;
 case 2:
dequeue();
break;
 case 3:
display();
break;
 case 4:
 cout<<"Exit\n";
 break;
 default: cout<<"Incorrect!\n";
 }
 }while(ch != 4);
 return 0;
}
