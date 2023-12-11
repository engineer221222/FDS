
2.
def accept_marks(A):
    n = int(input("Enter the total no.  of student: "))
    for i in range(n) :
        while True:
            x = input("Enter the marks scored in FDS for students %d : "%(i+1))
            if (x== "AB"):
                x =-1 
                break
            x = int(x)
            if(x >= 0 and x <= 30) :
                break
            else :
                print("Plz enter valid marks out of 30")
        A.append(x)
        print("Marks accepted & stored successfully");
        
def display_marks(A) :
        print("\nMarks Scored in FDS")
        for i in range(len(A)):
            if (A[i] == -1) :
                print("\tStudents %d : AB"%(i+1))
            else :
                print("\tStudents %d : %d"%(i+1,A[i]))
                
def search_set(A,X) :
        n = len(A)
        for i in range(n):
            if(A[i] == X):
                return (1)
            return(0)
        
def find_average_score_of_class(A) :
        sum = 0
        for i in range(len(A)):
            if(A[i] != -1):
                sum = sum + A[i]
            avg = sum / len(A)
            display_marks(A)
            print("\nAverage score of class is %.2f\n\n"%avg)
            
def find_highest_and_lowest_score_of_class(A):
        max = -1 
        min = 31
        for i in range(1,len(A)) :
            if(max < A[i]) :
                max = A[i]
                max_ind = i
            if(min > A[i] and A[i] != -1) :
                min = A[i]
                min_ind = i
        display_marks(A)
        print("Highest mark score of class is %d scored by student %d"%(max,max_ind+1))
        print("Lowest mark score of class is %d scored by student %d"%(min,min_ind+1))
    
def find_count_of_absent_students(A) :
        count = 0
        for i in range(len(A)):
            if(A[i] == -1):
                count += 1
        display_marks(A)
        print("\tAbsent student count = %d"%count)
        
def main():
        FDS_Marks = []
        while True :
            print("\t\t1 : Accept FDS Marks")
            print("\t\t2 : Average score of class")
            print("\t\t3 : Highest score and lowest score of class")
            print("\t\t4 : Count of students who were absent for the best")
            print("\t\t5 : Display mark with highest frequency")
            print("\t\t6 : Exit")
            ch = int(input("Enter your choice: "))
            if (ch == 6):
                print("End of program")
                quit()
            elif (ch == 1) :
                accept_marks(FDS_Marks)
                display_marks(FDS_Marks)
            elif (ch == 2) :
                find_average_score_of_class(FDS_Marks)
            elif (ch == 3) :
                find_highest_and_lowest_score_of_class(FDS_Marks)
            elif (ch == 4) :
                find_count_of_absent_students(FDS_Marks)
            else :
                print("Wrong choice entered !! Try again")
                
main()


3.
def accept_matrix(M):  
    print("\nEnter the order of the matrix (row,col) : ")
    r= int(input("\trow = "))                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             
    c= int(input("\tcol = "))
    print("Enter the elements of the Matrix : \n")
    for i in range(r):
        A=[]
        for j in range(c):
            A.append(int(input()))
        M.append(A)
    print("Matrix accepted and stored successfully accepted ")


def display_matrix(M,r,c):      
    print("Matrix (%d,%d) : " %(r,c))
    for i in range(r):
        print("\t\t",end=' ')
        for j in range (c):
            print("%3d"%M[i][j],end=' ')
        print("")
            
def addition_matrix(M1,M2,M3,r,c):     
    for i in range(r):
        A=[]
        for j in range(c):
            A.append(M1[i][j]+M2[i][j])
        M3.append(A)


def subtraction_matrix(M1,M2,M3,r,c):       
    for i in range(r):
        A=[]
        for j in range(c):
            A.append(M1[i][j]-M2[i][j])
        M3.append(A)



def multiplication_matrix(M1,M2,M3,r1,c1,c2):      
    for i in range(r1):
        A=[]
        for j in range(c2):
            sum=0
            for k in range(c1):
                sum=sum+(M1[i][k]*M2[k][j])
            A.append(sum)
        M3.append(A)
        
        
def find_transpose_matrix(M,r,c,T):    
    for i in range(c):
        A=[]
        for j in range(r):
            A.append(M[j][i])
        T.append(A)



