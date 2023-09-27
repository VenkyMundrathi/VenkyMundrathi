- 👋 Hi, I’m @VenkyMundrathi
- 👀 I’m interested in ...
- 🌱 I’m currently learning about online covid registrations...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

include <conio.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_DAYS 31
#define MAX_MONTHS 12

// Defining Structure
typedef struct mynode {
	char name[20];
	char gen[6];
	char idtype[40];
	char id[20];
	char mob[20];
	char comor[3];
	struct mynode* link;
} Node;
Node* start = NULL;
	char mobileNumber[20];

// Global Variables
int n;
char state[20], dis[20], hos[40], date[12], hour[6];

// Declaring Function Used In This Program
void heading();
void details();
void venue();
int det();
void printDayWiseReport(int registrations[][MAX_DAYS], int daysInMonth[]);
void printMonthWiseReport(int registrations[][MAX_DAYS], int daysInMonth[]);
void receipt();
void addnode(char a[20], char b[6], char c[40], char d[20],
			char e[20], char f[3]);
// Function To Take Candidate Numbers & Details
void details()
{
	int i;
	char a[20], b[6], c[40], d[20], e[20], f[3];
                                                                             5

	// Calling Heading() Function
	heading();
	printf(
		"\t\t\t\tEnter Candidate Number (Max 4 People): ");
	scanf("%d", &n);

	// Taking Candidate Details
	for (i = 1; i <= n; i++) {
		// For Clear Screen
		system("cls");

		// Calling Heading() Function
		heading();
		printf("\t\t\t\tEnter The %dth Candidate Name: ",
			i);
		fflush(stdin);
		gets(a);
		printf("\t\t\t\tEnter The %dth Candidate Gender: ",
			i);
		fflush(stdin);
		gets(b);
		printf("\t\t\t\tEnter The %dth Candidate Id-Type(like:- aadhar,pan): ",
			i);
		fflush(stdin);
		gets(c);
		printf(
			"\t\t\t\tEnter The %dth Candidate (12-Digit) Id-Number: ",
			i);
		fflush(stdin);
		gets(d);
		mbl:

    printf("Enter a 10-digit mobile number: ");
    fgets(mobileNumber, sizeof(mobileNumber), stdin);

    // Remove the newline character at the end of the string
    mobileNumber[strcspn(mobileNumber, "\n")] = '\0';

    // Check if the number has exactly 10 digits
    if (strlen(mobileNumber) == 10) {
        printf("Mobile number is valid.\n”);        
    } else {
        printf("Entered mobile number is not valid.\n");
        goto mbl;
    }
    printf("\t\t\t\tEnter The %dth (10-digit) Candidate Mobile "
			"Number: ",
			i);
		fflush(stdin);
		gets(e);

   		printf("\t\t\t\tEnter The %dth Candidate "
			"Co-Morbidity Status (Yes or No): ",
			i);
		fflush(stdin);
		gets(f);

		// Calling Function addnode()
		addnode(a, b, c, d, e, f);
	}
}

// Function To Create Node & Insert Data Like Linked List
void addnode(char a[20], char b[6], char c[40], char d[20],
			char e[20], char f[3])
{
	Node *newptr = NULL, *ptr;
	newptr = (Node*)malloc(sizeof(Node));
	strcpy(newptr->name, a);
	strcpy(newptr->gen, b);
	strcpy(newptr->idtype, c);
	strcpy(newptr->id, d);
	strcpy(newptr->mob, e);
	strcpy(newptr->comor, f);
	newptr->link = NULL;
	if (start == NULL)
		start = newptr;
	else {
		ptr = start;
		while (ptr->link != NULL)
			ptr = ptr->link;
		ptr->link = newptr;
	}
}

// Function To Take Date & Time Details
void venue()
{
	int i, x = 0;

	// For Clear Screen
	system("cls");

	// Calling Heading() Function
	heading();
	printf("\t\t\t\tEnter State: ");
	gets(state);
	printf("\t\t\t\tEnter District: ");
	gets(dis);
	printf("\t\t\t\tEnter Date (DD-MM-YY): ");
	gets(date);
	printf("\t\t\t\tEnter Time (12 Hours): ");
	gets(hour);

	// For Clear Screen
	system("cls");

	// Calling Heading() Function
	heading();

	// List Of Hospitals Available
	printf("\t\t\t\t1. MGM Hospital\n");
	printf("\t\t\t\t2. AJARA  Hospital\n");
	printf("\t\t\t\t3. MAX CARE Hospital\n");

	// Taking Hospital Choice
	do {
		printf("\t\t\t\tEnter Choice: ");
		scanf("%d", &i);
		if (i == 1)
			strcpy(hos, "MGM Hospital");
		else if (i == 2)
			strcpy(hos, "AJARA Hospital");
		else if (i == 3)
			strcpy(hos, "MAX CARE Hospital");
		else {
			printf("Enter Correct Choice...");
			x = 1;
		}
	} while (x);
}

// Function To Print Receipt
void receipt()
{
	int i,c;
	Node* ptr = start;

	// For Clear Screen
	system("cls");
	heading();
	printf(
		"\n\t\t\t\t*Take Screenshot For Further Use*\n");

	// Printing Candidate All Details
	for (i = 1; i <= n; i++) {
		printf("\t\t\t\t%dst Candidate Name: ", i);
		puts(ptr->name);
		printf("\t\t\t\t%dst Candidate Gender: ", i);
		puts(ptr->gen);
		printf("\t\t\t\t%dst Candidate Id-type: ", i);
		puts(ptr->idtype);
		printf("\t\t\t\t%dst Candidate Id Number: ", i);
		puts(ptr->id);
		printf("\t\t\t\t%dst Candidate Mobile Number: ", i);
		puts(ptr->mob);
		printf(
			"\t\t\t\t%dst Candidate Co-Morbidity Status: ",
			i);
		puts(ptr->comor);
		printf("\n");
		ptr = ptr->link;
	}
	printf("\t\t\t\tState: ");
	puts(state);
	printf("\t\t\t\tDistrict: ");
	puts(dis);
	printf("\t\t\t\tDate: ");
	puts(date);
	printf("\t\t\t\tTime: ");
	puts(hour);
	printf("\t\t\t\tChosen Hospital: ");
	puts(hos);
	printf("\n\t\t\t\t*Thank You For registration*");
	printf("\n\n\n\n");
	system("pause");
	printf("\n\nPress 1 to show the registration information\n");
	printf("or press zero to terminate the program");
	scanf("%d",&c);
	if(c==1)
             det();

       else
           exit(0);     
}

// Function To Make Heading Of Portal
void heading()
{
	printf(
		"\t\t\t\t*Covid Vaccination Registration*\n");
	printf("\t\t\t***Take Vaccine At Your Time & Fight "
		"Against Corona***\n\n");
}



void printDayWiseReport(int registrations[][MAX_DAYS], int daysInMonth[]) 
{
    printf("Day-wise Report:\n");
    int i,month,day;
    for ( month = 0; month < MAX_MONTHS; month++) {
        for (day = 0; day < daysInMonth[month]; day++) {
            printf("Month %d, Day %d: %d registrations\n", month + 1, day + 1, registrations[month][day]);
        }
    }
    printf("\n");
}

void printMonthWiseReport(int registrations[][MAX_DAYS], int daysInMonth[]) {
    printf("Month-wise Report:\n");
    int totalDone = 0,month,day;
    for (month = 0; month < MAX_MONTHS; month++) {
        int monthTotal = 0;
        for (day = 0; day < daysInMonth[month]; day++) {
            monthTotal += registrations[month][day];
        }
        totalDone += monthTotal;
        printf("Total registrations for Month %d: %d\n", month + 1, monthTotal);
    }
    int totalLeft = MAX_DAYS * MAX_MONTHS - totalDone;
    printf("\nTotal registrations done: %d\n", totalDone);
    
}

int det()
{
    int registrations[MAX_MONTHS][MAX_DAYS] = {0};
    int daysInMonth[MAX_MONTHS] = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
    int choice;

    // Simulated registrations data
    registrations[0][1] = 1096;    // January, Day 1
    registrations[0][2] = 122;registrations[0][3] = 196;registrations[0][4] = 1066;registrations[0][5] = 1226;registrations[0][6] = 1556;registrations[0][7] = 1446;registrations[0][8] = 1096;registrations[0][9] = 1006;registrations[0][10] = 1096;registrations[0][11] = 2316;registrations[0][12] = 1296;registrations[0][13] = 1096;registrations[0][14] = 1395;registrations[0][15] = 2226;registrations[0][16] = 1492;registrations[0][17] = 3362;registrations[0][18] = 1096;registrations[0][19] = 1016;registrations[0][20] = 1236;registrations[0][21] = 1096;registrations[0][22] = 1326;registrations[0][23] = 1856;registrations[0][24] = 1226;registrations[0][25] = 1091;registrations[0][26] = 1042;registrations[0][27] = 1262;registrations[0][28] = 1096;registrations[0][29] = 1436;registrations[0][30] = 2346;
    ////////////
    registrations[1][29] = 7723;    // February, Day 15
    registrations[1][2] = 122;
    registrations[1][3] = 196;registrations[1][4] = 1066;registrations[1][5] = 1226;registrations[1][6] = 1556;registrations[1][7] = 1446;registrations[1][8] = 1096;registrations[1][9] = 1006;registrations[1][10] = 1096;registrations[1][11] = 2316;registrations[1][12] = 1296;registrations[1][13] = 1096;registrations[1][14] = 1395;registrations[1][15] = 2226;registrations[1][16] = 1492;registrations[1][17] = 3362;registrations[1][18] = 1096;registrations[1][19] = 1016;registrations[1][20] = 1236;registrations[1][21] = 1096;registrations[1][22] = 1326;registrations[1][23] = 1856;registrations[1][24] = 1226;registrations[1][25] = 1091;registrations[1][26] = 1042;registrations[1][27] = 1262;registrations[1][28] = 1096;registrations[1][29] = 1436;
    /////////
    registrations[2][30] = 1325;    // March, Day 10
    registrations[2][2] = 122;
    registrations[2][3] = 196;registrations[2][4] = 1066;registrations[2][5] = 1226;registrations[2][6] = 1556;registrations[2][7] = 1446;registrations[2][8] = 1096;registrations[2][9] = 1006;registrations[2][10] = 1096;registrations[2][11] = 2316;registrations[2][12] = 1296;registrations[2][13] = 1096;registrations[2][14] = 1395;registrations[2][15] = 2226;registrations[2][16] = 1492;registrations[2][17] = 3362;registrations[2][18] = 1096;registrations[2][19] = 1016;registrations[2][20] = 1236;registrations[2][21] = 1096;registrations[2][22] = 1326;registrations[2][23] = 1856;registrations[2][24] = 1226;registrations[2][25] = 1091;registrations[2][26] = 1042;registrations[2][27] = 1262;registrations[2][28] = 1096;registrations[2][29] = 1436;registrations[2][30] = 2346;
    ///////////
    
    registrations[3][31] = 5602;
    registrations[3][2] = 122;
    registrations[3][3] = 196;registrations[3][4] = 1066;registrations[3][5] = 1226;registrations[3][6] = 1556;registrations[3][7] = 1446;registrations[3][8] = 1096;registrations[3][9] = 1006;registrations[3][10] = 1096;registrations[3][11] = 2316;registrations[3][12] = 1296;registrations[3][13] = 1096;registrations[3][14] = 1395;registrations[3][15] = 2226;registrations[3][16] = 1492;registrations[3][17] = 3362;registrations[3][18] = 1096;registrations[3][19] = 1016;registrations[3][20] = 1236;registrations[3][21] = 1096;registrations[3][22] = 1326;registrations[3][23] = 1856;registrations[3][24] = 1226;registrations[3][25] = 1091;registrations[3][26] = 1042;registrations[3][27] = 1262;registrations[3][28] = 1096;registrations[3][29] = 1436;registrations[3][30] = 2346;
    /////////
    registrations[4][31] = 9765; 
    registrations[4][2] = 122;registrations[4][3] = 1932;registrations[4][4] = 1066;registrations[4][5] = 1226;registrations[4][6] = 1556;registrations[4][7] = 1446;registrations[4][8] = 1096;registrations[4][9] = 1006;registrations[4][10] = 1096;registrations[4][11] = 2316;registrations[4][12] = 1296;registrations[4][13] = 1096;registrations[4][14] = 1395;registrations[4][15] = 2226;registrations[4][16] = 1492;registrations[4][17] = 3362;registrations[4][18] = 1096;registrations[4][19] = 1016;registrations[4][20] = 1236;registrations[4][21] = 1096;registrations[4][22] = 1326;registrations[4][23] = 1856;registrations[4][24] = 1226;registrations[4][25] = 1091;registrations[4][26] = 1042;registrations[4][27] = 1262;registrations[4][28] = 1096;registrations[4][29] = 1436;registrations[4][30] = 2346;
    ///////
    registrations[5][31] = 7831;  
    registrations[5][2] = 122;registrations[5][3] = 196;registrations[5][4] = 1066;registrations[5][5] = 1226;registrations[5][6] = 1556;registrations[5][7] = 1446;registrations[5][8] = 1096;registrations[5][9] = 1006;registrations[5][10] = 1096;registrations[5][11] = 2316;registrations[5][12] = 1296;registrations[5][13] = 1096;registrations[5][14] = 1395;registrations[5][15] = 2226;registrations[5][16] = 1492;registrations[5][17] = 3362;registrations[5][18] = 1096;registrations[5][19] = 1016;registrations[5][20] = 1236;registrations[5][21] = 1096;registrations[5][22] = 1326;registrations[5][23] = 1856;registrations[5][24] = 1226;registrations[5][25] = 1091;registrations[5][26] = 1042;registrations[5][27] = 1262;registrations[5][28] = 1096;registrations[5][29] = 1436;registrations[5][30] = 2346;
    /////////
    registrations[6][30] = 8324; 
    registrations[6][2] = 122;registrations[6][3] = 196;registrations[6][4] = 1066;registrations[6][5] = 1226;registrations[6][6] = 1556;registrations[6][7] = 1446;registrations[6][8] = 1096;registrations[6][9] = 1006;registrations[6][10] = 1096;registrations[6][11] = 2316;registrations[6][12] = 1296;registrations[6][13] = 1096;registrations[6][14] = 1395;registrations[6][15] = 2226;registrations[6][16] = 1492;registrations[6][17] = 3362;registrations[6][18] = 1096;registrations[6][19] = 1016;registrations[6][20] = 1236;registrations[6][21] = 1096;registrations[6][22] = 1326;registrations[6][23] = 1856;registrations[6][24] = 1226;registrations[6][25] = 1091;registrations[6][26] = 1042;registrations[6][27] = 1262;registrations[6][28] = 1096;registrations[6][29] = 1436;registrations[6][30] = 2346;
    //////
    registrations[7][31] = 8643;  
    registrations[7][2] = 122;registrations[7][3] = 196;registrations[7][4] = 1066;registrations[7][5] = 1226;registrations[7][6] = 1556;registrations[7][7] = 1446;registrations[7][8] = 1096;registrations[7][9] = 1006;registrations[7][10] = 1096;registrations[7][11] = 2316;registrations[7][12] = 1296;registrations[7][13] = 1096;registrations[7][14] = 1395;registrations[7][15] = 2226;registrations[7][16] = 1492;registrations[7][17] = 3362;registrations[7][18] = 1096;registrations[7][19] = 1016;registrations[7][20] = 1236;registrations[7][21] = 1096;registrations[7][22] = 1326;registrations[7][23] = 1856;registrations[7][24] = 1226;registrations[7][25] = 1091;registrations[7][26] = 1042;registrations[7][27] = 1262;registrations[7][28] = 1096;registrations[7][29] = 1436;registrations[7][30] = 2346;
    ////////
    registrations[8][31] = 5282;  
    registrations[8][2] = 122;registrations[8][3] = 196;registrations[8][4] = 1066;registrations[8][5] = 1226;registrations[8][6] = 1556;registrations[8][7] = 1446;registrations[8][8] = 1096;registrations[8][9] = 1006;registrations[8][10] = 1096;registrations[8][11] = 2316;registrations[8][12] = 1296;registrations[8][13] = 1096;registrations[8][14] = 1395;registrations[8][15] = 2226;registrations[8][16] = 1492;registrations[8][17] = 3362;registrations[8][18] = 1096;registrations[8][19] = 1016;registrations[8][20] = 1236;registrations[8][21] = 1096;registrations[8][22] = 1326;registrations[8][23] = 1856;registrations[8][24] = 1226;registrations[8][25] = 1091;registrations[8][26] = 1042;registrations[8][27] = 1262;registrations[8][28] = 1096;registrations[8][29] = 1436;registrations[8][30] = 2346;
    /////////
    registrations[9][31] = 7221;
    registrations[9][2] = 122;registrations[9][3] = 196;registrations[9][4] = 1066;registrations[9][5] = 1226;registrations[9][6] = 1556;registrations[9][7] = 1446;registrations[9][8] = 1096;registrations[9][9] = 1006;registrations[9][10] = 1096;registrations[9][11] = 2316;registrations[9][12] = 1296;registrations[9][13] = 1096;registrations[9][14] = 1395;registrations[9][15] = 2226;registrations[9][16] = 1492;registrations[9][17] = 3362;registrations[9][18] = 1096;registrations[9][19] = 1016;registrations[9][20] = 1236;registrations[9][21] = 1096;registrations[9][22] = 1326;registrations[9][23] = 1856;registrations[9][24] = 1226;registrations[9][25] = 1091;registrations[9][26] = 1042;registrations[9][27] = 1262;registrations[9][28] = 1096;registrations[9][29] = 1436;registrations[9][30] = 2346;
    //////
    registrations[10][31] = 6322;
    registrations[10][2] = 122;registrations[10][3] = 196;registrations[10][4] = 1066;registrations[10][5] = 1226;registrations[10][6] = 1556;registrations[10][7] = 1446;registrations[10][8] = 1096;registrations[10][9] = 1006;registrations[10][10] = 1096;registrations[10][11] = 2316;registrations[10][12] = 1296;registrations[10][13] = 1096;registrations[10][14] = 1395;registrations[10][15] = 2226;registrations[10][16] = 1492;registrations[10][17] = 3362;registrations[10][18] = 1096;registrations[10][19] = 1016;registrations[10][20] = 1236;registrations[10][21] = 1096;registrations[10][22] = 1326;registrations[10][23] = 1856;registrations[10][24] = 1226;registrations[10][25] = 1091;registrations[10][26] = 1042;registrations[10][27] = 1262;registrations[10][28] = 1096;registrations[10][29] = 1436;registrations[10][30] = 2346;
    ////
    registrations[11][31] = 7183; 
     registrations[11][2] = 122;registrations[11][3] = 1962;registrations[11][4] = 1066;registrations[11][5] = 1226;registrations[11][6] = 1556;registrations[11][7] = 1446;registrations[11][8] = 1096;registrations[11][9] = 1006;registrations[11][10] = 1096;registrations[11][11] = 2316;registrations[11][12] = 1296;registrations[11][13] = 1096;registrations[11][14] = 1395;registrations[11][15] = 2226;registrations[11][16] = 1492;registrations[11][17] = 3362;registrations[11][18] = 1096;registrations[11][19] = 1016;registrations[11][20] = 1236;registrations[11][21] = 1096;registrations[11][22] = 1326;registrations[11][23] = 1856;registrations[11][24] = 1226;registrations[11][25] = 1091;registrations[11][26] = 1042;registrations[11][27] = 1262;registrations[11][28] = 1096;registrations[11][29] = 1436;registrations[11][30] = 2346;
    
    ////////
    registrations[12][31] = 3971;
    registrations[12][2] = 122;registrations[12][3] = 196;registrations[12][4] = 1066;registrations[12][5] = 1226;registrations[12][6] = 1556;registrations[12][7] = 1446;registrations[12][8] = 1096;registrations[12][9] = 1006;registrations[12][10] = 1096;registrations[12][11] = 2316;registrations[12][12] = 1296;registrations[12][13] = 1096;registrations[12][14] = 1395;registrations[12][15] = 2226;registrations[12][16] = 1492;registrations[12][17] = 3362;registrations[12][18] = 1096;registrations[12][19] = 1016;registrations[12][20] = 1236;registrations[12][21] = 1096;registrations[12][22] = 1326;registrations[12][23] = 1856;registrations[12][24] = 1226;registrations[12][25] = 1091;registrations[12][26] = 1042;registrations[12][27] = 1262;registrations[12][28] = 1096;registrations[12][29] = 1436;registrations[12][30] = 2346;
    
    printf("Enter 1 for day-wise report or 2 for month-wise report: ");
    scanf("%d", &choice);

    if (choice == 1) {
        printDayWiseReport(registrations, daysInMonth);
    } else if (choice == 2) {
        printMonthWiseReport(registrations, daysInMonth);
    } else {
        printf("Invalid choice.\n");
        return 1;
    }

}

