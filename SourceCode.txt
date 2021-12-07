#include <stdio.h>
#include <stdlib.h>
#include <windows.h>
#include <stdbool.h>
#include <string.h>
#include <mmsystem.h>
/// this three are connected to the crypted password.
#define ENTER 13
#define TAB 9
#define BKSPC 8
int i;
int NumOfOrders;
char OrderType[20][50];
bool TrueFalse = false;
int wallet,change;
int OrderPrice[5];
int OrderQuantity[5];
int sumofAll=0;
///DRINKS PRICE
int water=7,cocacola=12,pepsi=12,mountainD=15,sprite=10,milk=15,coffee=14;
///BREAKFAST & LUNCH PRICE
int scramEgg=12,friedR=10,hotD=8,ham=12,tocino=15,friedC=25,chickenC=25,porkM=20,beefS=20,caldereta=20;
///SNACKS PRICE
int kikiam=10,fishball=10,bananaq=5,camoteq=5,hotC=5,hamB=30,cheeseB=35;
bool menu= false;

///mao ni ang struct statement nag define ni siya og new data.
struct user{
    char fullName[50];
    char username[50];
    char password[50];
    char email[50];
    char phone[50];
};
///void must in the top of the int main
void takeinput(char ch[50]){
    fgets(ch,50,stdin);
    ch[strlen(ch)-1]=0;


}
/*i generate the username to separate the username and email
     for example: jeddesape@gmail.com, so the username will be jeddesape only */