def main():
    while True:
        print("\t\t\t1: Accept Matrix");
        print("\t\t\t2: Display Matrix"); 
        print("\t\t\t3: Addition of Matrix");
        print("\t\t\t4: Subtraction of Matrix");
        print("\t\t\t5: Multiplication of Matrix");
        print("\t\t\t6: Transpose of Matrix");
        print("\t\t\t7: Exit ");
        
        ch=int(input("Enter your choice : "))
        M3=[]
        if (ch==7):
            print("End of program")
            break
        elif (ch==1):
            M1=[]
            M2=[]
            print("Input first matrix")
            accept_matrix(M1)
            r1=len(M1)
            c1=len(M1[0])
            print("Input Second Matrix")
            accept_matrix(M2)
            r2=len(M2)
            c2=len(M2[0])
        elif(ch==2):
            print("\tFirst ",end=' ')
            display_matrix(M1, r1, c1)
            print("\tSecond ",end=' ')
            display_matrix(M2, r2, c2)
        elif(ch==3):
            print("\tFirst ",end=' ')
            display_matrix(M1, r1, c1)
            print("\tSecond ",end=' ')
            display_matrix(M2, r2, c2)
            if(r1==r2 and c1==c2):
                addition_matrix(M1, M2, M3, r1, c1)
                print("\tAddition ")
                display_matrix(M3, r1, c1)
            else:
                print("Addition not possible (order not same) ")
                
        elif (ch==4):
            print("\tFirst ",end=' ')
            display_matrix(M1, r1, c1)
            print("\tSecond ",end=' ')
            display_matrix(M2, r2, c2)
            if(r1==r2 and c1==c2):
                subtraction_matrix(M1, M2, M3, r1, c1)
                print("\tSubtraction ")
                display_matrix(M3, r1, c1)
            else:
                print("Subtraction not possible (order not same) ")
                
        elif (ch==5):
            print("\tFirst ",end=' ')
            display_matrix(M1, r1, c1)
            print("\tSecond ",end=' ')
            display_matrix(M2, r2, c2)
            if(c1==r2):
                multiplication_matrix(M1, M2, M3, r1, c1,c2)
                print("\tMultiplication ")
                display_matrix(M3, r1, c1)
            else:
                print("Multiplication not possible ")
                
        elif (ch==6):
            print("\tFirst ",end=' ')
            display_matrix(M1, r1, c1)
            find_transpose_matrix(M1, r1, c1, M3);
            print("\tTranspose ",end=' ');
            display_matrix(M3,c1,r1)
            print("\tSecond ",end=' ')
            display_matrix(M2, r2, c2)
            M3=[]
            find_transpose_matrix(M2, r2, c2, M3);
            print("\tTranspose ",end=' ');
            display_matrix(M3,c2,r2)
            
        else:
            print("Wrong choice entered!! Try again")
            
main()      


searching.
def accept_array(A): 
   n = int(input("Enter the total no. of student : "))
   for i in range(n):
      x = int(input("Enter the  roll no of student %d : "%(i+1)))
      A.append(x)
   print("Student Info accepted successfully\n\n")
   return n

def display_array(A,n): 
   if(n == 0) :
      print("\nNo records in the database")
   else :
      print("Students  Array : ",end=' ')
      for i in range(n) :
         print("%d  "%A[i],end=' ')
      print("\n");

def Linear_Search(A,n,X) :
   for i in range(n) :
      if(A[i] == X) :
         return i      
   return -1       


def Sentinel_Search(A,n,X) :
   last = A[n-1]
   i = 0
   A[n-1] = X    
   while(A[i] != X) :
      i  = i  +1
   A[n-1] = last
   if( (i < n-1) or (X == A[n-1]) ) :
      return i   
   else :
      return -1    
   
def Recursive_binary_search(A,s,l,X):
    if(s<= l):
        mid = int((s+l)/2)
        if(A[mid] ==X):
            return mid
        else:
            if(A[mid] > X):
                return Recursive_binary_search(A,s,mid-1,X)
            else:
                Recursive_binary_search(A,s,mid+1,X)

def Iterative_binary_searc(A,n,X):
    s = 0
    l = n-1
    while(s<= l):
        mid = int((s+l)/2)
        if(A[mid]==X):
            return mid
        else:
            if(X< A[mid]):
                l = mid-1
            else:
                s = mid+1
    return -1

def Fibonacci_search(A,n,X):
    f1 = 0
    f2 = 1
    f3 = f1+ f2
    offset = -1
    while(f3>1):
        i = min(offset +f1,n-1)
        if(A[i] == X):
            return i
        else:
            if(X<A[i]):
                f3 = f1
                f2 = f2-f1
                f1 = f3-f2
            else:
                f3 = f2
                f2 = f1
                f1 = f3-f2
                offset = i
    if(f2==1 and (offset+1)<n and A[offset +1]==X):
        return offset +1
    return -1

