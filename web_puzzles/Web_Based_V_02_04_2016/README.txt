

############################# Testing Web Security  version 1.0  #####################################

### Challenge: Web Login  ####
This challenge deals with login puzzles. These puzzles encompasses the common mistakes
 done by developer. These might be default user-name and passwords, hard-coded passwords 
 in html or JavaScript code, client side validation.
 
### Puzzles               ####
Objective: Enter the email address and password, and have a successful login to complete the level.

### Level 0: demo0.html   ####
To solve this puzzle, user need to go to source page. Method: Right click on page and click "View 
Page Source". If the source code is carefully reviewed, the line that contains code for 'Sign In' 
button also includes the static hard-coded value for the password. e.g.: var password='12345678
<button onclick="var password = '12345678'; checkInput(password); return false;" type="submit" 
class="btn btn-lg btn-primary btn-block">Sign In</button>
User just needs to enter any email address and the hard coded password and click the 'Sign In' button.
Answer: 
abc@xyz.com 
12345678

### Level 1: demo1.html   ####
To solve this puzzle, user need to go to source page. Method: Right click on page and click "View 
Page Source". If the source code is carefully reviewed, the line that contains code for 'Sign in' 
button also includes the JavaScript function. On clicking the button, it calls the JavaScript function
 'checkinput(password)'. To access the JavaScript file, go to head section in  page source. 
 e.g: 
 <head>... 
 <script src="js/demo1.js" type="text/javascript"></script>
 </head> 
The function 'checkinput()' checks the password if it matches with the concatenation of string "s" and "12345678".
User just needs to enter any email address and the password 's12345678' and click the 'Sign In' button

Answer: 
abc@xyz.com 
s12345678

### Level 2: demo2.html   ####
This puzzle is next version of previous puzzles with a difficulty level. It also uses same JavaScript function to check the input 
password. The main difference is that it uses the concept of hexa-decimal and hexMD5 other than plain text.
To compute the exact password, user needs to compute the corresponding text string for given hexa-decimal formatted strings and concatenate 
with the string passed in function, then compute its hexMD5 value.
Code: if(document.login.inputPassword.value != hexMD5("\x43\x4f\x4d\x50\x37\x33\x32\x37"+pass)) {
Hints: 
From hexa-decimal to text:
visit http://www.unit-conversion.info/texttools/hexadecimal/, 
enter the hexa-decimal chars in input data section, choose 'hex numbers to text' from 'convert' drop-down.
Click on 'Output' text-area. The corresponding text string is shown on output.
\x43\x4f\x4d\x50\x37\x33\x32\x37
COMP7327

Compute MD5 Hex:
Visit http://md5sum.org/, enter the plain text (concatenating the string from hexa-decimal and string passed in function) 
and click 'Get MD5 Hex' button.
Plaintext: COMP732712345678
Output: b0b802febcbb710fbcc537dbce86745d
User just needs to enter any email address and the password as above output and click the 'Sign In' button

Answer: 
abc@xyz.com 
b0b802febcbb710fbcc537dbce86745d


### Level 3: demo3.html   ####
This puzzle encompasses the issue on form validation. The given form is a sample of payment form.
If the Checkbox provided in the billing section is checked, the value entered in shipping information is auto populated in
billing section as well. The issue on the form is that it does not compare the shipping and billing information on form submit.
Therefore, user can modify the shipping information and simply click submit button resulting different billing and shipping information.
Objective: User needs to enter Shipping and payment information and then check the check-box in billing section. This will populate same 
values as entered in shipping section. Now the user needs to modify the shipping information and try to get successful submit.
To make the puzzle more tricky, user needs to enter exact information in shipping information for which form is checking the input 
on JavaScript. So, user needs to review 'reviewForm.js' and collect inputs.

To solve:
Enter the input:
Shipping information:
Street Address: 1327 Elm Street
City: 0x4E0x59
State: New York 
Zip: 38111
phoneNumber: 8765309
email: dr.Jekyl@hyde.com

Payment information:
Card(Credit/Debit): Check Debit
Card Type: Any of them except MasterCard and original value
Card Number: 1234567890151
Card Name: any thing more than 20 characters to trigger ""
Security Code: 1408
Card Exp Date: 09/06/91

Billing information:
Just check the checkbox, the fields will be disabled and values are seen.

Second Step:
Modify the Shipping information:
shipping Adress: 1428 Elm Street
shipping City: Gotham
shipping State = Texas
shipping zip: 90210

Final step: Click 'Submit' button.


############# © 2016, Center for Information Assurance (CfIA), University of Memphis. ##########################################


 