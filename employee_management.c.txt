#include <stdio.h>

union Asset
{
    char laptop[20];
    char phone[20];
    char vehicle[20];
};

struct Employee
{
    int id;
    char name[20];
    float salary;
    int type;
    union Asset asset;
};

float bonus(float salary)
{
    if (salary >= 30000)
        return salary * 0.10;
    else
        return salary * 0.05;
}

void display(struct Employee *e)
{
    printf("\nID: %d", e->id);
    printf("\nName: %s", e->name);
    printf("\nSalary: %.2f", e->salary);

    if (e->type == 1)
        printf("\nLaptop: %s", e->asset.laptop);
    else if (e->type == 2)
        printf("\nPhone: %s", e->asset.phone);
    else
        printf("\nVehicle: %s", e->asset.vehicle);
}

int main()
{
    struct Employee e;
    int choice, performance;

    printf("Enter ID: ");
    scanf("%d", &e.id);

    printf("Enter Name: ");
    scanf("%s", e.name);

    printf("Enter Salary: ");
    scanf("%f", &e.salary);

    do
    {
        printf("\n\n1.Bonus  2.Asset  3.Display  4.Exit");
        printf("\nEnter choice: ");
        scanf("%d", &choice);

        switch(choice)
        {
            case 1:
                printf("Performance: ");
                scanf("%d", &performance);

                if(performance >= 80)
                    printf("Bonus = %.2f", bonus(e.salary));
                else
                    printf("Bonus = 0");
                break;

            case 2:
                printf("1.Laptop  2.Phone  3.Vehicle: ");
                scanf("%d", &e.type);

                if(e.type == 1)
                    scanf("%s", e.asset.laptop);
                else if(e.type == 2)
                    scanf("%s", e.asset.phone);
                else
                    scanf("%s", e.asset.vehicle);
                break;

            case 3:
                display(&e);
                break;

            case 4:
                printf("Exit");
                break;

            default:
                printf("Invalid choice");
        }

    } while(choice != 4);

    return 0;
}