def Main() :   
   A = []
   while True :
        print ("\t1 : Accept & Display Students info ")      
        print ("\t2 : Linear Search")
        print ("\t3 : Sentinel Search")
        print ("\t4 : Recursive_binary_search")
        print ("\t5 : Iterative_binary_search")
        print ("\t6 : Fibonacci Search")
        print ("\t7 : Exit")
        ch = int(input("Enter your choice : "))
        if (ch == 7):
            print ("End of Program")
            quit()
        elif (ch==1):
            A = []
            n = accept_array(A)
            display_array(A,n)
        elif (ch==2):
            X = int(input("Enter the roll_no to be searched : "))
            flag  = Linear_Search(A,n,X)
            if(flag == -1) :
                print("\tRoll no to be Searched not Found\n")
            else :
                print("\tRoll no found at location %d"%(flag + 1))
        elif (ch==3):
            X = int(input("Enter the roll_no to be searched : "))
            flag  = Sentinel_Search(A,n,X)
            if(flag == -1) :
                print("\tRoll no to be Searched not Found\n")
            else :
                print("\tRoll no found at location %d"%(flag + 1))            


        elif (ch==4):
                X = int(input("Enter the roll_no to be searched : "))
                flag  = Recursive_binary_search(A,0,n-1,X)
                if(flag == -1) :
                    print("\tRoll no to be Searched not Found\n")
                else :
                    print("\tRoll no found at location %d"%(flag + 1))
        elif (ch==5):
            X = int(input("Enter the roll_no to be searched : "))
            flag  = Iterative_binary_searc(A,n,X)
            if(flag == -1) :
                print("\tRoll no to be Searched not Found\n")
        elif (ch==6):
            X = int(input("Enter the roll_no to be searched : "))
            flag  = Fibonacci_search(A,n,X)
            if(flag == -1) :
                print("\tRoll no to be Searched not Found\n")
            else :
                print("\tRoll no found at location %d"%(flag + 1))
Main()



sorting.
def accept_array(A):
    n = int(input("Enter total number of student: "))
    for i in range(n):
        x=int(input("Enter First Year percentage of %d :"%(i+1)))
        A.append(x)
    print("Array accepted Successfuly!!!\n\n")    
def display_array(A):
    n=len(A)
    if(n==0):
        print("\n No record in database !! ")
    else:
        print("Array Of FE Marks :",end=' ')
        for i in range(n):
            print("%.2f "%A[i],end=' ')
        print("\n")

def partition(A,s,l):                     
    b = s+1
    e = l
    while(e >=b ):
        while(b<=l and A[s] >= A[b]):
            b = b+1
        while(A[s]<A[e]):
            e =e-1
        if(e>b):
            temp = A[e]
            A[e]=A[b]
            A[b] = temp
    temp = A[s]
    A[s] = A[e]
    A[e] = temp
    return e
def Quicksort(A,s,l):
    if(s<l):
        mid = partition(A, s, l)
        Quicksort(A, s, mid - 1)
        Quicksort(A, mid +1, l)


def selection_sort(A):
    n =len(A)
    for pos in range(n-1):
        min_ind = pos
        for i in range(pos +1,n):
            if(A[i]< A[min_ind]):
                min_ind =i
        temp = A[pos]
        A[pos] = A[min_ind]
        A[min_ind] = temp

        
def bubble_sort(A):
    n = len(A)
    for Pass in range(1,n):
        for i in range(n-Pass):
            if(A[i]<A[i+1]):
                temp=A[i]
                A[i]=A[i+1]
                A[i+1]=temp

