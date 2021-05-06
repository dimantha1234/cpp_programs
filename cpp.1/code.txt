#include <iostream>
#include <conio.h>
#include <stdio.h>

using namespace std;

class student
{
private:
    char name[150];
    char sex[5];
    int age;
    char school[100];
    char field[150];
    int year;
public:
    void fninput()
    {
        cout<<"Enter your name:\t";
        cin>>name;
        cout<<"Enter age:\t";
        cin>>age;
        cout<<"Enter sex:\t";
        cin>>sex;
        cout<<"Enter your school:\t";
        cin>>school;
        cout<<"Enter the field you wish to study in our university:\t";
        cin>>field;
        cout<<"Enter the years you plan to follow higher studies(This helps us to give you the most useful study route to follow:\t ";
        cin>>year;

    }
    void fnprocess()
    {
        FILE*pf;
        pf=fopen("student.txt","a");
        fprintf(pf,"\n%s			%d		%s		%s		%s",name,age,school,sex,field);
        fclose(pf);
    }
    void fnprocess1()
    {
        FILE*pf;
        pf=fopen("student.txt","w");
        fprintf(pf,"**Student Details**\nName			Age		School		Sex		Field\n\n%s			%d		%s		%s		%s",name,age,school,sex,field);
        fclose(pf);
    }
    void fnoutput()
    {
        cout<<"Name:\t"<<name<<endl;
        cout<<"Age:\t"<<age<<endl;
        cout<<"Sex:\t"<<sex<<endl;
        cout<<"School:\t"<<school<<endl;
        cout<<"Preferred field:\t"<<field<<endl;
    }
};
int main()
{
    p:
    int a;
    system("COLOR 03");
    cout<<"                         Welcome!\n";
    cout<<" 1)Add details\n 2)See details\n 3)Rewrite\n 4)Exit\n**Input your desire:\t";
    cin>>a;
    system("cls");
    switch(a)
    {
    case 1:
        student obj;
        obj.fninput();
        obj.fnprocess();
        cout<<"Press any key to continue!!";
        getch();
        system("cls");
        obj.fnoutput();
        break;
    case 2:
       char blame[200];
       FILE*filepointer;
       filepointer=fopen("student.txt","r");
       if (filepointer==NULL)
       {
           printf("There is no valid file!");
       }
        else
        {
            while(!feof(filepointer))
            {
                fgets(blame,200,filepointer);
                printf("%s",blame);
            }
        }
        fclose(filepointer);
        cout<<"Press any key to continue!!";
        getch();
        system("cls");
        goto p;
        break;
    case 3:
        student obj1;
        obj1.fninput();
        obj1.fnprocess1();
        cout<<"Press any key to continue!!";
        getch();
        system("cls");
        obj1.fnoutput();
        break;
    case 4:
        cout<<"Have a good day!";
        break;
    default:
        cout<<"Invalid input!!\nPlease enter a valid input!!\n";
        goto p;
    }
    return 0;
}
