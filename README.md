## Result Sheet

### Calculation Condition:

1. **Student ID:** Apply validation, Unique value for each Student; consider 6-digit Student_ID where Leftmost digit is character "S" and rest of 5 digit are Numeric type.
2. **Grade Point:** Use appropriate formula to find out Grade Point for each subjects as per below condition on Marks and Grade Point:
    
    
    | Marks | Grade Point |
    | --- | --- |
    | 80-100 | 5.00 |
    | 70-79 | 4.00 |
    | 60-69 | 3.00 |
    | 50-59 | 2.00 |
    | 00-49 | 0.00 |
    | Abs | Absent |
3. **Total:** Use appropriate formula to calculate the calculations (Calculate on the basis of Type).
4. Grade Point Average (GPA): Calculate with appropriate formula from all subjects Grade Point.
5. **Letter Grade:** Use appropriate formula to find out Letter Grade from GPA column as per below conditions
    
    
    | Grade Point Average | Letter Grade |
    | --- | --- |
    | 5.00 | A+ |
    | 4.00 - 4.99 | A |
    | 3.00-3.99 | B |
    | 2.00-2.99 | C |
    | 0.00-1.99 | F |
    | Absent | Absent |
6. **Position (Rank):** Use appropriate formula to find rank from GPA column.
7. **Conditional Formatting:** Apply Conditional Formatting on "Comments" column to highlight with Green Colour when "Pass", and with Yellow Colour when "Fail" and with Red Colour when "Absent".
8. **VLOOKUP:** Use the appropriate formula for looking up student names names. Make a dropdown list on the student names (As per Sample). The GPA column should show the GPA.
9. **Chart:** Insert a Column Chart for Student Name vs Total Marks (Refer to Sample).

### Sample Table:

| A | B | C | D | E | F | G | H | I | J | K | L | M | N |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  | Student ID | Student Name | Mathematics |  | ICT |  | Bangla |  | Total Marks | GPA | Letter Grade | Position | Comment (Pass/ Fail/ Absent) |
| 1 |  |  | Marks | Grade Point | Marks | Grade Point | Marks | Grade Point |  |  |  |  |  |
| 2 | S10001 | A | 55 |  | 65 |  | 43 |  |  |  |  |  |  |
| 3 | S10002 | B | 45 |  | 70 |  | 81 |  |  |  |  |  |  |
| 4 | S10003 | C | 60 |  | 60 |  | 60 |  |  |  |  |  |  |
| 5 | S10004 | D | Abs |  | 63 |  | 53 |  |  |  |  |  |  |
| 6 | S10005 | E | 99 |  | 75 |  | 75 |  |  |  |  |  |  |

### Formula:

1. Student ID Data Validation: 
    
    ```
    =AND(COUNTIF($A$3:$A$7,A3)=1,LEFT(A3,1)="S",LEN(A3)=6,ISNUMBER(VALUE(RIGHT(A3,5))))
    ```
    
2. **Grade Point:** 
    
    ```
    =IF(C3="Abs","Absent",IF(C3>=80,5,IF(C3>=70,4,IF(C3>=60,3,IF(C3>=50,2,IF(C3<50,0))))))
    ```
    
3. Grade Point Average (GPA):**:** 
    
    ```
    =IF(J4="Absent","Absent",AVERAGE(E4,G4,I4))
    ```
    
4. **Total Marks:** 
    
    ```
    =IF(OR(D4="Abs",F4="Abs",H4="Abs"),"Absent",D4+F4+H4)
    ```
    
5. **Letter Grade:** 
    
    ```
    =IF(K4="Absent","Absent",IF(K4=5,"A+",IF(K4>=4,"A",IF(K4>=3,"B",IF(K4>=2,"C",IF(K4>=0,"F"))))))
    ```
    
6. **Position/Rank:** 
    
    ```
    =IF(K4="Absent","-",RANK(K4,$K$4:$K$8,0))
    ```
    

### VLOOKUP Sample Table:

|  | C | D |
| --- | --- | --- |
| 12 | Student Name | GPA |
| 13 | B | 3 |

**Vlookup Formula for GPA:**

```
=VLOOKUP(C13,$C$4:$K$8,9,0)
```

## Electricity  Bill

### Calculation Condition:

1. **Cust_ID:** Apply validation for unique ID for each customer. ID should be 6-digit numeric value.
2. **Cust. Name:** Name should be filled automatically according to Cust_ID.
3. **Meter Reading date:** Apply cell format for showing the date as per sample and must be valid for within the date of July 1, 2023 to June 30, 2024.
4. **Consumed Unit:** Use appropriate formula
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
6. **Service Charge:** Use the formula to place Tk 500 automatically for the customer who minimum use 1 unit
of electricity.
7. **Bill Amount:** Bill Amount must be calculated by the summation of electricity charge and Service Charge.
8. **Rank:** Use formula to generate ranking value based on "Bill Amount"

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

### Formula:

1. Co**nsumed Unit:**
    
    ```
    =E4-D4
    ```
    
2. **Electricity Charge**
    
    ```
    =IF(F4<=75,F4*4.19,IF(F4<=200,F4*5.72,IF(F4<=400,F4*6.34,IF(F4<=500,F4*9.94,IF(F4>500,F4*11.46)))))
    ```
    
3. S**ervice Charge**
    
    ```
    =IF(F4>0,500)
    ```
    
4. **Rank**
    
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