def Main():
    A = []
    while True:
        print ("\t1: Accept & Display the FE Marks")
        print ("\t2: Quick sort ascending order and display top five scores")
        print("\t 3. Selection sort order :\n")
        print("\t 4.Bubble sort order with top 5 percentage:\n")

        print ("\t5: Exit")
        ch= int(input("Enter your choice: "))
        if (ch == 5):
            print ("End of Program")
            quit()
        elif (ch ==1):
            A = []
            accept_array(A)
            display_array(A)
        elif (ch==2):
            print("Marks before sorting")
            display_array(A)
            n = len(A)
            Quicksort(A,0,n-1)
            print("Marks after sorting")
            display_array(A)
            if(n >= 5):
                print("Top Five Scores: ")
                for i in range(n-1,n-6,-1):
                    print("\t%.2f"%A[i])
            else:
                print("Top Scorers: ")
                for i in range(n-1,-1,-1) :
                    print("\d%.2" %A[1])

            
        elif(ch == 3):
            print("precentage before sorting:")
            display_array(A)
            selection_sort(A)
            print("percentage after sorting:")
            display_array(A)
        elif(ch == 4):
            print("precentage before sorting:")
            display_array(A)
            bubble_sort(A)
            print("percentage after sorting:")
            display_array(A)
            if(len(A) >= 5):
                print("top percentage :")
                for i in range(5):
                    print("\t%.2f"%A[i])
            else:
                print("top scorer")
                for i in range(5):
                    print("\t%.2f"%A[i])
        else:
            print("wrong choice")

Main()





9.palindrome
#include<iostream>
#include<string.h>
#define max 50
using namespace std;

class STACK
{
	private:
		char a[max];
		int top;
	
	public:
		STACK()
		{
			top=-1;	
		}	
		
		void push(char);
		void reverse();	
		void convert(char[]);
		void palindrome();
};

void STACK::push(char c)
{
	top++;
	a[top] = c;
	a[top+1]='\0';
	
	cout<<endl<<c<<" is pushed on stack ...";
}

void STACK::reverse()
{
	char str[max];
	
	cout<<"\n\nReverse string is : ";
		
	for(int i=top,j=0; i>=0; i--,j++)
	{
		cout<<a[i];
		str[j]=a[i];
	}
	
	cout<<endl;
}


void STACK::convert(char str[])
{
	int j,k,len = strlen(str);

	for(j=0, k=0; j<len; j++)
	{
		if( ( (int)str[j] >= 97 && (int)str[j] <=122 ) || ( (int)str[j] >= 65 && (int)str[j] <=90 ))
		{
			if( (int)str[j] <=90 )
			{
				str[k] = (char)( (int)str[j] + 32 );
			}else
			{
				str[k] = str[j];				
			}

			k++;			
		}
	}
	str[k]='\0';

	cout<<endl<<"given String : "<<str<<"\n";
}




void STACK::palindrome()
{	
	char str[max];
	int i,j;		

	for(i=top,j=0; i>=0; i--,j++)
	{
		str[j]=a[i];
	}
	str[j]='\0';
	
	
	if(strcmp(str,a) == 0)
		cout<<"\n\nString is palindrome...";
	else
		cout<<"\n\nString is not palindrome...";
}


int main()
{
	STACK stack;

	char str[max];
	int i=0;
	
	cout<<"\nEnter string to be reversed and check is it palindrome or not : \n\n";
	
	cin.getline(str , 50);
	
	stack.convert(str);
	
	while(str[i] != '\0')
	{
		stack.push(str[i]);
		i++;
	}

	stack.palindrome();

	stack.reverse();
	
}


10.postfix
#include <iostream>
using namespace std;
class Stack
{
public:
    char stack_array[50];
    int top;
    Stack()
    {
        top = -1;
    }
    void push(char symbol)
    {
        if (full())
            cout << "\nStack overflow:\n";
        else
        {
            top = top + 1;
            stack_array[top] = symbol;
        }
    }
    char pop()
    {
        if (empty())
            return ('#');
        else
            return (stack_array[top--]);
    }
    int empty()
    {
        if (top == -1)
            return (1);
        else
            return (0);
    }
    int full()
    {
        if (top == 49)
            return (1);
        else
            return (0);
    }

private:
    char infix[50];
    char postfix[50];

public:
    void read()
    {
        cout << "\nEnter an infix expression:";
        cin >> infix;
    }
    int white_space(char symbol)
    {
        if (symbol == ' ' || symbol == '\t' || symbol == '\0')
            return 1;
        else
            return 0;
    }
    void ToPostfix()
    {
        int prev, p;
        char entry;
        p = 0;
        for (int i = 0; infix[i] != '\0'; i++)
        {
            if (!white_space(infix[i]))
            {
                switch (infix[i])
                {
                case '(':
                    push(infix[i]);
                    break;
                case ')':
                    while ((entry = pop()) != '(')
                        postfix[p++] = entry;
                    break;
                case '+':
                case '-':
                case '*':
                case '/':
                    if (!empty())
                    {
                        prev = prior(infix[i]);
                        entry = pop();
                        while (prev <= prior(entry))
                        {
                            postfix[p++] = entry;
                            if (!empty())
                                entry = pop();
                            else
                                break;
                        }
                        if (prev > prior(entry))
                            push(entry);
                    }
                    push(infix[i]);
                    break;
                default:
                    postfix[p++] = infix[i];
                    break;
                }
            }
        }
        while (!empty())
            postfix[p++] = pop();
        postfix[p] = '\0';
        cout << "\nThe postfix expression is: " << postfix << endl;
    }
    int prior(char symbol)
    {
        switch (symbol)
        {
        case '/':
            return (4);
        case '*':
            return (3);
        case '+':
            return (2);
        case '-':
            return (1);
        case '(':
            return (0);
        default:
            return (-1);
        }
    }
};

