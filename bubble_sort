#include <stdio.h>
#include <stdlib.h>
#include <time.h>
typedef struct nude
{
    struct nude *next;
    int value;
} nude;
nude *head1;
nude *head2;
int var;
int delete_var(nude **head, int var, int k);
void show (nude *head);
void push (nude *head, int var);
int swap(nude **head, nude **a, nude **b); //if you call
void b_sort(nude **head);
int delete_duplicats(nude **head1, nude **head2);
int main()
{
    srand(time(NULL));
    head1 = malloc (sizeof(nude));
    head1->value=1;
    head1->next=NULL;
    head2 = malloc (sizeof(nude));
    head2->value=3;
    head2->next=NULL;
    int i=0;


    for (i=0; i<15; i++)
    {
        push(head1,rand()%30);
    }

    printf("ws1(%d) < ws2(%d) = %d",head1,head1->next,head1<head1->next);
    nude *tmp;
    printf("\nlist:\n");
    show(head1);
    b_sort(&head1);
    printf("\nlist after b_sort:\n");
    show(head1);
    delete_var(&head1,4,2);
    printf("\nlist after deleting 4 two times\n");
    show(head1);
    swap(&head1, &head1->next->next->next->next->next, &head1->next->next->next->next);
    printf("\nlist after swap\n");
    show(head1);


    return 0;
}
int delete_var (nude **head, int var, int k)
{
    nude *ws,*previous;
    int flag=0;
    int found=0;
    int j=1;
    ws=*head;
    int imonhead=1;
    if (!k) flag=1;
    else j=k;
    while(ws!=NULL) // going through list
    {

        if(ws->value==var&&imonhead&&j) //checking if struct with certain value has been found and if it's on *head
        {
            *head=ws->next;         //changing *head aka deleting.
            ws=ws->next;            //^
            found++;                //counts how many elements have been deleted
            if (!flag) j--;         //lowers the number of elements to be deleted, if user calls function with 0 as argument, it'll delete untill pointer==NULL
        }
        else if(ws->value==var&&j)  //same as previous, but doesnt include *head changes
        {
            previous->next=ws->next;
            ws=ws->next;
            found++;
            if (!flag) j--;

        }
        else
        {
            previous=ws;        //just goes through list
            ws=ws->next;
            imonhead=0;
        }
    }
    return found; //returns how many elements were deleted, required in delete_duplicate function
}
int delete_duplicats(nude **head1, nude **head2)
{
    nude *ws = *head1;
    while (ws!=NULL)
    {
        if(delete_var(head2,ws->value,0)) delete_var(head1,ws->value,0); //2 lists: list1, list2. takes first element from list1 and tries to delete it in
        ws=ws->next;                                                     //list2. if it happens, function delete deletes (:C) certain element and returns found != 0 so
    }                                                                    //if from 90. line is true hence we can delete that element from list1, otherwise if(false) n shit
}
void push (nude *head, int var)
{
    nude *temp;
    nude *newvalue;
    temp=head;
    while(temp->next!=NULL) temp=temp->next;
    newvalue = malloc (sizeof(nude));
    newvalue->value=var;
    temp->next=newvalue;
    newvalue->next=NULL;


}
void show (nude *head)
{


    while(head!=NULL)
    {
        printf(" %d",head->value);
        head=head->next;

    }
}
int swap(nude **head, nude **a, nude **b)

{
    nude *tmp;
    nude *previous;
    nude *found;
    nude *a1;
    nude *b1;

    a1=*a;
    b1=*b;
    int distance1=0;
    int distance2=0;


    tmp = *head;
    nude *tmp1;
    nude *tmp2;
    tmp1=*head;
    tmp2=*head;
    nude *found1;
    nude *previous1;
    nude *found2;
    nude *previous2;
    if (*head==a1 && *head==b1) return 0;   //if you try to swap 1 element with itself return 0
    else if (*head==a1)                     //if 1 of the elements is 0
    {

        while(tmp!=NULL)
        {
            if (tmp==b1)                    //looks for b1 pointer
            {
                found = tmp;
                break;
            }
            else
            {
                previous=tmp;               //sets pointer behind found element
                tmp=tmp->next;
            }
        }
        if (((*head)->next)==found || (found->next)==(*head))      //if they're next to each other
        {
            tmp=found->next;
            *head=found;
            previous->next=found->next;
            found->next=previous;
        }
        else
        {
            tmp=*head;
            *head=found;
            tmp->next=(*head)->next;
            (*head)->next=previous;
            previous->next=tmp;
        }





    }
    else if (*head==b1)
    {
        while(tmp!=NULL)
        {
            if (tmp==a1)        //looks for a1 pointer and same thing as above
            {
                found = tmp;
                break;
            }
            else
            {
                previous=tmp;
                tmp=tmp->next;
            }
        }

        tmp=*head;
        *head=found;
        tmp->next=(*head)->next;
        (*head)->next=previous;
        previous->next=tmp;
    }
    else
    {

        while(tmp1!=NULL)   //they're not next to each other
        {
            if (tmp1==a1)
            {
                found1 = tmp1;
                break;
            }
            else
            {
                previous1=tmp1;
                tmp1=tmp1->next;
                distance1++;
            }
        }
        while(tmp2!=NULL)
        {
            if (tmp2==b1)
            {
                found2 = tmp2;
                break;
            }
            else
            {
                previous2=tmp2;
                tmp2=tmp2->next;
                distance2++;
            }
        }
        if ((found2->next)==found1 || (found1->next)== found2)
        {
            if (distance1<distance2)
            {
                tmp=found2->next;
                found1->next=tmp;
                previous1->next=found2;
                found2->next=found1;
            }
            else if (distance1>distance2)
            {
                tmp=found1->next;
                found2->next=tmp;
                previous2->next=found1;
                found1->next=found2;
            }

        }
        else
        {
            printf("-.-.-.-.- %d %d -.-.-.-.-",distance1,distance2 );
            if (distance1<distance2)
            {
                tmp=found2->next;
                found2->next=found1->next;
                previous2->next=found1;
                found1->next=tmp;
                previous1->next=found2;
            }
            else if(distance1>distance2)
            {
                tmp=found1->next;
                found1->next=found2->next;
                previous1->next=found2;
                found2->next=tmp;
                previous2->next=found1;
            }

        }

    }




}
void b_sort(nude **head)
{
    nude *tmp;

    int flaga=1;
    while(flaga)
    {

        flaga=0;
        tmp=head1;
        while(tmp->next!=NULL)
        {

            if((tmp->value)>(tmp->next->value))
            {
                swap(&head1,&tmp,&tmp->next);
                flaga=1;
                continue;
            }

            if (tmp->next==NULL) return 0;
            tmp=tmp->next;


        }

    }
}
void check (nude *a, nude *b)
{

}