char generateUsername(char email[50], char username[50]){
    for (int i=0; i < strlen(email);i++){
        if(email[i]=='@'){
                break;
        }

    }

};
//this statement shows to encrypt the password of the user.
void takepassword(char password [50]){
    int i;
    char ch;
    while (1){

        ch = getch();
        if (ch == ENTER || ch == TAB){
            password[i]='\0';
            break;
        }
        else if(ch == BKSPC){
                if(i>0){

                    i--;
                    printf("\b \b");

                }


        }
        else {
            password [i++]=ch;
            printf("* \b");
        }
    }

}
int main()
{
    //to have a database on our system we create a FILE..
    FILE *fp;
    //usr found is you variable name which is define ,if the user is already registered or not. remember 0 is TRUE and 1 is FALSE .
    int choice,usrFound=0;
    struct user user;
    char password2[50];

    HANDLE hConsole;hConsole=GetStdHandle
    (STD_OUTPUT_HANDLE);
    SetConsoleTextAttribute(hConsole,3);
    three:
    top:
    system("cls");
    printf("|----------------\\\____________________________________________________________________________________________________");
    printf("\n|Foodweb.evsu.ph  \\\ New Tab (+)\\\                                                                                      |");
    printf("\n|------------------\\\------------\\\_____________________________________________________________________________________|");
    printf("\n                                                                                                              ");
    printf("\n                                                                                                              ");
    printf("\n                                                                                                              ");
    printf("\n                                                                                                              ");
    printf("\n                                                                                                              ");
    SetConsoleTextAttribute(hConsole,11);
    printf("\n                                                 1. SIGN UP                                                   ");
    printf("\n                                                 2. LOGIN                                                     ");
    printf("\n                                                 3. EXIT                                                      ");
    SetConsoleTextAttribute(hConsole,3);
    printf("\n                                                                                                              ");
    printf("\n                                                                                                              ");
    printf("\n                                                                                                              ");
    printf("\n                                                                                                              ");
    printf("\n                                                                                                              ");
    printf("\n                                                                                                              ");

    SetConsoleTextAttribute(hConsole,6);
    printf("\nTYPE:");
    SetConsoleTextAttribute(hConsole,13);
    scanf("%d",&choice);
    fgetc(stdin);
    system("cls");

    switch (choice){
    case 1:
    signup:
    system("cls");
    SetConsoleTextAttribute(hConsole,3);
    printf("|------------------------------\\\______________________________________________________________________________________");
    printf("\n|Foodweb.evsu.ph/Signup         \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    printf("\n\n\n                                                                                                           \n\n");
    SetConsoleTextAttribute(hConsole,6);
    printf("\n                                         |||| || |||||| ||  || ||  || ||||||");
    printf("\n                                         ||   || ||     ||| || ||  || ||  ||");
    printf("\n                                           || || ||  || || ||| |||||| ||||||");
    printf("\n                                         |||| || |||||| ||  || |||||| || \n\n");
    SetConsoleTextAttribute(hConsole,3);
    printf("\n\t\t\t\tFullname:");
    takeinput(user.fullName);
    printf("\n\t\t\t\tUsername:");
    takeinput(user.username);
    printf("\n\t\t\t\tEmail:");
    takeinput(user.email);
    printf("\n\t\t\t\tPhone Number:");
    takeinput(user.phone);
    printf("\n\t\t\t\tPassword:");
    takepassword(user.password);
    printf("\n\n\t\t\t\tConfirm Password:");
    takepassword(password2);
    system("cls");

    if(!strcmp(user.password,password2)){
        generateUsername(user.email,user.username);
        //fopen is a fuction to create a new file or to open an existing file. This call will initialize an object of the type FILE.
        fp = fopen("Database.txt","a+");
        fwrite(&user,sizeof(struct user),1,fp);
        if(fwrite !=0){
                char yN[50];
            printf("|------------------------------\\\______________________________________________________________________________________");
            printf("\n|Foodweb.evsu.ph/Verified!      \\\ New Tab (+)\\\                                                                        |");
            printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
            printf("\n\n\t\t\t\t\tUser Registration Success!\n\n\n",user.username);
            printf("\n\n\n\t\t\t\t\tDo you want to continue?");
            SetConsoleTextAttribute(hConsole,10);
            printf("\n\t\t\t\t             _____   _____           ");
            printf("\n\t\t\t\t            | Yes | |  No |            ");
            printf("\n\t\t\t\t            |=====| |=====|            \n\n\n\n");
            scanf("%s",&yN);

            if((strcmp(yN,"Yes")==0) || (strcmp(yN,"yes")==0)){
                    while ( !menu ){
    system("cls");
    SetConsoleTextAttribute(hConsole,6);
    printf("|------------------------------\\\______________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen      \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    printf("|___________|======|____________________________________|====|___________________________________|======|_____________|\n");
    printf("|-----------|DRINKS|------------------------------------|MEAL|-----------------------------------|SNACKS|-------------|\n");
    printf("|-----------|======|------------------------------------|====|-----------------------------------|======|-------------|\n");
    printf("|_____________________________________________________________________________________________________________________|\n");
    printf("|__||______________________||__||_______BREAKFAST_______||__||_________LUNCH__________||__________________________||__|\n");
    printf("|--||Water.........Php 7.00||--||Scrambled Egg..Php12.00||--||Fried Chicken...Php25.00||--||Kikiam........Php10.00||--|\n");
    printf("|--||Coca-cola.....Php12.00||--||Fried Rice.....Php10.00||--||Chicken Curry...Php25.00||--||Fishball......Php10.00||--|\n");
    printf("|--||Pepsi.........Php12.00||--||Hotdog.........Php 8.00||--||Pork Menudo.....Php20.00||--||Bananaque.....Php 5.00||--|\n");
    printf("|--||Mountain Dew..Php15.00||--||Ham............Php12.00||--||Beef Steak......Php20.00||--||Camoteque.....Php 5.00||--|\n");
    printf("|--||Sprite........Php10.00||--||Tocino.........Php15.00||--||Caldereta.......Php20.00||--||Hotcake.......Php 5.00||--|\n");
    printf("|--||Milk..........Php15.00||--||                       ||--||                        ||--||Hamburger.....Php30.00||--|\n");
    printf("|--||Coffee........Php14.00||--||                       ||--||                        ||--||Cheeseburger..Php35.00||--|\n");
    printf("|--||**********************||--||***********************||--||************************||--||**********************||--|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("\n\n\n\t\t\t\t\t\tEnter your Wallet:");
    SetConsoleTextAttribute(hConsole,13);
    scanf("%d",&wallet);
    system("cls");
    SetConsoleTextAttribute(hConsole,6);
    printf("|------------------------------\\\_______________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen      \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    printf("|___________|======|____________________________________|====|___________________________________|======|_____________|\n");
    printf("|-----------|DRINKS|------------------------------------|MEAL|-----------------------------------|SNACKS|-------------|\n");
    printf("|-----------|======|------------------------------------|====|-----------------------------------|======|-------------|\n");
    printf("|_____________________________________________________________________________________________________________________|\n");
    printf("|__||______________________||__||_______BREAKFAST_______||__||_________LUNCH__________||__________________________||__|\n");
    printf("|--||Water.........Php 7.00||--||Scrambled Egg..Php12.00||--||Fried Chicken...Php25.00||--||Kikiam........Php10.00||--|\n");
    printf("|--||Coca-cola.....Php12.00||--||Fried Rice.....Php10.00||--||Chicken Curry...Php25.00||--||Fishball......Php10.00||--|\n");
    printf("|--||Pepsi.........Php12.00||--||Hotdog.........Php 8.00||--||Pork Menudo.....Php20.00||--||Bananaque.....Php 5.00||--|\n");
    printf("|--||Mountain Dew..Php15.00||--||Ham............Php12.00||--||Beef Steak......Php20.00||--||Camoteque.....Php 5.00||--|\n");
    printf("|--||Sprite........Php10.00||--||Tocino.........Php15.00||--||Caldereta.......Php20.00||--||Hotcake.......Php 5.00||--|\n");
    printf("|--||Milk..........Php15.00||--||                       ||--||                        ||--||Hamburger.....Php30.00||--|\n");
    printf("|--||Coffee........Php14.00||--||                       ||--||                        ||--||Cheeseburger..Php35.00||--|\n");
    printf("|--||**********************||--||***********************||--||************************||--||**********************||--|\n");
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------||Your Wallet:Php%d.00 ||---------------------------------------------|\n",wallet);
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    fflush(stdin);
    printf("Number of order:");
    SetConsoleTextAttribute(hConsole,13);
    scanf("%d", &NumOfOrders);

    if (NumOfOrders > 0){ menu=true; }
    else { printf("please enter a positive number\n");
    }

    }
    reselect:
    system("cls");
    SetConsoleTextAttribute(hConsole,6);
    printf("|------------------------------\\\______________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen      \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    printf("|___________|======|____________________________________|====|___________________________________|======|_____________|\n");
    printf("|-----------|DRINKS|------------------------------------|MEAL|-----------------------------------|SNACKS|-------------|\n");
    printf("|-----------|======|------------------------------------|====|-----------------------------------|======|-------------|\n");
    printf("|_____________________________________________________________________________________________________________________|\n");
    printf("|__||______________________||__||_______BREAKFAST_______||__||_________LUNCH__________||__________________________||__|\n");
    printf("|--||Water.........Php 7.00||--||Scrambled Egg..Php12.00||--||Fried Chicken...Php25.00||--||Kikiam........Php10.00||--|\n");
    printf("|--||Coca-cola.....Php12.00||--||Fried Rice.....Php10.00||--||Chicken Curry...Php25.00||--||Fishball......Php10.00||--|\n");
    printf("|--||Pepsi.........Php12.00||--||Hotdog.........Php 8.00||--||Pork Menudo.....Php20.00||--||Bananaque.....Php 5.00||--|\n");
    printf("|--||Mountain Dew..Php15.00||--||Ham............Php12.00||--||Beef Steak......Php20.00||--||Camoteque.....Php 5.00||--|\n");
    printf("|--||Sprite........Php10.00||--||Tocino.........Php15.00||--||Caldereta.......Php20.00||--||Hotcake.......Php 5.00||--|\n");
    printf("|--||Milk..........Php15.00||--||                       ||--||                        ||--||Hamburger.....Php30.00||--|\n");
    printf("|--||Coffee........Php14.00||--||                       ||--||                        ||--||Cheeseburger..Php35.00||--|\n");
    printf("|--||**********************||--||***********************||--||************************||--||**********************||--|\n");
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------||Your Wallet:Php%d.00 ||---------------------------------------------|\n",wallet);
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    SetConsoleTextAttribute(hConsole,6);

    printf("Type Your orders:\n");

    for(i=0; i<NumOfOrders; i++)
    {
    SetConsoleTextAttribute(hConsole,6);
    printf("Order:");


    scanf("%s", OrderType[i]);

    }

    for(i=0; i<NumOfOrders; i++)
    {
    TrueFalse = false;
    while ( !TrueFalse ){
    //-------------------------V------DRINKS SECTION---------V---------------------------//
    if((strcmp(OrderType[i], "Water")==0)||(strcmp(OrderType[i],"water")==0)){
        OrderPrice[i] = water; TrueFalse = true;
    }
    else if((strcmp(OrderType[i], "Coca-cola")==0)||(strcmp(OrderType[i],"coca-cola")==0)){
        OrderPrice[i] = cocacola; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "Pepsi")==0)||(strcmp(OrderType[i],"pepsi")==0)){
        OrderPrice[i] = pepsi; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "MountainDew")==0)||(strcmp(OrderType[i],"mountaindew")==0)){
        OrderPrice[i] = mountainD; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "Sprite")==0)||(strcmp(OrderType[i],"sprite")==0)){
        OrderPrice[i] = sprite; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "Milk")==0)||(strcmp(OrderType[i],"milk")==0)){
        OrderPrice[i] = milk; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "Coffee")==0)||(strcmp(OrderType[i],"coffee")==0)){
        OrderPrice[i] = coffee; TrueFalse =true;
    }
    //-----------------------V-------BREAKFAST & LUNCH SECTION------V---------------------------//
    else if((strcmp(OrderType[i], "ScrambledEgg")==0)||(strcmp(OrderType[i],"scrambledegg")==0)){
        OrderPrice[i] = scramEgg; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "FriedRice")==0)||(strcmp(OrderType[i],"friedrice")==0)){
        OrderPrice[i] = friedR; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Hotdog")==0)||(strcmp(OrderType[i],"hotdog")==0)){
        OrderPrice[i] = hotD; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Ham")==0)||(strcmp(OrderType[i],"ham")==0)){
        OrderPrice[i] = ham; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Tocino")==0)||(strcmp(OrderType[i],"tocino")==0)){
        OrderPrice[i] = tocino; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "FriedChicken")==0)||(strcmp(OrderType[i],"friedchicken")==0)){
        OrderPrice[i] = friedC; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "ChickenCurry")==0)||(strcmp(OrderType[i],"chickencurry")==0)){
        OrderPrice[i] = chickenC; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "PorkMenudo")==0)||(strcmp(OrderType[i],"porkmenudo")==0)){
        OrderPrice[i] = porkM; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "BeefSteak")==0)||(strcmp(OrderType[i],"beefsteak")==0)){
        OrderPrice[i] = beefS; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Caldereta")==0)||(strcmp(OrderType[i],"caldereta")==0)){
        OrderPrice[i] = caldereta; TrueFalse =true;
    }
    //---------------------V------------SNACKS SECTION----------V-----------------------//
     else if((strcmp(OrderType[i], "Kikiam")==0)||(strcmp(OrderType[i],"kikiam")==0)){
        OrderPrice[i] = kikiam; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Fishball")==0)||(strcmp(OrderType[i],"fishball")==0)){
        OrderPrice[i] = fishball; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Bananaque")==0)||(strcmp(OrderType[i],"bananaque")==0)){
        OrderPrice[i] = bananaq; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Camoteque")==0)||(strcmp(OrderType[i],"camoteque")==0)){
        OrderPrice[i] = camoteq; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Hotcake")==0)||(strcmp(OrderType[i],"hotcake")==0)){
        OrderPrice[i] = hotC; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Hamburger")==0)||(strcmp(OrderType[i],"hamburger")==0)){
        OrderPrice[i] = hamB; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Cheeseburger")==0)||(strcmp(OrderType[i],"cheeseburger")==0)){
        OrderPrice[i] = cheeseB; TrueFalse =true;
    }

    //------------------------Not Available section----V------------------------------
    else{
    system("cls");
    printf("Type the given correct order, please reselect\n");
    printf("Type any key to continue");
    getch();
    goto reselect;
     return 0;
     }
    //--------------------------------------------------------------------------------
    }
    }
    system("cls");

    SetConsoleTextAttribute(hConsole,6);

    printf("|------------------------------\\\______________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen      \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    printf("|___________|======|____________________________________|====|___________________________________|======|_____________|\n");
    printf("|-----------|DRINKS|------------------------------------|MEAL|-----------------------------------|SNACKS|-------------|\n");
    printf("|-----------|======|------------------------------------|====|-----------------------------------|======|-------------|\n");
    printf("|_____________________________________________________________________________________________________________________|\n");
    printf("|__||______________________||__||_______BREAKFAST_______||__||_________LUNCH__________||__________________________||__|\n");
    printf("|--||Water.........Php 7.00||--||Scrambled Egg..Php12.00||--||Fried Chicken...Php25.00||--||Kikiam........Php10.00||--|\n");
    printf("|--||Coca-cola.....Php12.00||--||Fried Rice.....Php10.00||--||Chicken Curry...Php25.00||--||Fishball......Php10.00||--|\n");
    printf("|--||Pepsi.........Php12.00||--||Hotdog.........Php 8.00||--||Pork Menudo.....Php20.00||--||Bananaque.....Php 5.00||--|\n");
    printf("|--||Mountain Dew..Php15.00||--||Ham............Php12.00||--||Beef Steak......Php20.00||--||Camoteque.....Php 5.00||--|\n");
    printf("|--||Sprite........Php10.00||--||Tocino.........Php15.00||--||Caldereta.......Php20.00||--||Hotcake.......Php 5.00||--|\n");
    printf("|--||Milk..........Php15.00||--||                       ||--||                        ||--||Hamburger.....Php30.00||--|\n");
    printf("|--||Coffee........Php14.00||--||                       ||--||                        ||--||Cheeseburger..Php35.00||--|\n");
    printf("|--||**********************||--||***********************||--||************************||--||**********************||--|\n");
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------||Your Wallet:Php%d.00 ||---------------------------------------------|\n",wallet-OrderPrice[i]);
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("Quantity:\n");

    for(i=0; i<NumOfOrders; i++)
    {
    SetConsoleTextAttribute(hConsole,13);
    printf("%s: ", OrderType[i]);

    scanf("%d", &OrderQuantity[i]);
    }

    system("cls");
    SetConsoleTextAttribute(hConsole,6);

    printf("|----------------------------------\\\__________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen/receipt  \\\ New Tab (+)\\\                                                                    |");
    printf("\n|------------------------------------\\\____________\\\___________________________________________________________________|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    SetConsoleTextAttribute(hConsole,8);
    printf("|   ************     ************     **********       ************   ************   ************      ************   |\n");
    printf("|   *************    ************    *************     ************   ************   *************     ************   |\n");
    printf("|   ***        ***   ************   ***        ****    ************   ************   ***        ***    ************   |\n");
    printf("|   ***        ***   ***            ***         ****   ***                ****       ***         ***       ****       |\n");
    printf("|   ***        ***   ***            ***         ****   ***                ****       ***         ***       ****       |\n");
    printf("|   ***       ***    ************   ***                ************       ****       ***        ***        ****       |\n");
    printf("|   ***********      ************   ***                ************       ****       *************         ****       |\n");
    printf("|   ***********      ***            ***                ***                ****       ***********           ****       |\n");
    printf("|   ***      ***     ***            ***         ****   ***                ****       ***                   ****       |\n");
    printf("|   ***        ***   ************   ***        ****    ************   ************   ***                   ****       |\n");
    printf("|   ***         ***  ************   **************     ************   ************   ***                   ****       |\n");
    printf("|   ***          *** ************   *************      ************   ************   ***                   ****       |\n");
    SetConsoleTextAttribute(hConsole,6);
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");

        SetConsoleTextAttribute(hConsole,9);
    for(i=0; i<NumOfOrders; i++)
    {
    printf("\t\t\t\t%s", OrderType[i]);
    printf("\t\tx%d",OrderQuantity[i]);
    printf("\t\tPhp%d.00\n",OrderPrice[i]*OrderQuantity[i]);
    }

    for(i=0; i<NumOfOrders; i++)
    {
        sumofAll += OrderPrice[i]*OrderQuantity[i];
        change=wallet-sumofAll;
    }
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("\t\t\t\tWallet:\t\t\t\tPhp%d.00\n", wallet);
    printf("\t\t\t\tTotal:\t\t\t\tPhp%d.00\n",sumofAll);
    printf("\t\t\t\tChange:\t\t\t\tPhp%d.00\n",change);
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    SetConsoleTextAttribute(hConsole,14);

    printf("\t\t\t\t\t***THANKYOU FOR ORDERING***\n");
    printf("\t\t\t\t***Please wait for your order to arrive***\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    PlaySound(TEXT("wav\\ty.wav"),NULL,SND_SYNC);
    SetConsoleTextAttribute(hConsole,10);

    printf("|\t\t\t\t\t\t LOG OUT");
    printf("|\n\t\t\t\t\tPress any key to Log Out:");
    getch();
    goto top;

    return 0;




            }
            if((strcmp(yN,"No")==0) || (strcmp(yN,"no")==0)){
            system("cls");
            printf("|------------------------------\\\______________________________________________________________________________________");
            printf("\n|FoodWeb.evsu.ph/Exit           \\\ New Tab (+)\\\                                                                        |");
            printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
            printf("\n                                                                                                                       \n\n");
            printf("\n                                                                                                                       \n\n");
            SetConsoleTextAttribute(hConsole,4);
            printf("\n                                               PLEASE COME BACK AGAIN :)                                         \n\n\n\n\n");
            goto three;
            }



        }
        else printf("\n\nSorry! Something went wrong :(");
        //fclose is a function return 0 on success or if there is an error in closing the file.
        fclose(fp);

    }
    else {
        printf("|-------------------------------------\\\______________________________________________________________________________");
        printf("\n|FoodWeb.evsu.ph/Password donot matched\\\ New Tab (+)\\\                                                                |");
        printf("\n|---------------------------------------\\\____________\\\_______________________________________________________________|\n");
        printf("\n\n\t\t\t\t\tPassword donot matched!!!\n\n\n\n\n");
        Beep(800,300);
        printf("\t\t\t\t\tPlease type any key to continue");
        getch();
        goto signup;
    }
    break;
    case 2:{

        char username[50],pword[50];
        struct user login;
    SetConsoleTextAttribute(hConsole,3);
    nr:
    logAgain:
    system("cls");
    printf("|------------------------------\\\______________________________________________________________________________________");
    printf("\n|Foodmania.evsu.ph/Login        \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    SetConsoleTextAttribute(hConsole,6);
    printf("\n\n\n                                                           \n\n");
    printf("\n                                           ||     |||||| |||||| || ||  ||                         ");
    printf("\n                                           ||     ||  || ||     || ||| ||                         ");
    printf("\n                                           ||  || ||  || ||  || || || |||                 ");
    printf("\n                                           |||||| |||||| |||||| || ||  ||                 \n\n");
    SetConsoleTextAttribute(hConsole,3);
    printf("\n\t\t\t\t\tUsername:");
    takeinput(username);
    printf("\n\t\t\t\t\tPassword:");
    takepassword(pword);

    fp = fopen("Database.txt","r");
    while(fread(&login,sizeof(struct user),1,fp)){
        if(!strcmp(login.username,username)){
            if(!strcmp(login.password,pword)){
                char yN;
                system("cls");
                printf("|------------------------------\\\______________________________________________________________________________________");
                printf("\n|FoodWeb.evsu.ph/E-Canteen      \\\ New Tab (+)\\\                                                                        |");
                printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
                printf("\n                                                                                                                   \n\n");
                printf("\n\t\t\t\t\t\tWelcome %s",login.fullName);
                printf("\n\n\n\n\t\t\t\t\tFullName: %s",login.fullName);
                printf("\n\t\t\t\t\tUsername: %s",login.username);
                printf("\n\t\t\t\t\tEmail: %s",login.email);
                printf("\n\t\t\t\t\tContact no.: %s\n\n\n\n\n",login.phone);
                printf("\n\n\n\t\t\t\t\tType any key to continue:");
                getch();
                system("cls");

                while ( !menu ){
    system("cls");
    SetConsoleTextAttribute(hConsole,6);
    printf("|------------------------------\\\______________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen      \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    printf("|___________|======|____________________________________|====|___________________________________|======|_____________|\n");
    printf("|-----------|DRINKS|------------------------------------|MEAL|-----------------------------------|SNACKS|-------------|\n");
    printf("|-----------|======|------------------------------------|====|-----------------------------------|======|-------------|\n");
    printf("|_____________________________________________________________________________________________________________________|\n");
    printf("|__||______________________||__||_______BREAKFAST_______||__||_________LUNCH__________||__________________________||__|\n");
    printf("|--||Water.........Php 7.00||--||Scrambled Egg..Php12.00||--||Fried Chicken...Php25.00||--||Kikiam........Php10.00||--|\n");
    printf("|--||Coca-cola.....Php12.00||--||Fried Rice.....Php10.00||--||Chicken Curry...Php25.00||--||Fishball......Php10.00||--|\n");
    printf("|--||Pepsi.........Php12.00||--||Hotdog.........Php 8.00||--||Pork Menudo.....Php20.00||--||Bananaque.....Php 5.00||--|\n");
    printf("|--||Mountain Dew..Php15.00||--||Ham............Php12.00||--||Beef Steak......Php20.00||--||Camoteque.....Php 5.00||--|\n");
    printf("|--||Sprite........Php10.00||--||Tocino.........Php15.00||--||Caldereta.......Php20.00||--||Hotcake.......Php 5.00||--|\n");
    printf("|--||Milk..........Php15.00||--||                       ||--||                        ||--||Hamburger.....Php30.00||--|\n");
    printf("|--||Coffee........Php14.00||--||                       ||--||                        ||--||Cheeseburger..Php35.00||--|\n");
    printf("|--||**********************||--||***********************||--||************************||--||**********************||--|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("\n\n\n\t\t\t\t\t\tEnter your Wallet:");
    SetConsoleTextAttribute(hConsole,13);
    scanf("%d",&wallet);
    system("cls");
    SetConsoleTextAttribute(hConsole,6);
    printf("|------------------------------\\\______________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen      \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    printf("|___________|======|____________________________________|====|___________________________________|======|_____________|\n");
    printf("|-----------|DRINKS|------------------------------------|MEAL|-----------------------------------|SNACKS|-------------|\n");
    printf("|-----------|======|------------------------------------|====|-----------------------------------|======|-------------|\n");
    printf("|_____________________________________________________________________________________________________________________|\n");
    printf("|__||______________________||__||_______BREAKFAST_______||__||_________LUNCH__________||__________________________||__|\n");
    printf("|--||Water.........Php 7.00||--||Scrambled Egg..Php12.00||--||Fried Chicken...Php25.00||--||Kikiam........Php10.00||--|\n");
    printf("|--||Coca-cola.....Php12.00||--||Fried Rice.....Php10.00||--||Chicken Curry...Php25.00||--||Fishball......Php10.00||--|\n");
    printf("|--||Pepsi.........Php12.00||--||Hotdog.........Php 8.00||--||Pork Menudo.....Php20.00||--||Bananaque.....Php 5.00||--|\n");
    printf("|--||Mountain Dew..Php15.00||--||Ham............Php12.00||--||Beef Steak......Php20.00||--||Camoteque.....Php 5.00||--|\n");
    printf("|--||Sprite........Php10.00||--||Tocino.........Php15.00||--||Caldereta.......Php20.00||--||Hotcake.......Php 5.00||--|\n");
    printf("|--||Milk..........Php15.00||--||                       ||--||                        ||--||Hamburger.....Php30.00||--|\n");
    printf("|--||Coffee........Php14.00||--||                       ||--||                        ||--||Cheeseburger..Php35.00||--|\n");
    printf("|--||**********************||--||***********************||--||************************||--||**********************||--|\n");
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------||Your Wallet:Php%d.00 ||---------------------------------------------|\n",wallet);
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    fflush(stdin);
    printf("|Number of order:");
    SetConsoleTextAttribute(hConsole,13);
    scanf("%d", &NumOfOrders);

    if (NumOfOrders > 0){ menu=true; }
    else { printf("please enter a positive number\n");
    }

    }
    Logreselect:
    system("cls");

    SetConsoleTextAttribute(hConsole,6);
    printf("|------------------------------\\\______________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen      \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    printf("|___________|======|____________________________________|====|___________________________________|======|_____________|\n");
    printf("|-----------|DRINKS|------------------------------------|MEAL|-----------------------------------|SNACKS|-------------|\n");
    printf("|-----------|======|------------------------------------|====|-----------------------------------|======|-------------|\n");
    printf("|_____________________________________________________________________________________________________________________|\n");
    printf("|__||______________________||__||_______BREAKFAST_______||__||_________LUNCH__________||__________________________||__|\n");
    printf("|--||Water.........Php 7.00||--||Scrambled Egg..Php12.00||--||Fried Chicken...Php25.00||--||Kikiam........Php10.00||--|\n");
    printf("|--||Coca-cola.....Php12.00||--||Fried Rice.....Php10.00||--||Chicken Curry...Php25.00||--||Fishball......Php10.00||--|\n");
    printf("|--||Pepsi.........Php12.00||--||Hotdog.........Php 8.00||--||Pork Menudo.....Php20.00||--||Bananaque.....Php 5.00||--|\n");
    printf("|--||Mountain Dew..Php15.00||--||Ham............Php12.00||--||Beef Steak......Php20.00||--||Camoteque.....Php 5.00||--|\n");
    printf("|--||Sprite........Php10.00||--||Tocino.........Php15.00||--||Caldereta.......Php20.00||--||Hotcake.......Php 5.00||--|\n");
    printf("|--||Milk..........Php15.00||--||                       ||--||                        ||--||Hamburger.....Php30.00||--|\n");
    printf("|--||Coffee........Php14.00||--||                       ||--||                        ||--||Cheeseburger..Php35.00||--|\n");
    printf("|--||**********************||--||***********************||--||************************||--||**********************||--|\n");
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------||Your Wallet:Php%d.00 ||---------------------------------------------|\n",wallet);
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    SetConsoleTextAttribute(hConsole,6);

    printf("Type Your orders:\n");

    for(i=0; i<NumOfOrders; i++)
    {
    SetConsoleTextAttribute(hConsole,6);
    printf("Order:");


    scanf("%s", OrderType[i]);

    }

    for(i=0; i<NumOfOrders; i++)
    {
    TrueFalse = false;
    while ( !TrueFalse ){
    //-------------------------V------DRINKS SECTION---------V---------------------------//
    if((strcmp(OrderType[i], "Water")==0)||(strcmp(OrderType[i],"water")==0)){
        OrderPrice[i] = water; TrueFalse = true;
    }
    else if((strcmp(OrderType[i], "Coca-cola")==0)||(strcmp(OrderType[i],"coca-cola")==0)){
        OrderPrice[i] = cocacola; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "Pepsi")==0)||(strcmp(OrderType[i],"pepsi")==0)){
        OrderPrice[i] = pepsi; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "MountainDew")==0)||(strcmp(OrderType[i],"mountaindew")==0)){
        OrderPrice[i] = mountainD; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "Sprite")==0)||(strcmp(OrderType[i],"sprite")==0)){
        OrderPrice[i] = sprite; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "Milk")==0)||(strcmp(OrderType[i],"milk")==0)){
        OrderPrice[i] = milk; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "Coffee")==0)||(strcmp(OrderType[i],"coffee")==0)){
        OrderPrice[i] = coffee; TrueFalse =true;
    }
    //-----------------------V-------BREAKFAST & LUNCH SECTION------V---------------------------//
    else if((strcmp(OrderType[i], "ScrambledEgg")==0)||(strcmp(OrderType[i],"scrambledegg")==0)){
        OrderPrice[i] = scramEgg; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "FriedRice")==0)||(strcmp(OrderType[i],"friedrice")==0)){
        OrderPrice[i] = friedR; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Hotdog")==0)||(strcmp(OrderType[i],"hotdog")==0)){
        OrderPrice[i] = hotD; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Ham")==0)||(strcmp(OrderType[i],"ham")==0)){
        OrderPrice[i] = ham; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Tocino")==0)||(strcmp(OrderType[i],"tocino")==0)){
        OrderPrice[i] = tocino; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "FriedChicken")==0)||(strcmp(OrderType[i],"friedchicken")==0)){
        OrderPrice[i] = friedC; TrueFalse =true;
    }
    else if((strcmp(OrderType[i], "ChickenCurry")==0)||(strcmp(OrderType[i],"chickencurry")==0)){
        OrderPrice[i] = chickenC; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "PorkMenudo")==0)||(strcmp(OrderType[i],"porkmenudo")==0)){
        OrderPrice[i] = porkM; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "BeefSteak")==0)||(strcmp(OrderType[i],"beefsteak")==0)){
        OrderPrice[i] = beefS; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Caldereta")==0)||(strcmp(OrderType[i],"caldereta")==0)){
        OrderPrice[i] = caldereta; TrueFalse =true;
    }
    //---------------------V------------SNACKS SECTION----------V-----------------------//
     else if((strcmp(OrderType[i], "Kikiam")==0)||(strcmp(OrderType[i],"kikiam")==0)){
        OrderPrice[i] = kikiam; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Fishball")==0)||(strcmp(OrderType[i],"fishball")==0)){
        OrderPrice[i] = fishball; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Bananaque")==0)||(strcmp(OrderType[i],"bananaque")==0)){
        OrderPrice[i] = bananaq; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Camoteque")==0)||(strcmp(OrderType[i],"camoteque")==0)){
        OrderPrice[i] = camoteq; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Hotcake")==0)||(strcmp(OrderType[i],"hotcake")==0)){
        OrderPrice[i] = hotC; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Hamburger")==0)||(strcmp(OrderType[i],"hamburger")==0)){
        OrderPrice[i] = hamB; TrueFalse =true;
    }
     else if((strcmp(OrderType[i], "Cheeseburger")==0)||(strcmp(OrderType[i],"cheeseburger")==0)){
        OrderPrice[i] = cheeseB; TrueFalse =true;
    }

    //------------------------Not Available section----V------------------------------
    else{
    system("cls");
    printf("Type the given correct order, please reselect\n");
    printf("Type any key to continue");
    getch();
    goto Logreselect;
     return 0;
     }
    //--------------------------------------------------------------------------------
    }
    }
    system("cls");

    SetConsoleTextAttribute(hConsole,6);

    printf("|------------------------------\\\______________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen      \\\ New Tab (+)\\\                                                                        |");
    printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
    printf("|___________|======|____________________________________|====|___________________________________|======|_____________|\n");
    printf("|-----------|DRINKS|------------------------------------|MEAL|-----------------------------------|SNACKS|-------------|\n");
    printf("|-----------|======|------------------------------------|====|-----------------------------------|======|-------------|\n");
    printf("|_____________________________________________________________________________________________________________________|\n");
    printf("|__||______________________||__||_______BREAKFAST_______||__||_________LUNCH__________||__________________________||__|\n");
    printf("|--||Water.........Php 7.00||--||Scrambled Egg..Php12.00||--||Fried Chicken...Php25.00||--||Kikiam........Php10.00||--|\n");
    printf("|--||Coca-cola.....Php12.00||--||Fried Rice.....Php10.00||--||Chicken Curry...Php25.00||--||Fishball......Php10.00||--|\n");
    printf("|--||Pepsi.........Php12.00||--||Hotdog.........Php 8.00||--||Pork Menudo.....Php20.00||--||Bananaque.....Php 5.00||--|\n");
    printf("|--||Mountain Dew..Php15.00||--||Ham............Php12.00||--||Beef Steak......Php20.00||--||Camoteque.....Php 5.00||--|\n");
    printf("|--||Sprite........Php10.00||--||Tocino.........Php15.00||--||Caldereta.......Php20.00||--||Hotcake.......Php 5.00||--|\n");
    printf("|--||Milk..........Php15.00||--||                       ||--||                        ||--||Hamburger.....Php30.00||--|\n");
    printf("|--||Coffee........Php14.00||--||                       ||--||                        ||--||Cheeseburger..Php35.00||--|\n");
    printf("|--||**********************||--||***********************||--||************************||--||**********************||--|\n");
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------||Your Wallet:Php%d.00 ||---------------------------------------------|\n",wallet-OrderPrice[i]);
    printf("|---------------------------------------------||=======================||---------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("Quantity:\n");

    for(i=0; i<NumOfOrders; i++)
    {
    SetConsoleTextAttribute(hConsole,13);
    printf("%s: ", OrderType[i]);
    scanf("%d", &OrderQuantity[i]);
    }

    system("cls");
    SetConsoleTextAttribute(hConsole,6);

    printf("|----------------------------------\\\__________________________________________________________________________________");
    printf("\n|FoodWeb.evsu.ph/E-Canteen/receipt  \\\ New Tab (+)\\\                                                                    |");
    printf("\n|------------------------------------\\\____________\\\___________________________________________________________________|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    SetConsoleTextAttribute(hConsole,8);
    printf("|   ************     ************     **********       ************   ************   ************      ************   |\n");
    printf("|   *************    ************    *************     ************   ************   *************     ************   |\n");
    printf("|   ***        ***   ************   ***        ****    ************   ************   ***        ***    ************   |\n");
    printf("|   ***        ***   ***            ***         ****   ***                ****       ***         ***       ****       |\n");
    printf("|   ***        ***   ***            ***         ****   ***                ****       ***         ***       ****       |\n");
    printf("|   ***       ***    ************   ***                ************       ****       ***        ***        ****       |\n");
    printf("|   ***********      ************   ***                ************       ****       *************         ****       |\n");
    printf("|   ***********      ***            ***                ***                ****       ***********           ****       |\n");
    printf("|   ***      ***     ***            ***         ****   ***                ****       ***                   ****       |\n");
    printf("|   ***        ***   ************   ***        ****    ************   ************   ***                   ****       |\n");
    printf("|   ***         ***  ************   **************     ************   ************   ***                   ****       |\n");
    printf("|   ***          *** ************   *************      ************   ************   ***                   ****       |\n");
    SetConsoleTextAttribute(hConsole,6);
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");

    SetConsoleTextAttribute(hConsole,9);
    for(i=0; i<NumOfOrders; i++)
    {
    printf("\t\t\t\t%s", OrderType[i]);
    printf("\t\tx%d",OrderQuantity[i]);
    printf("\t\tPhp%d.00\n",OrderPrice[i]*OrderQuantity[i]);
    }

    for(i=0; i<NumOfOrders; i++)
    {
        sumofAll += OrderPrice[i]*OrderQuantity[i];
        change=wallet-sumofAll;
    }
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("\t\t\t\tWallet:\t\t\t\tPhp%d.00\n", wallet);
    printf("\t\t\t\tTotal:\t\t\t\tPhp%d.00\n",sumofAll);
    printf("\t\t\t\tChange:\t\t\t\tPhp%d.00\n",change);
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    SetConsoleTextAttribute(hConsole,14);

    printf("\t\t\t\t\t***THANKYOU FOR ORDERING***\n");
    printf("\t\t\t\t***Please wait for your order to arrive***\n");
    printf("|---------------------------------------------------------------------------------------------------------------------|\n");
    PlaySound(TEXT("wav\\ty.wav"),NULL,SND_SYNC);
    SetConsoleTextAttribute(hConsole,10);

    printf("|\t\t\t\t\t\t LOG OUT");
    printf("|\n\t\t\t\t\tPress any key to Log Out:");
    getch();
    goto top;

    return 0;




            }
            else {
                system("cls");
                printf("|------------------------------\\\______________________________________________________________________________________");
                printf("\n|FoodWeb.evsu.ph/InvalidPassword\\\ New Tab (+)\\\                                                                        |");
                printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
                printf("\n                                                                                                                   \n\n");
                printf("\n\t\t\t\t\tInvalid Username or Password!!!\n\n\n\n\n");
                printf("Type any key to Continue:");
                getch();
                goto logAgain;
                Beep(800,300);
            }
            usrFound = 1;
        }
    }
        if (!usrFound){
            system("cls");
            printf("|------------------------------\\\______________________________________________________________________________________");
            printf("\n|FoodWeb.evsu.ph/NotRegistered  \\\ New Tab (+)\\\                                                                        |");
            printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
            printf("\n                                                                                                                   \n\n");
            printf("\n\n\t\t\t\t\tUser is not registered!!!\n\n\n\n\n");
            Beep(800,300);
            printf("\t\t\t\t\tType any key to continue");
            getch();
            goto nr;

        }
        fclose(fp);
        break;
    }
    case 3:{
            system("cls");
            SetConsoleTextAttribute(hConsole,9);
            printf("|------------------------------\\\______________________________________________________________________________________");
            printf("\n|FoodWeb.evsu.ph/Exit           \\\ New Tab (+)\\\                                                                        |");
            printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
            printf("\n                                                                                                                       \n\n");
            printf("\n                                                                                                                       \n\n");
            SetConsoleTextAttribute(hConsole,4);
            printf("\n                                               PLEASE COME BACK AGAIN :)                                         \n\n\n\n\n");
            SetConsoleTextAttribute(hConsole,9);

            break;

            }

      default:{
            printf("|------------------------------\\\______________________________________________________________________________________");
            printf("\n|FoodWeb.evsu.ph/Error          \\\ New Tab (+)\\\                                                                        |");
            printf("\n|--------------------------------\\\____________\\\_______________________________________________________________________|\n");
            printf("\n                                                                                                                       \n\n");
            printf("\n                                                                                                                       \n\n");
            SetConsoleTextAttribute(hConsole,4);
            printf("\n                                               PLEASE TYPE THE CORRECT CHOICES                                       \n\n\n\n\n");
            SetConsoleTextAttribute(hConsole,9);
            return 0;

      }


     }



}