int main()
{
    char choice = 'y';
    Stack expr;
    while (choice == 'y')
    {
        expr.read();
        expr.ToPostfix();
        cout << "\n\nDo you want to continue ? (y/n): ";
        cin >> choice;
    }
    return 0;
}


11.job
#include<iostream>
using namespace std;
#define size 10

class JobQue
{
	private:
		struct queue
		{
			int que[size];
			int front;
			int rear;
		}Q;
	public:
		JobQue();				//Constructor
		int Qfull();
		int insert(int);
		int Qempty();
		int Delete();
		void display();
};

JobQue::JobQue()					//Initializing the Job Queue
{
	Q.front=-1;
	Q.rear=-1;
}

int JobQue::Qfull()
{
	if(Q.rear>=size-1)
		return 1;
	else
		return 0;
}

int JobQue::insert(int item)
{
	if(Q.front==-1)
		Q.front++;
	Q.que[++Q.rear]=item;
		return Q.rear;
}

int JobQue::Qempty()
{
	if((Q.front==-1)||(Q.front>Q.rear))
		return 1;
		
	else
		return 0;
}

int JobQue::Delete()
{
	int item;
	item=Q.que[Q.front];
	Q.front++;
	
		cout<<"\n The deleted job is:"<<item;
			return Q.front;
}

void JobQue::display()
{
	int i;
	for(i=Q.front;i<=Q.rear;i++)
	cout<<" "<<Q.que[i];
}

int main()
{
	int ch,item;
	char ans;
	JobQue J;
	do
	{
		cout<<"\n Main Menu:";
		cout<<"\n 1.ADD Job\n 2.Delete Job\n 3.Display Job Queue:";
		cout<<"\n Enter your choice:";
		cin>>ch;
		switch(ch)
		{
			case 1:	
				if(J.Qfull())		//Queue Overflow
					cout<<"\n Can not insert the job";
					
				else
				{
					cout<<"\n Enter the Job number:";
					cin>>item;
					J.insert(item);
				}
				break;
						
			case 2:	
				if(J.Qempty())		//Queue Underflow
					cout<<"\n Queue Underflow:";
					
				else 
					J.Delete();
				break;
											
			case 3:	
				if(J.Qempty())
					cout<<"\n Job Queue is Empty:";
					
				else
					J.display();
				break;
					
			default: 
				cout<<"\n Wrong Choice:";
					break;
		}
				
				cout<<"\n Do you want to continue?:";
				cin>>ans;
	}
	while(ans=='Y'||ans=='y');
	return 0;
}



12.deque
#include<iostream>
#include<stdio.h>
#define MAX 10
using namespace std;

struct que
{
    int arr[MAX];
    int front,rear;
};

void init(struct que *q)
{
    q->front=-1;
    q->rear=-1;
}

void print(struct que q)
{
    int i;
    i=q.front;
    while(i!=q.rear)
    {
        cout<<"\t"<<q.arr[i];
        i=(i+1)%MAX;
    }
    cout<<"\t"<<q.arr[q.rear];
}

int isempty(struct que q)
{
    return q.rear==-1?1:0;
}

int isfull(struct que q)
{
    return (q.rear+1)%MAX==q.front?1:0;
}

void addf(struct que *q,int data)
{
    if(isempty(*q))
    {
        q->front=q->rear=0;
        q->arr[q->front]=data;
    }
    else
    {
        q->front=(q->front-1+MAX)%MAX;
        q->arr[q->front]=data;
    }
}

void addr(struct que *q,int data)
{
    if(isempty(*q))
    {
        q->front=q->rear=0;
        q->arr[q->rear]=data;
    }
    else
    {
        q->rear=(q->rear+1)%MAX;
        q->arr[q->rear]=data;
    }
}

