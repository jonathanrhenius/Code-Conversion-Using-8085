# Code-Conversion-Using-8085

## Aim:

To write 8085 microprocessor programs for converting:
1.	Hexadecimal to ASCII
2.	ASCII to Hexadecimal

## Apparatus Required:
•	Laptop with an internet connection

## Program 1: Hexadecimal to ASCII Conversion

## Algorithm:

1.	Load the hexadecimal number from memory location 4200H.
2.	Mask the upper nibble and check if it is less than 10H.
3.	If it is less than 10H, add 30H to convert it to ASCII.
4.	If it is greater than 10H, add 37H to convert it to ASCII.
5.	Repeat the process for the lower nibble.
6.	Store the ASCII equivalent in memory location 4300H and 4301H.

## Program:
```
LDA 4200H;
MOV B, A;
ANI 0f0H;
RRC;
RRC
RRC
RRC;
CPI 0AH;
JC ADD30;
ADI 37H;
JMP STORE1;
ADD30: ADI 30H;
STORE1: STA 4300H;
MOV A, B;
ANI 0FH;
CPI 0AH;
JC ADD30L;
ADI 37H;
JMP STORE2;
ADD30L: ADI 30H;
STORE2: STA 4301H;
HLT;
```

## Output:
<img width="1811" height="870" alt="Screenshot 2025-09-15 135227" src="https://github.com/user-attachments/assets/a56520a5-1490-444d-947d-9f3680dd8211" />
<img width="294" height="472" alt="Screenshot 2025-09-15 135235" src="https://github.com/user-attachments/assets/877ecb9b-0c66-4291-ba55-7e1977eac836" />
<img width="296" height="460" alt="Screenshot 2025-09-15 135242" src="https://github.com/user-attachments/assets/0125b344-f8e8-48ee-9457-7f1ee89035ca" />



## Program 2: ASCII to Hexadecimal Conversion

## Algorithm:

1.	Load the first ASCII digit from memory location 4200H.
2.	Convert it to hexadecimal by subtracting 30H (if it's a number) or 37H (if it's a letter A-F).
3.	Load the second ASCII digit from memory location 4201H and repeat the process.
4.	Combine the upper and lower nibbles to form a hexadecimal number.
5.	Store the result in memory location 4300H.

## Program:
```
LDA 4200H;
CPI 3AH;
JC SUB30;
SUI 37H;
JMP STOREH;
SUB30: SUI 30H;

STOREH: MOV C, A;
LDA 4201H;
CPI 3AH;
JC SUB30L;
SUI 37H;;
JMP STOREL;
SUB30L: SUI 30H;
STOREL: MOV B, A;
MOV A, C;
RLC 
RLC
RLC
RLC
ADD B;
STA 4300H;
HLT;
```


## Output:
<img width="1812" height="861" alt="Screenshot 2025-09-15 140734" src="https://github.com/user-attachments/assets/9095a35a-bb9c-46bc-8a17-c9dcaa651e2c" />
<img width="294" height="421" alt="Screenshot 2025-09-15 140741" src="https://github.com/user-attachments/assets/b5e43551-6d41-47f1-8f99-68c85ec6c479" />
<img width="293" height="360" alt="Screenshot 2025-09-15 140748" src="https://github.com/user-attachments/assets/c0aebd9d-2d38-4b75-b9bb-85103c504d31" />




## Result:

The 8085 microprocessor successfully converts hexadecimal numbers to ASCII and vice versa, storing the results in memory.



