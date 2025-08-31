## Context
- [Result Sheet](#result-sheet)
- [Electricity Bill](#electricity--bill)
- [Monthly Budget Tracker](#monthly-budget-tracker)
- [Monthly Salary Sheet](#monthly-salary-sheet)

## Result Sheet

---

### Sample Table:

|  | A | B | C | D | E | F | G | H | I | J | K | L | M |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Student ID | Student Name | Mathematics |  | ICT |  | Bangla |  | Total Marks | GPA | Letter Grade | Position | Comment (Pass/ Fail/ Absent) |
| 1 |  |  | Marks | Grade Point | Marks | Grade Point | Marks | Grade Point |  |  |  |  |  |
| 2 | S10001 | A | 55 |  | 65 |  | 43 |  |  |  |  |  |  |
| 3 | S10002 | B | 45 |  | 70 |  | 81 |  |  |  |  |  |  |
| 4 | S10003 | C | 60 |  | 60 |  | 60 |  |  |  |  |  |  |
| 5 | S10004 | D | Abs |  | 63 |  | 53 |  |  |  |  |  |  |
| 6 | S10005 | E | 99 |  | 75 |  | 75 |  |  |  |  |  |  |

### Calculation Condition:

1. **Student ID:** Apply validation, Unique value for each Student; consider 6-digit Student_ID where Leftmost digit is character "S" and rest of 5 digit are Numeric type.
    
    ```
    =AND(COUNTIF($A$3:$A$7,A3)=1,LEFT(A3,1)="S",LEN(A3)=6,ISNUMBER(VALUE(RIGHT(A3,5))))
    ```
    
2. **Grade Point:** Use appropriate formula to find out Grade Point for each subjects as per below condition on Marks and Grade Point:
    
    
    | Marks | Grade Point |
    | --- | --- |
    | 80-100 | 5.00 |
    | 70-79 | 4.00 |
    | 60-69 | 3.00 |
    | 50-59 | 2.00 |
    | 00-49 | 0.00 |
    | Abs | Absent |
    
    ```
    =IF(C3="Abs","Absent",IF(C3>=80,5,IF(C3>=70,4,IF(C3>=60,3,IF(C3>=50,2,IF(C3<50,0))))))
    ```
    
3. **Total:** Use appropriate formula to calculate the calculations (Calculate on the basis of Type).
    
    ```
    =IF(OR(D4="Abs",F4="Abs",H4="Abs"),"Absent",D4+F4+H4)
    ```
    
4. **Grade Point Average (GPA):** Calculate with appropriate formula from all subjects Grade Point.
    
    ```
    =IF(J4="Absent","Absent",AVERAGE(E4,G4,I4))
    ```
    
5. **Letter Grade:** Use appropriate formula to find out Letter Grade from GPA column as per below conditions
    
    
    | Grade Point Average | Letter Grade |
    | --- | --- |
    | 5.00 | A+ |
    | 4.00 - 4.99 | A |
    | 3.00-3.99 | B |
    | 2.00-2.99 | C |
    | 0.00-1.99 | F |
    | Absent | Absent |
    
    ```
    =IF(K4="Absent","Absent",IF(K4=5,"A+",IF(K4>=4,"A",IF(K4>=3,"B",IF(K4>=2,"C",IF(K4>=0,"F"))))))
    ```
    
6. **Position (Rank):** Use appropriate formula to find rank from GPA column.
    
    ```
    =IF(K4="Absent","-",RANK(K4,$K$4:$K$8,0))
    ```
    
7. **Conditional Formatting:** Apply Conditional Formatting on "Comments" column to highlight with Green Colour when "Pass", and with Yellow Colour when "Fail" and with Red Colour when "Absent".
8. **VLOOKUP:** Use the appropriate formula for looking up student names names. Make a dropdown list on the student names (As per Sample). The GPA column should show the GPA.
    
    ### VLOOKUP Sample Table:
    
    |  | C | D |
    | --- | --- | --- |
    | 12 | Student Name | GPA |
    | 13 | B | 3 |
    
    **Vlookup Formula for GPA:**
    
    ```
    =VLOOKUP(C13,$C$4:$K$8,9,0)
    ```
    
9. **Chart:** Insert a Column Chart for Student Name vs Total Marks (Refer to Sample).
    
    ![image.png](attachment:5969ba81-c553-4f46-beac-26e972cdc53c:image.png)
    

## Electricity  Bill

---

### Sample Table:

|  | A | B | C | D | E | F | G | H | I | J |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Cust_ID | Cust. Name | Meter Reading Date | Prev. Unit | Curr. Unit | Consumed Unit | Electricity Charge | Service Charge | Bill Amount | Rank |
| 2 | 101001 | B | December 15, 2023 | 6582 | 6781 |  |  |  |  |  |
| 3 | 101002 | B | December 16, 2023 | 6582 | 6781 |  |  |  |  |  |
| 4 | 101003 | C | December 17, 2023 | 7810 | 7908 |  |  |  |  |  |
| 5 | 101004 | D | December 18, 2023 | 21105 | 21935 |  |  |  |  |  |
| 6 | 101005 | E | December 19, 2023 | 3511 | 3961 |  |  |  |  |  |
| 7 | 101006 | F | December 20, 2023 | 45214 | 49054 |  |  |  |  |  |

### Calculation Condition:

1. **Cust_ID:** Apply validation for unique ID for each customer. ID should be 6-digit numeric value.
    
    ```
    =AND(LEN(A2)=6,COUNTIF($A$2:$A$7,A2)=1)
    ```
    
2. **Cust. Name:** Name should be filled automatically according to Cust_ID.
    
    ```
    =IF(OR(A2=101001,A2=101002),"B",IF(A2=101003,"C",IF(A2=101004,"D",IF(A2=101005,"E",IF(A2=101006,"F")))))
    ```
    
3. **Meter Reading date:** Apply cell format for showing the date as per sample and must be valid for within the date of July 1, 2023 to June 30, 2024.
4. **Consumed Unit:** Use appropriate formula
    
    ```
    =E4-D4
    ```
    
5. **Electricity Charge:**
Use appropriate formula for calculating electricity charge. The range of consumption and rate per units see in the table.
    
    
    | Range of Consumption | Rate per unit |
    | --- | --- |
    | 0-75 units | Tk 4.19 |
    | 76-200 units | Tk 5.72 |
    | 201-400 units
    401-500 units | Tk 6.34
    Tk 9.94 |
    | Above 500 units | Tk 11.46 |
    
    ```
    =IF(F4<=75,F4*4.19,IF(F4<=200,F4*5.72,IF(F4<=400,F4*6.34,IF(F4<=500,F4*9.94,IF(F4>500,F4*11.46)))))
    ```
    
6. **Service Charge:** Use the formula to place Tk 500 automatically for the customer who minimum use 1 unit of electricity.
    
    ```
    =IF(F4>0,500)
    ```
    
7. **Bill Amount:** Bill Amount must be calculated by the summation of electricity charge and Service Charge.
    
    ```
    =G2+H2
    ```
    
8. **Rank:** Use formula to generate ranking value based on "Bill Amount"
    
    ```
    =RANK(I4,$I$4:$I$9,0)
    ```
    

### VLOOKUP Sample Table

|  | A | B |
| --- | --- | --- |
| 12 | VLOOKUP |  |
| 13 | Cust_ID | Bill Amount |
| 14 | 101006 | 44506.4 |

**VLookup formula:**

```
=VLOOKUP(A14,$A$4:$I$9,9,0)
```

## Monthly Budget Tracker

---

## Sample Table:

|  | A | B | C | D | E | F | G |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 |  |  |  |  |  |  |  |
| 2 | Date | Category | Description | Amount | Budget Range | Rank | Type |
| 3 | 1-Jun-24 | Income | Salary | 30000 |  |  |  |
| 4 | 2-Jun-24 | Housing | Rent | 12000 |  |  |  |
| 5 | 3-Jun-24 | Utilities | Electricity Bill | 1100 |  |  |  |
| 6 | 4-Jun-24 | Food | Groceries (Vegetables) | 600 |  |  |  |
| 7 | 5-Jun-24 | Food | Groceries (Fish) | 1800 |  |  |  |
| 8 | 6-Jun-24 | Utilities | Internet Bill | 500 |  |  |  |
| 9 | 7-Jun-24 | Transport | Office transport | 700 |  |  |  |
| 10 | 8-Jun-24 | Entertainment | Movie | 400 |  |  |  |
| 11 | 8-Jun-24 | Food | Groceries (Vegetables) | 800 |  |  |  |
1. **Date Format:** Use date format as DD-MMM-YY in ‘Date’ Column.
2. **Category:** Apply data validation for Category names. Category names other than “Income,
Housing, Utilities, Food, Transport, Entertainment” will not be allowed. (Use Custom Rule,
don’t use List Rule)
    
    ```
    =OR(B3="Income",b3="Housing",b3="Utilities",b3="Food",b3="Transport",b3="Entertainment")
    ```
    
3. Apply Conditional Formatting on Type column to highlight “Income” with Green colour and
“Expense” with Red Color (As per Sample). Type will come automatically from Category.
Only “Income” Category will be defined as “Income”, all others will be “Expense”.
    
    ```
    =IF(B3="Income","Income","Expense")
    ```
    
4. **Total:** Use appropriate formula to calculate the total Income and Expenses and show it in
a separate table (Calculate on the basis of Type)
    
    
    |  | A | B |
    | --- | --- | --- |
    | 14 | Total Monthly Income |  |
    | 15 | Total Monthly Expenses |  |
    | 16 | Net Balance |  |
    1. **Total Income:**
        
        ```
        =SUMIF(G3:G11,"Income",D3:D11)
        ```
        
    2. **Total Expenses:**
        
        ```
        =SUMIF(G3:G11,"Expense",D3:D11)
        ```
        
    3. **Net Balance:**
        
        ```
        =B14-B15
        ```
        
5. **Budget Range:** Use appropriate formula to indicate “Income” or “In Range” or “Over
Budget” as per below conditions on Type and Amount:
    
    
    | **Type** | **Amount** | **Range** |
    | --- | --- | --- |
    | Income | – | Income |
    | Expense | > 20% of Income | Over Budget |
    | Expense | < 20% of Income | In Range |
    
    ```
    =IF(B3="Income","Income",IF(D3>20%*$D$3,"Over Budget",IF(D3<20%*$D$3,"In Range")))
    ```
    
6. **Rank:** Use appropriate formula to show Ranking of expenses (Only which types are
‘Expense’) in this column. (Use Helper Table as necessary)
    
    
    |  | I |
    | --- | --- |
    | 1 | Helper Table for Rank |
    | 2 | Expenses |
    | 3 | - |
    | 4 | 12000 |
    | 5 | 1100 |
    | 6 | 600 |
    | 7 | 1800 |
    | 8 | 500 |
    | 9 | 700 |
    | 10 | 400 |
    | 11 | 800 |
    1. Helper Table for Rank Expenses: 
        
        ```
        =IF(G4="Expense",D4,"-")
        ```
        
    2. Rank: 
        
        ```
        =IF(G4="Income","-",RANK(I4,$I$3:$I$11,0))
        ```
        
7. **Lookup:** Use appropriate formula for looking up total expenses by the category. Make a
dropdown list on the category to show total expenses (As per Sample). The Total Amount
column should show total of the same category. (Use Helper Table as necessary)

## Monthly Salary Sheet

### Sample Table

|  | A | B | C | D | E | F | G | H | I | J |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Employee ID | Basic Salary | Allowances | Tax Rate(%) | Tax Amount | LoanDeduction | TotalDeduction | GrossSalary | NetSalary | BudgetRange |
| 2 | E001 | 6000 | 1000 | 10 |  | 400 |  |  |  |  |
| 3 | E002 | 5000 | 1200 | 15 |  | 500 |  |  |  |  |
| 4 | E003 | 4000 | 1500 | 20 |  | 500 |  |  |  |  |
| 5 | E004 | 3000 | 1000 | 10 |  | 500 |  |  |  |  |
| 6 | E005 | 8000 | 500 | 15 |  | 500 |  |  |  |  |

### Calculation Condition:

1. **Total:** Use appropriate formula to calculate the calculations (Calculate on the basis of Type).
2. **Tax Amount:** Calculate with appropriate formula from Basic Salary and Tax Rate.
    
    ```
    =B2*D2%
    ```
    
3. **Total Deduction:** Tax Amount + Loan Deduction.
    
    ```
    =E2+F2
    ```
    
4. **Gross Salary:** Basic Salary + Allowances.
    
    ```
    =B2+C2
    ```
    
5. **Net Salary:** Gross Salary - Total Deduction.
    
    ```
    =H2-G2
    ```
    
6. Budget Range: Use appropriate formula to indicate `In Range Deduct` or `Over Deduct` as per below conditions on Type and Amount:

    
    
    | Type | Amount | Range |
    | --- | --- | --- |
    | Tax Rate | > 10% of Basic Salary | Over Deduct |
    | Tax Rate | <= 10% of Basic Salary | In Range Deduct |
    
    ```
    =IF(D2>10,"Over Deduct","In Range Deduct")
    ```
    
7. **Conditional Formatting:** Apply Conditional Formatting on `Budget Range` column to highlight with `Green colour` when Budget Range is `In Range Deduct` and with `Red Colour` when Tax Budget Range
`Over Deduct`
8. **Category Names:** Apply data validation for Category Names. Category names other than "Basic Salary, Allowance, Gross Salary, Tax Deduct, Loan Deduct, Total Deduct and Net Salary" will not be allowed (Use Custom Rule, don't use List Rule).
    
    ### Category Table:
    
    |  | A | B | C |
    | --- | --- | --- | --- |
    | 9 | Category Names | TotalAmount | Types |
    | 10 | Basic Salary |  |  |
    | 11 | Allowance |  |  |
    | 12 | Gross Salary |  |  |
    | 13 | Tax Amount |  |  |
    | 14 | Loan Deduction |  |  |
    | 15 | Total Deduction |  |  |
    | 16 | Net Salary |  |  |
    
    ```
    =OR(A10="Basic Salary",A10="Allowance",A10="Gross Salary",A10="Tax Amount",A10="Loan Deduction",A10="Total Deduction",A10="Net Salary")
    ```
    
9. **Types:** Types column will fill-up automatically from Category. The "Basic Salary, Allowances, Gross Salary and Net Salary" Category will be defined as "Income", all others will be "Expense".
    
    ```
    =IF(OR(A10="Basic Salary",A10="Allowance",A10="Gross Salary"),"Income","Expense")
    ```
    
10. VLOOKUP: Use the appropriate formula for looking up category names. Make a dropdown list on the category names (As per Sample). The Total Amount column should show sum of the same category. (Use Helper Table as necessary).
    
    ### VLOOKUP Table
    
    |  | F | G |
    | --- | --- | --- |
    | 11 | VLOOKUP |  |
    | 12 | Category | Total Amount |
    | 13 |  |  |
    
    ```
    =VLOOKUP(F13,$A$10:$B$16,2,0)
    ```
    
11. Chart: Insert a Column Chart for Net Salary vs Total Deductions (Refer to Sample).
    
    ![image.png](attachment:f58cc7bb-52c4-4e33-afb5-eaeaa69a43f4:image.png)
    

## Weekly Wages Sheet

Sample Table:

|  | A | B | C | D | E | F | G | H | I | J |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Emp_ID | Name | Designation | Hours/Work | Basic Wages | Overtime Wages | Medical Allowance | Gross Amount | Income Tax (IT) | Net Amount |
| 2 | E101001 | A | Grade-1 | 40 |  |  |  |  |  |  |
| 3 | E101002 | B | Grade-3 | 55 |  |  |  |  |  |  |
| 4 | E101003 | C | Grade-2 | 43 |  |  |  |  |  |  |
| 5 | E101004 | D | Grade-3 | 44 |  |  |  |  |  |  |
| 6 | E101005 | E | Grade-1 | 48 |  |  |  |  |  |  |
| 7 | E101006 | F | Grade-3 | 54 |  |  |  |  |  |  |
| 8 | E101007 | G | Grade-2 | 45 |  |  |  |  |  |  |
| 9 | E101008 | H | Grade-1 | 60 |  |  |  |  |  |  |
| 10 | E101009 | I | Grade-2 | 47 |  |  |  |  |  |  |
| 11 | E101010 | J | Grade-3 | 49 |  |  |  |  |  |  |

### **Calculation Condition:**

1. **EMP_ID:** Apply validation, Unique value for each Employee; consider 7 digit Emp_ID where Leftmost digit is character "E" and rest of 6 digit are Numeric type.
    
    ```
    =AND(COUNTIF($A$2:$A$11,A2)=1,LEN(A2)=7,LEFT(A2,1)="E",ISNUMBER(VALUE(RIGHT(A2,6))))
    ```
    
2. **Designation:** Apply dropdown List to choose designation (Grade-1, Grade-2 and Grade-3)
3. **Basic Wages:** Up to 40 hours wages is base wages. Values are autofill following below condition:
    1. Grade-1: 150 Taka/Hour
    2. Grade-2: 125 Taka/Hour
    3. Grade-3: 100 Taka/Hour
    
    ```
    =IF(C2="Grade-1",MIN(D2,40)*150,IF(C2="Grade-2",MIN(D2,40)*125,IF(C2="Grade-3",MIN(D2,40)*100)))
    ```
    
4. **Overtime Wages:** Hours above 40 are count as overtime hours. Calculate Overtime Wages as 200 Taka/Hour using autofill formula.
    
    ```
    =IF(D2>40,(D2-40)*200,0)
    ```
    
5. **Medical allowances:** Fixed Tk. 500/week for all allowance.
6. Gross Wages: Base Wages + Overtime Wages
    
    ```
    =E2+F2
    ```
    
7. Income Tax (IT): 10% of Gross wages.
    
    ```
    =H2*10%
    ```
    
8. Net Amount: (Gross Wages + Medical Allowance) - IT
    
    ```
    =(H2+G2)-I2
    ```

## Others
- https://docs.google.com/spreadsheets/d/1B9I8s57DkzVTJERNnJF-trP-yoxz857X/edit?usp=sharing&ouid=116277591153016490720&rtpof=true&sd=true

- https://docs.google.com/spreadsheets/d/1psk9Zz08Mnen-yklicG-HEbrTjvH8DHB/edit?usp=sharing&ouid=116277591153016490720&rtpof=true&sd=true

- https://docs.google.com/spreadsheets/d/1IZRO9PWkqPAWaFe0XAbVox_b5VYdDL9O/edit?usp=sharing&ouid=116277591153016490720&rtpof=true&sd=true
