# Excel-Formula

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
| 2 | S10001 | A | 55 | 2 | 65 | 3 | 43 | 0 | 163 | 1.67 | F | 4 | Fail |
| 3 | S10002 | B | 45 | 0 | 70 | 4 | 81 | 5 | 196 | 3.00 | B | 2 | Pass |
| 4 | S10003 | C | 60 | 3 | 60 | 3 | 60 | 3 | 180 | 3.00 | B | 2 | Pass |
| 5 | S10004 | D | Abs | Absent | 63 | 3 | 53 | 2 | Absent | Absent | Absent | - | Absent |
| 6 | S10005 | E | 99 | 5 | 75 | 4 | 75 | 4 | 249 | 4.33 | A | 1 | Pass |

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