int delf(struct que *q)
{
    int data1;
    data1=q->arr[q->front];
    if(q->front==q->rear)
        init(q);
    else
        q->front=(q->front+1)%MAX;
    return data1;
}

int delr(struct que *q)
{
    int data1;
    data1=q->arr[q->rear];
    if(q->front==q->rear)
        init(q);
    else
        q->rear=(q->rear-1+MAX)%MAX;
    return data1;
}

int main()
{
    struct que q;
    int data,ch;
    init(&q);
    while(ch!=6)
    {
        cout<<"\t\n1.Insert front"
                "\t\n2.Insert rear"
                "\t\n3.Delete front"
                "\t\n4.Delete rear"
                "\t\n5.Print"
                "\t\n6.Exit";
         cout<<"\nEnter your choice : ";
        cin>>ch;
        switch(ch)
        {
           case 1:
              cout<<"\nEnter data to insert front : ";
              cin>>data;
              addf(&q,data);
              break;

           case 2:
               cout<<"\nEnter the data to insert rear : ";
               cin>>data;
               addr(&q,data);
               break;

           case 3:
               if(isempty(q))
                   cout<<"\nDequeue is empty!!!";
               else
               {
                   data=delf(&q);
                   cout<<"\nDeleted data is : "<<data;
               }
               break;

           case 4:
               if(isempty(q))
                   cout<<"\nDequeue is empty!!!";
               else
               {
                   data=delr(&q);
                   cout<<"\nDeleted data is : "<<data;
               }
               break;

           case 5:
                if(isempty(q))
                    cout<<"\nDequeue is empty!!!";
                else
                {
                    cout<<"\nDequeue elements are : ";
                    print(q);
                }
                break;
        }
    }
    return 0;
}


13.pizza

#include <iostream>
using namespace std;
#define size 5
class pizza
{
    int porder[size];
    int front,rear;
public:
    pizza()
    {
     front=rear=-1;
    }
    
    int qfull()
    {
     if((front==0)&&(rear==(size-1))||(front==(rear+1)%size))
         return 1;
     else
         return 0;
    }
    
    int qempty()
    {
        if(front==-1)
            return 1;
        else
            return 0;
    }
    void accept_order(int);
    void make_payment(int);
    void order_in_queue();
};


void pizza::accept_order(int item)
{
    if(qfull())
        cout<<"\nVery Sorry !!!! No more orders....\n";
    else
    {
        if(front==-1)		//empty case
        {
            front=rear=0;		//front++ rear++
        }
        else
        {
            rear=(rear+1)%size;
        }
        porder[rear]=item;
    }
}

void pizza::make_payment(int n)
{
    int item;
    char ans;
    if(qempty())
        cout<<"\nSorry !!! There are no pending orders....\n";
    else
    {
      cout<<"\nDeliverd orders as follows...\n";
      for(int i=0;i<n;i++)
      {
          item=porder[front];
          if(front==rear)
          {
               front=rear=-1;		//go to initial state again.
          }
          else
          {
              front=(front+1)%size;
          }
          cout<<"\t"<<item;
      }
      cout<<"\nTotal amount to pay = "<<n*100;
      cout<<"\nThank you visit Again....\n";
    }
}

void pizza::order_in_queue()
{
    int temp;
    if(qempty())
    {
        cout<<"\nSorry !! There is no pending order...\n";
    }
    else
    {
        temp=front;
        cout<<"\nPending Order as follows..\n";
        while(temp!=rear)
        {
            cout<<"\t"<<porder[temp];
            temp=(temp+1)%size;
        }
        cout<<"\t"<<porder[temp];
    }
}


int main()
{
    pizza p1;
    int ch,k,n;
    do
    {
     cout<<"\n\t***** Welcome To Pizza Parlor *******\n";
     cout << "\n1.Accept order\n2.Make_payment\n3.Pending Orders";
     cout<<"\nEnter your choice: ";
     cin>>ch;
     switch(ch)
     {
      case 1:cout<<"\nWhich Pizza do u like most....\n";
             cout<<"\n1.Veg Soya Pizza\n2.Veg butter Pizza\n3.Chicken_Pizza";
             cout<<"\nPlease enter your order: ";
             cin>>k;
             p1.accept_order(k);
             break;
             
      case 2:cout<<"\nHow many Pizza do you want?";
             cin>>n;
             p1.make_payment(n);
             break;
             
             
      case 3:cout<<"\n Following orders are in queue to deliver....as follows..\n";
             p1.order_in_queue();
             break;
     }
    }while(ch!=4);

    return 0;
}
