# PRINTING VARIABLES
in this we use the echo command, till now we used the echo command to print values but it can also be used to print the value associated with the variables for this we need to use the '$' symbol .Here in this challenge we printed the value contained in variable flag.

```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{8TR1tH9itUtogbfpieX_EwJuNDE.ddTN1QDL5MTM1czW}
```

# SETTING VARIABLES

Here we learnt how to input values or assign values into a variable. Like in all the other languages we use the '=' sign to assign values.But one thing that needs to be taken care of is that there should not be any spaces in between variable,value and the '=' sign or else it will try to run the variable name as a command .
Here we assign the value COLLEGE to the variable PWN.

```
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{AqabD1YfDRGFNB_TYOHnAj2iAGD.dlTN1QDL5MTM1czW}
  ```
# MULTI WORD VARIABLES

In this challenge, if we want to assign value which contains spaces to a particular variable then we need to mention the value within " " or else as soon as it encounters a space it will stop the assigning process.

```
Connected!
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{83dia9bcUccDcpqImqPJGUYrvlg.dBjN1QDL5MTM1czW}
```


# EXPORTING VARIABLES

In general, the values which we assign to a variable are not printed when accessed in a different shell, this is because the variables are local and if we need to access the variables outside we need to use the export command. Here in this challenge ,we assign the value college with the export command and we assign the value pwn to the variable college without the export command.

```
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{4z2kx_KpPxg9L1iuwyjEELgl04r.dJjN1QDL5MTM1czW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```
